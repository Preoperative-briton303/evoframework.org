+++
title = "Build"
description = "Three audiences, three doors: plugin authors, distribution authors, operators."
template = "section.html"
sort_by = "weight"
weight = 2
+++

Two authoring paths feed every device on evo. A plugin author writes
against the plugin contract; a UI author writes against the client
API. Both end up on the same vendor distribution.

<div class="flow-diagram-wrap">
<svg class="flow-diagram" viewBox="0 0 1200 600" preserveAspectRatio="xMidYMid meet" xmlns="http://www.w3.org/2000/svg" role="img" aria-labelledby="flow-diagram-title flow-diagram-desc">
<title id="flow-diagram-title">Two authoring paths converge on a vendor device</title>
<desc id="flow-diagram-desc">The evo framework on the left splits into two parallel paths: plugin (top) and UI (bottom). Both paths converge on the vendor device on the right. Animated particles trace each path.</desc>

<defs>
<linearGradient id="flow-card-bg" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#0d2236"/>
<stop offset="55%" stop-color="#102a44"/>
<stop offset="100%" stop-color="#0a1828"/>
</linearGradient>

<linearGradient id="flow-evo-bg" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#0e2a44"/>
<stop offset="50%" stop-color="#163a5e"/>
<stop offset="100%" stop-color="#0a1d30"/>
</linearGradient>

<linearGradient id="flow-device-bg" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#0d2438"/>
<stop offset="50%" stop-color="#1a4470"/>
<stop offset="100%" stop-color="#0a1d30"/>
</linearGradient>

<linearGradient id="flow-brand" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#00d4aa"/>
<stop offset="100%" stop-color="#00a080"/>
</linearGradient>

<radialGradient id="flow-glow-bg" cx="50%" cy="50%" r="60%">
<stop offset="0%" stop-color="#00d4aa" stop-opacity="0.12"/>
<stop offset="100%" stop-color="#00d4aa" stop-opacity="0"/>
</radialGradient>

<filter id="flow-card-glow" x="-15%" y="-15%" width="130%" height="130%">
<feGaussianBlur stdDeviation="4" result="blur"/>
<feFlood flood-color="#00d4aa" flood-opacity="0.20"/>
<feComposite in2="blur" operator="in" result="glow"/>
<feMerge>
<feMergeNode in="glow"/>
<feMergeNode in="SourceGraphic"/>
</feMerge>
</filter>

<filter id="flow-strong-glow" x="-15%" y="-15%" width="130%" height="130%">
<feGaussianBlur stdDeviation="9" result="blur"/>
<feFlood flood-color="#00d4aa" flood-opacity="0.32"/>
<feComposite in2="blur" operator="in" result="glow"/>
<feMerge>
<feMergeNode in="glow"/>
<feMergeNode in="SourceGraphic"/>
</feMerge>
</filter>

<filter id="flow-particle" x="-200%" y="-200%" width="500%" height="500%">
<feGaussianBlur stdDeviation="2.2" result="blur"/>
<feFlood flood-color="#00d4aa" flood-opacity="0.95"/>
<feComposite in2="blur" operator="in" result="glow"/>
<feMerge>
<feMergeNode in="glow"/>
<feMergeNode in="SourceGraphic"/>
</feMerge>
</filter>

<marker id="flow-arrow" viewBox="0 0 12 12" refX="6" refY="6" markerWidth="9" markerHeight="9" orient="auto-start-reverse">
<path d="M2,2 L10,6 L2,10 z" fill="#00d4aa"/>
</marker>
</defs>

<ellipse cx="600" cy="300" rx="700" ry="270" fill="url(#flow-glow-bg)"/>

<g filter="url(#flow-strong-glow)">
<rect x="60" y="200" width="240" height="200" rx="22" fill="url(#flow-evo-bg)" stroke="#256086" stroke-width="1.5"/>
<rect x="60" y="200" width="240" height="4" rx="2" fill="url(#flow-brand)"/>
<g transform="translate(258, 218)">
<rect width="28" height="28" rx="7" fill="url(#flow-brand)"/>
</g>
</g>
<text x="180" y="280" text-anchor="middle" class="flow-card-title flow-card-title-large">evo</text>
<text x="180" y="310" text-anchor="middle" class="flow-card-subtitle">framework</text>
<line x1="100" y1="332" x2="260" y2="332" stroke="#256086" stroke-width="1" opacity="0.5"/>
<text x="180" y="360" text-anchor="middle" class="flow-card-content">the steward</text>
<text x="180" y="382" text-anchor="middle" class="flow-card-content-sm">catalogue . subjects</text>

<path id="flow-path-1" d="M 300,260 C 380,260 400,180 480,180" fill="none" stroke="#00d4aa" stroke-width="2" stroke-dasharray="4 6" opacity="0.7" marker-end="url(#flow-arrow)"/>
<path id="flow-path-2" d="M 300,340 C 380,340 400,420 480,420" fill="none" stroke="#00d4aa" stroke-width="2" stroke-dasharray="4 6" opacity="0.7" marker-end="url(#flow-arrow)"/>

<circle r="3.5" fill="#00d4aa" filter="url(#flow-particle)">
<animateMotion dur="3.5s" repeatCount="indefinite" begin="0s">
<mpath href="#flow-path-1"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#flow-particle)">
<animateMotion dur="3.5s" repeatCount="indefinite" begin="1.7s">
<mpath href="#flow-path-1"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#flow-particle)">
<animateMotion dur="3.5s" repeatCount="indefinite" begin="0.85s">
<mpath href="#flow-path-2"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#flow-particle)">
<animateMotion dur="3.5s" repeatCount="indefinite" begin="2.55s">
<mpath href="#flow-path-2"/>
</animateMotion>
</circle>

<g filter="url(#flow-card-glow)">
<rect x="480" y="110" width="220" height="140" rx="16" fill="url(#flow-card-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="480" y="110" width="220" height="3" rx="1.5" fill="url(#flow-brand)" opacity="0.7"/>
<g transform="translate(515, 138)">
<rect x="0" y="0" width="20" height="20" rx="4" fill="none" stroke="#00d4aa" stroke-width="2" opacity="0.9"/>
<rect x="-2" y="6" width="8" height="8" rx="2" fill="#00d4aa" opacity="0.95"/>
</g>
</g>
<text x="590" y="166" text-anchor="middle" class="flow-card-title">plugin</text>
<text x="590" y="190" text-anchor="middle" class="flow-card-subtitle">stocks a slot</text>
<line x1="510" y1="208" x2="670" y2="208" stroke="#256086" stroke-width="1" opacity="0.4"/>
<text x="590" y="232" text-anchor="middle" class="flow-card-content-sm">respond . take custody</text>

<g filter="url(#flow-card-glow)">
<rect x="480" y="350" width="220" height="140" rx="16" fill="url(#flow-card-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="480" y="350" width="220" height="3" rx="1.5" fill="url(#flow-brand)" opacity="0.7"/>
<g transform="translate(513, 378)">
<rect x="0" y="0" width="24" height="17" rx="2.5" fill="none" stroke="#00d4aa" stroke-width="2" opacity="0.9"/>
<line x1="6" y1="22" x2="18" y2="22" stroke="#00d4aa" stroke-width="2" opacity="0.9"/>
<circle cx="12" cy="8.5" r="2" fill="#00d4aa" opacity="0.95"/>
</g>
</g>
<text x="590" y="406" text-anchor="middle" class="flow-card-title">UI</text>
<text x="590" y="430" text-anchor="middle" class="flow-card-subtitle">consumes projections</text>
<line x1="510" y1="448" x2="670" y2="448" stroke="#256086" stroke-width="1" opacity="0.4"/>
<text x="590" y="472" text-anchor="middle" class="flow-card-content-sm">subscribe . query</text>

<path id="flow-path-3" d="M 700,180 C 780,180 800,260 880,260" fill="none" stroke="#00d4aa" stroke-width="2" stroke-dasharray="4 6" opacity="0.7" marker-end="url(#flow-arrow)"/>
<path id="flow-path-4" d="M 700,420 C 780,420 800,340 880,340" fill="none" stroke="#00d4aa" stroke-width="2" stroke-dasharray="4 6" opacity="0.7" marker-end="url(#flow-arrow)"/>

<circle r="3.5" fill="#00d4aa" filter="url(#flow-particle)">
<animateMotion dur="3.5s" repeatCount="indefinite" begin="3.5s">
<mpath href="#flow-path-3"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#flow-particle)">
<animateMotion dur="3.5s" repeatCount="indefinite" begin="5.2s">
<mpath href="#flow-path-3"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#flow-particle)">
<animateMotion dur="3.5s" repeatCount="indefinite" begin="4.35s">
<mpath href="#flow-path-4"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#flow-particle)">
<animateMotion dur="3.5s" repeatCount="indefinite" begin="6.05s">
<mpath href="#flow-path-4"/>
</animateMotion>
</circle>

<g filter="url(#flow-strong-glow)">
<rect x="880" y="180" width="260" height="240" rx="22" fill="url(#flow-device-bg)" stroke="#3a7a9c" stroke-width="1.5"/>
<rect x="880" y="180" width="260" height="4" rx="2" fill="url(#flow-brand)"/>
<g transform="translate(1098, 198)">
<rect width="28" height="28" rx="7" fill="url(#flow-brand)">
<animate attributeName="opacity" values="0.85;1;0.85" dur="3.2s" repeatCount="indefinite"/>
</rect>
</g>
</g>
<text x="1010" y="262" text-anchor="middle" class="flow-card-title flow-card-title-large">device</text>
<text x="1010" y="290" text-anchor="middle" class="flow-card-subtitle">(vendor)</text>
<line x1="920" y1="310" x2="1100" y2="310" stroke="#3a7a9c" stroke-width="1" opacity="0.55"/>
<text x="1010" y="338" text-anchor="middle" class="flow-card-content">your distribution</text>
<text x="1010" y="362" text-anchor="middle" class="flow-card-content-sm">catalogue . plugins</text>
<text x="1010" y="384" text-anchor="middle" class="flow-card-content-sm">UI . branding . packaging</text>
</svg>

<p class="flow-diagram-caption">
Two authoring paths, one device. Plugin authors stock slots on the
steward; UI authors subscribe to projections from the steward. The
vendor distribution is what assembles both into a deployable device.
</p>
</div>

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
