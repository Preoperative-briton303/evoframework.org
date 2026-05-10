+++
title = "Build"
description = "Three audiences, three doors: plugin authors, distribution authors, operators."
template = "section.html"
sort_by = "weight"
weight = 2
+++

The Build section is split by what you are starting. Each path below
points at the smallest set of contracts you have to know to make
progress, then the engineering docs that elaborate them.

## What runs evo

Anything with a CPU, some RAM, and a little storage. The framework
runs on Unix today (Linux primarily, eight architectures, three ARM
profiles, glibc and musl) and the contracts the framework defines
do not assume Unix. Hardware classes the framework is designed for
range from MCU-class wearables and sensors at the small end, through
single-board appliances and automotive compute units in the middle,
to edge gateways and inference servers at the large end. The
[distributions page](/distributions/) shows the spread visually.

## I am writing a plugin

You want a single artefact that stocks a slot in someone's
catalogue. You start with three contracts.

The plugin contract itself, in
[PLUGIN_CONTRACT.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PLUGIN_CONTRACT.md),
defines what code you write: instance shape (singleton or factory),
interaction shape (respondent or warden), the lifecycle calls, and
the manifest fields. The contract is small; most plugins are a few
hundred lines once boilerplate is factored.

The shelf shape your plugin claims to satisfy lives in
[evo-catalogue-schemas](https://github.com/foonerd/evo-catalogue-schemas).
The schemas are versioned independently of the framework, so plugin
authors can pin a specific schemas version against their builds. The
admission gate validates a plugin's manifest against the catalogue
document at startup.

The signing posture for your plugin is documented in
[PLUGIN_PACKAGING.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PLUGIN_PACKAGING.md).
Brand-neutral plugins targeting the `org.evoframework.*` namespace
are signed by the evo project's commons key; per-vendor plugins are
signed by the vendor; individual authors sign with their own key.

For a worked example end to end, read the source of any plugin in
[evo-device-audio](https://github.com/foonerd/evo-device-audio):
the MPD warden, the local-file metadata respondent, the ALSA
composition responder. Each is a complete plugin in tens of files,
admitted by name into any audio distribution that adopts the
reference.

## I am building a distribution

You want to ship a device. The framework holds the middle; you own
the catalogue, the plugin curation, the branding, and the packaging.

Start with
[BOUNDARY.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/BOUNDARY.md).
It is the normative split: what crosses the framework / distribution
interface, what each side must not own, and the review test for any
new work that does not obviously belong on one side.

If you are building in an existing domain (audio is the only domain
shipped today), you do not author the plumbing. The reference generic
device gives you brand-neutral plugins, signed by the evo project,
ready to be admitted by name. For audio, that is
[evo-device-audio](https://github.com/foonerd/evo-device-audio). You
admit those plugins in your catalogue, then add only what is
genuinely vendor-specific: branding, product-specific plugins,
packaging.

If you are bringing up a new domain, you write the reference generic
device first. The pattern is in the same boundary document; the
worked example for "how to scaffold a brand-neutral plugin set for a
domain" is `evo-device-audio` itself.

The vendor-side methodology, with every release plane, signing key,
and CI workflow named, is documented as a separate showcase artefact.
It is written so that anywhere it names a specific brand or target
hardware, a future vendor reads their own brand and their own
hardware; the pattern survives the substitution.

### Targets

The framework is pure Rust, no C dependencies, Unix-native today.
Cross-compilation is straightforward; the `cargo` toolchain plus
`cross` covers every architecture below. The supported target list
on the day of writing:

- `x86_64-unknown-linux-gnu` and `x86_64-unknown-linux-musl`
- `aarch64-unknown-linux-gnu` and `aarch64-unknown-linux-musl`
- `armv7-unknown-linux-gnueabihf` and `armv7-unknown-linux-musleabihf`
- `arm-unknown-linux-gnueabihf` (ARMv6 - Raspberry Pi 1 / Zero W)
- `aarch64-linux-android` (Android Bionic)

Eight architectures, three ARM profiles, glibc and musl. Yocto is a
straight pull-in for any of the targets above.

The architecture is OS-neutral in spirit. The plugin contract reduces
to a respond/take-custody shape, and the steward's job - admit the
catalogue, place contributions, compose projections, dispatch
actions, emit notifications - is expressible in any reasonable
runtime. Ports beyond Unix are an open invitation:

- **RTOS** (FreeRTOS, Zephyr) for hard-real-time controllers.
- **Bare-metal Cortex-M** for sensor and wearable devices.
- **Embedded WASM** for sandboxed plugin distribution to constrained
  environments.
- **Constrained RISC-V** profiles for purpose-built ASIC pairings.
- **GPU-augmented** Linux (NVIDIA Jetson, datacenter inference) for
  larger workloads, where plugins encapsulate model lifecycles
  rather than process lifecycles.

The fabric vocabulary - catalogue, racks, shelves, slots, plugins,
subjects, projections, happenings, custody, fast path - applies at
every scale. The same word means the same thing on a wristwatch and
on a datacenter rack.

## I am running a device

You want to install, configure, update, and trust an evo-based
device. You start with the filesystem layout.

Three roots: `/opt/evo` for read-only package content,
`/etc/evo` for operator-editable policy (steward configuration,
trust keys, catalogue overlays, per-plugin config), and
`/var/lib/evo` for runtime mutable state (subject registry, relation
graph, per-plugin state, caches).

Trust posture is operator-sovereign. The steward verifies plugin
signatures against trust roots installed in `/etc/evo/keys/`. A
distribution bundles its vendor key and the relevant commons keys by
default; the operator can add, remove, or restrict keys at any time.
A plugin that loses trust is dropped at next restart with no other
side effect, because no other plugin addresses it.

The default operator policy on the client socket grants
identity-resolving capabilities only to local-UID consumers running
as the steward's own user. Distributions with a frontend or bridge
running under a different UID widen the policy through
`/etc/evo/client_acl.toml`. See
[CLIENT_API.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/CLIENT_API.md)
for the negotiation and resolution operations.

Configuration is data, not code. A typo in a hardware parameter is a
one-line edit to the relevant file under `/etc/evo/plugins.d/`,
followed by a steward restart or a plugin reload. There is no rebuild,
no firmware flash, no release cycle.
