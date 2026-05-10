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

The vendor-side worked example, with every release plane, signing
key, and CI workflow named, is
[evo-device-volumio's SHOWCASE.md](https://github.com/foonerd/evo-device-volumio/blob/main/SHOWCASE.md).
Anywhere it says "Volumio" or "Raspberry Pi", a future vendor reads
their own brand and their own target hardware. The pattern survives
the substitution.

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
