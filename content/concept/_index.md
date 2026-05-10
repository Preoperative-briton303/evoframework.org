+++
title = "Concept"
description = "The fabric, in evo's own words. The long version of the homepage."
template = "section.html"
sort_by = "weight"
weight = 1
+++

This page is the canonical statement of what evo is. It is adapted
from `evo-core/docs/CONCEPT.md` and uses the project's load-bearing
vocabulary throughout. Each named term appears in the
[homepage glossary](/#the-words-evo-uses) and is defined in
context below.

## 1. Essence

Evo is a fabric for building appliance-class devices. It is a steward
that administers a catalogue of concerns, admits plugins that stock
slots in that catalogue, and emits composed projections to any
consumer that looks.

Evo itself is domain-neutral. A specific device, whether an audio
player, a home automation controller, a signage kiosk, or a
scientific instrument, is defined by a catalogue declaration and a
curated plugin set, shipped as a distribution of evo.

The essence sentence, for any evo-based device:

> A device that performs the work declared in its catalogue, by
> composing contributions from plugins around subjects, while
> presenting coherent information to any consumer that looks.

Everything else in this document is derivable from this sentence
plus the fabric vocabulary. Anything in a built system that does not
serve a rack declared in the catalogue is not essence; it is a
plugin contribution that has found the wrong home, or it does not
belong.

### 1.1 Framework and distribution boundary

Evo-core is the framework: steward, plugin SDK, wire and client
protocols, packaging contract, engineering docs. A device is a
distribution: curated catalogue, plugin set, branding, packaging,
and product integration. The normative split, what crosses the
interface, what each side must not own, and the review test for new
work, lives in
[BOUNDARY.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/BOUNDARY.md).
The framework does not subsume the product, and the product does
not patch the steward.

## 2. Fabric

The product is a steward that administers a catalogue. The catalogue
is organised into racks. Each rack holds shelves. Each shelf has one
or more slots of declared shape. Plugins stock slots. The steward is
the sole authority; plugins never communicate directly.

Every contribution is keyed to one or more subjects. The steward
keeps a canonical subject registry that reconciles the many external
addressings plugins use, file paths, service IDs, MusicBrainz IDs,
tag-derived identities, into one canonical subject per real thing.
Subjects are connected in a governed relation grammar; the steward
keeps the resulting graph.

Consumers never address plugins. They address the steward, either by
rack (structural query) or by subject (federated query). The steward
composes contributions from every rack that has opinions about the
subject, walks related subjects within a declared scope, and emits a
projection. All outbound behaviour of the system is either a
projection on demand or a streamed happening on the fabric's
notification surface. There is no side channel.

<div class="hub-diagram-wrap">
<svg class="hub-diagram" viewBox="0 0 1000 800" preserveAspectRatio="xMidYMid meet" xmlns="http://www.w3.org/2000/svg" role="img" aria-labelledby="hub-diagram-title hub-diagram-desc">
<title id="hub-diagram-title">The hub: plugins stock slots on the steward, the steward emits projections to consumers</title>
<desc id="hub-diagram-desc">Four plugins at the top fan in to a single point that arrows into the steward, which sits as the centerpiece. The steward's output fans out to four consumer nodes below: frontend, CLI, bridge, automation. Animated particles trace the data flow.</desc>

<defs>
<linearGradient id="hub-plugin-bg" x1="0" y1="0" x2="0" y2="1">
<stop offset="0%" stop-color="#162a40"/>
<stop offset="100%" stop-color="#0c1d30"/>
</linearGradient>

<linearGradient id="hub-steward-bg" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#0d2236"/>
<stop offset="50%" stop-color="#143a5c"/>
<stop offset="100%" stop-color="#0a1d30"/>
</linearGradient>

<linearGradient id="hub-brand" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#00d4aa"/>
<stop offset="100%" stop-color="#00a080"/>
</linearGradient>

<radialGradient id="hub-glow-bg" cx="50%" cy="50%" r="50%">
<stop offset="0%" stop-color="#00d4aa" stop-opacity="0.18"/>
<stop offset="60%" stop-color="#00d4aa" stop-opacity="0.04"/>
<stop offset="100%" stop-color="#00d4aa" stop-opacity="0"/>
</radialGradient>

<filter id="hub-card-glow" x="-15%" y="-15%" width="130%" height="130%">
<feGaussianBlur stdDeviation="3" result="blur"/>
<feFlood flood-color="#00d4aa" flood-opacity="0.18"/>
<feComposite in2="blur" operator="in" result="glow"/>
<feMerge>
<feMergeNode in="glow"/>
<feMergeNode in="SourceGraphic"/>
</feMerge>
</filter>

<filter id="hub-steward-glow" x="-10%" y="-15%" width="120%" height="130%">
<feGaussianBlur stdDeviation="9" result="blur"/>
<feFlood flood-color="#00d4aa" flood-opacity="0.34"/>
<feComposite in2="blur" operator="in" result="glow"/>
<feMerge>
<feMergeNode in="glow"/>
<feMergeNode in="SourceGraphic"/>
</feMerge>
</filter>

<filter id="hub-particle-glow" x="-200%" y="-200%" width="500%" height="500%">
<feGaussianBlur stdDeviation="2.5" result="blur"/>
<feFlood flood-color="#00d4aa" flood-opacity="0.95"/>
<feComposite in2="blur" operator="in" result="glow"/>
<feMerge>
<feMergeNode in="glow"/>
<feMergeNode in="SourceGraphic"/>
</feMerge>
</filter>

<marker id="hub-arrow" viewBox="0 0 12 12" refX="6" refY="6" markerWidth="9" markerHeight="9" orient="auto-start-reverse">
<path d="M2,2 L10,6 L2,10 z" fill="#00d4aa"/>
</marker>
</defs>

<ellipse cx="500" cy="400" rx="540" ry="290" fill="url(#hub-glow-bg)"/>

<g filter="url(#hub-card-glow)">
<rect x="135" y="20" width="130" height="80" rx="14" fill="url(#hub-plugin-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="135" y="20" width="130" height="2.5" rx="1" fill="url(#hub-brand)" opacity="0.6"/>
<circle cx="155" cy="42" r="3" fill="#00d4aa" opacity="0.7"/>
</g>
<text x="200" y="68" text-anchor="middle" class="hub-plugin-label">plugin</text>

<g filter="url(#hub-card-glow)">
<rect x="335" y="20" width="130" height="80" rx="14" fill="url(#hub-plugin-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="335" y="20" width="130" height="2.5" rx="1" fill="url(#hub-brand)" opacity="0.6"/>
<circle cx="355" cy="42" r="3" fill="#00d4aa" opacity="0.7"/>
</g>
<text x="400" y="68" text-anchor="middle" class="hub-plugin-label">plugin</text>

<g filter="url(#hub-card-glow)">
<rect x="535" y="20" width="130" height="80" rx="14" fill="url(#hub-plugin-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="535" y="20" width="130" height="2.5" rx="1" fill="url(#hub-brand)" opacity="0.6"/>
<circle cx="555" cy="42" r="3" fill="#00d4aa" opacity="0.7"/>
</g>
<text x="600" y="68" text-anchor="middle" class="hub-plugin-label">plugin</text>

<g filter="url(#hub-card-glow)">
<rect x="735" y="20" width="130" height="80" rx="14" fill="url(#hub-plugin-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="735" y="20" width="130" height="2.5" rx="1" fill="url(#hub-brand)" opacity="0.6"/>
<circle cx="755" cy="42" r="3" fill="#00d4aa" opacity="0.7"/>
</g>
<text x="800" y="68" text-anchor="middle" class="hub-plugin-label">plugin</text>

<path id="hub-in-1" d="M 200,100 Q 200,180 500,235" fill="none" stroke="#00d4aa" stroke-width="1.5" stroke-dasharray="3 6" opacity="0.65"/>
<path id="hub-in-2" d="M 400,100 Q 400,180 500,235" fill="none" stroke="#00d4aa" stroke-width="1.5" stroke-dasharray="3 6" opacity="0.65"/>
<path id="hub-in-3" d="M 600,100 Q 600,180 500,235" fill="none" stroke="#00d4aa" stroke-width="1.5" stroke-dasharray="3 6" opacity="0.65"/>
<path id="hub-in-4" d="M 800,100 Q 800,180 500,235" fill="none" stroke="#00d4aa" stroke-width="1.5" stroke-dasharray="3 6" opacity="0.65"/>

<circle r="3.5" fill="#00d4aa" filter="url(#hub-particle-glow)">
<animateMotion dur="3.4s" repeatCount="indefinite" begin="0s">
<mpath href="#hub-in-1"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#hub-particle-glow)">
<animateMotion dur="3.4s" repeatCount="indefinite" begin="0.85s">
<mpath href="#hub-in-2"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#hub-particle-glow)">
<animateMotion dur="3.4s" repeatCount="indefinite" begin="1.7s">
<mpath href="#hub-in-3"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#hub-particle-glow)">
<animateMotion dur="3.4s" repeatCount="indefinite" begin="2.55s">
<mpath href="#hub-in-4"/>
</animateMotion>
</circle>

<line x1="500" y1="235" x2="500" y2="290" stroke="#00d4aa" stroke-width="2" marker-end="url(#hub-arrow)"/>
<text x="514" y="270" class="hub-line-label">stock slots</text>

<g filter="url(#hub-steward-glow)">
<rect x="120" y="295" width="760" height="220" rx="22" fill="url(#hub-steward-bg)" stroke="#256086" stroke-width="1.5"/>
<rect x="120" y="295" width="760" height="4" rx="2" fill="url(#hub-brand)"/>
<g transform="translate(836, 311)">
<rect width="26" height="26" rx="6" fill="url(#hub-brand)"/>
</g>
</g>
<text x="500" y="346" text-anchor="middle" class="hub-steward-label">THE STEWARD</text>
<text x="500" y="376" text-anchor="middle" class="hub-steward-sub">sole authority . no side channel</text>
<line x1="320" y1="395" x2="680" y2="395" stroke="#256086" stroke-width="1" opacity="0.5"/>
<text x="500" y="425" text-anchor="middle" class="hub-steward-content">catalogue . admission . subjects . relations</text>
<text x="500" y="453" text-anchor="middle" class="hub-steward-content">custody ledger . projections . happenings bus</text>

<line x1="500" y1="525" x2="500" y2="585" stroke="#00d4aa" stroke-width="2" marker-end="url(#hub-arrow)"/>
<text x="514" y="565" class="hub-line-label">projections / happenings</text>

<path id="hub-out-1" d="M 500,585 Q 200,615 200,690" fill="none" stroke="#00d4aa" stroke-width="1.5" stroke-dasharray="3 6" opacity="0.65"/>
<path id="hub-out-2" d="M 500,585 Q 400,615 400,690" fill="none" stroke="#00d4aa" stroke-width="1.5" stroke-dasharray="3 6" opacity="0.65"/>
<path id="hub-out-3" d="M 500,585 Q 600,615 600,690" fill="none" stroke="#00d4aa" stroke-width="1.5" stroke-dasharray="3 6" opacity="0.65"/>
<path id="hub-out-4" d="M 500,585 Q 800,615 800,690" fill="none" stroke="#00d4aa" stroke-width="1.5" stroke-dasharray="3 6" opacity="0.65"/>

<circle r="3.5" fill="#00d4aa" filter="url(#hub-particle-glow)">
<animateMotion dur="3.4s" repeatCount="indefinite" begin="0.4s">
<mpath href="#hub-out-1"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#hub-particle-glow)">
<animateMotion dur="3.4s" repeatCount="indefinite" begin="1.25s">
<mpath href="#hub-out-2"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#hub-particle-glow)">
<animateMotion dur="3.4s" repeatCount="indefinite" begin="2.1s">
<mpath href="#hub-out-3"/>
</animateMotion>
</circle>
<circle r="3.5" fill="#00d4aa" filter="url(#hub-particle-glow)">
<animateMotion dur="3.4s" repeatCount="indefinite" begin="2.95s">
<mpath href="#hub-out-4"/>
</animateMotion>
</circle>

<g filter="url(#hub-card-glow)">
<rect x="135" y="690" width="130" height="80" rx="14" fill="url(#hub-plugin-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="135" y="687.5" width="130" height="2.5" rx="1" fill="url(#hub-brand)" opacity="0.6"/>
</g>
<text x="200" y="738" text-anchor="middle" class="hub-consumer-label">frontend</text>

<g filter="url(#hub-card-glow)">
<rect x="335" y="690" width="130" height="80" rx="14" fill="url(#hub-plugin-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="335" y="687.5" width="130" height="2.5" rx="1" fill="url(#hub-brand)" opacity="0.6"/>
</g>
<text x="400" y="738" text-anchor="middle" class="hub-consumer-label">CLI</text>

<g filter="url(#hub-card-glow)">
<rect x="535" y="690" width="130" height="80" rx="14" fill="url(#hub-plugin-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="535" y="687.5" width="130" height="2.5" rx="1" fill="url(#hub-brand)" opacity="0.6"/>
</g>
<text x="600" y="738" text-anchor="middle" class="hub-consumer-label">bridge</text>

<g filter="url(#hub-card-glow)">
<rect x="735" y="690" width="130" height="80" rx="14" fill="url(#hub-plugin-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="735" y="687.5" width="130" height="2.5" rx="1" fill="url(#hub-brand)" opacity="0.6"/>
</g>
<text x="800" y="738" text-anchor="middle" class="hub-consumer-label">automation</text>
</svg>

<p class="hub-diagram-caption">
Plugins stock slots on the steward and never address each other.
Consumers address the steward, never plugins. The steward composes
contributions around subjects and emits projections or happenings.
This is the hub discipline the rest of the document assumes.
</p>
</div>

Two classes of originator exist inside the fabric besides external
requests. Appointments originate actions from time. Watches originate
actions from observed conditions. Both produce instructions the
steward dispatches as if from outside. The custody ledger tracks
work entrusted to wardens, plugins that take custody of long-running
operations. A separate fast path serves real-time mutation without
recomposition.

## 3. Distributions and actors

Evo is brand-neutral. A device ships as a distribution of evo: a
catalogue declaration plus a plugin set plus branding. Multiple
distributions exist, for different domains and different vendors.

Five actor positions exist in the evo ecosystem.

| Position | Role |
|----------|------|
| Evo project | Maintains the steward, fabric, SDK, tooling. |
| Reference generic device | Curates a brand-neutral plugin set for one domain. |
| Vendor | Commercial or organisational entity that signs plugins under a claimed namespace with formal commitments. |
| Individual author | Person or small team signing plugins under their own name. |
| Operator | The person running the device. Sole authority on local trust and revocation. |

The full actor taxonomy, vendor contract, namespace governance, and
trust-root relationships live in
[VENDOR_CONTRACT.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/VENDOR_CONTRACT.md).

## 4. Rack catalogue

A distribution's catalogue declares racks. Racks belong to families
and kinds.

Rack families: **domain** (what the distribution does), **coordination**
(when and why it acts), **infrastructure** (how the fabric operates over
time).

Rack kinds: **producer** (originates instructions), **transformer**
(moves or changes something), **presenter** (renders projections to a
surface), **registrar** (holds knowledge).

A rack may have more than one kind when the concern straddles.

The rack list is open. New racks declare new concerns. The steward
reads the catalogue as data; no rack is compiled into evo.

## 5. Plugin model

Plugins contribute to slots. They never address each other. They
address only the steward, through a contract whose shape is declared
by the slot they stock.

Two orthogonal axes classify every plugin.

| Axis | Values | Meaning |
|------|--------|---------|
| Instance shape | Singleton, Factory | One contribution forever, or many contributions over time driven by world events. |
| Interaction shape | Respondent, Warden | Answer discrete requests, or take custody of sustained work. |

The full plugin contract is defined in
[PLUGIN_CONTRACT.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PLUGIN_CONTRACT.md).
Packaging, identity, signing, and installation are in
[PLUGIN_PACKAGING.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PLUGIN_PACKAGING.md).

"Plugin" does not imply optional, third-party, or sandboxed. It is
the universal term for any satisfier of a slot contract. Every
plugin ships as an independently versioned artefact with a declared
manifest. The only entity in the running system that is not a
plugin is the steward.

## 6. Implementation commitments

| Commitment | Statement |
|------------|-----------|
| Language | Rust for the steward and for in-process first-party plugins. |
| Base OS | Debian Trixie minimal (lite). Evo is a layer atop stock Debian. |
| Steward process | Single long-running process. Owns the catalogue, subject registry, relation graph, custody ledger, projection layer, happenings stream. |
| Plugin transport | Two transports of one contract: in-process (Rust trait) and out-of-process (Unix-socket protocol, any language). |
| Plugin delivery | Each plugin is an independently versioned artefact with a declared manifest. |
| Trust classes | Declared in manifests, enforced by the steward, authorised by the signing key used. |
| Catalogue as data | Rack and shelf declarations are TOML the steward reads, not code. Adding a new rack is a catalogue edit plus the plugins to stock it. The steward is unchanged. |
| Domain neutrality | The steward has no knowledge of audio, networking, any service, any protocol. All domain knowledge lives in catalogues and plugins. |

## 7. Filesystem layout on target

Evo owns three roots on a Debian device.

| Root | Purpose | Writable |
|------|---------|----------|
| `/opt/evo/` | Read-only content shipped by packages: binaries, plugins, catalogue declarations, static data. | No (package-owned). |
| `/etc/evo/` | Operator-editable policy: steward configuration, trust keys, catalogue overlays, per-plugin config overrides. | Yes (root-owned, operator-edited). |
| `/var/lib/evo/` | Runtime mutable state: subject registry, relation graph, per-plugin state and credentials, caches. | Yes (service-owned). |

The full layout is in
[PLUGIN_PACKAGING.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PLUGIN_PACKAGING.md).

## 8. What the fabric does not do

| Concern | Whose problem |
|---------|---------------|
| Domain-specific logic (audio, networking, metadata, anything service-specific) | The distribution's plugin set. |
| Authentication with specific external services | The plugin that integrates that service. |
| Protocol parsing, codec handling, format decoding | The plugin that speaks that protocol or format. |
| UI rendering and styling | Consumers of projections. The steward emits projections in declared structural shape; how they are drawn is not its concern. |
| Cross-plugin coordination | Does not exist. Plugins cannot coordinate. All composition is through the steward on subject keys. |

## 9. Consequences

- Adding a new service, protocol, or data source is stocking
  existing shelves with new plugin contributions. The steward is
  unchanged. The catalogue is unchanged. The fabric is unchanged.
- Replacing a plugin is replacing one artefact on one slot. Every
  other plugin, every other rack, every consumer is unaffected
  because none of them addresses that plugin directly.
- Graceful degradation is structural. A consumer asking about a
  subject receives whatever the fabric can compose; missing
  contributions mean absent fields, not broken projections.
- Plugin authors never coordinate. The coordination cost of the
  plugin ecosystem is O(1) per plugin: each author learns the plugin
  contract once.
- Distributions can replace any plugin, including the most central
  (playback engine, network manager), by providing an alternative
  honouring the same contract. The steward does not privilege
  first-party over third-party.
- The rack list is open; the plugin population is open; the fabric
  is closed.

## 10. Deeper reading

The full engineering documentation set lives alongside the framework
source. Each document below answers a specific concrete question
left open by the concept.

- [BOUNDARY.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/BOUNDARY.md) - the framework / distribution split.
- [PLUGIN_CONTRACT.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PLUGIN_CONTRACT.md) - what a plugin must satisfy.
- [PLUGIN_PACKAGING.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PLUGIN_PACKAGING.md) - manifest, signing, installation, filesystem.
- [VENDOR_CONTRACT.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/VENDOR_CONTRACT.md) - actor taxonomy, namespace governance.
- [CLIENT_API.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/CLIENT_API.md) - the client socket protocol, with examples in seven languages.
- [SCHEMAS.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/SCHEMAS.md) - every schema in one place.
- [STEWARD.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/STEWARD.md) - the steward's startup, admission, and essence enforcement.
- [SUBJECTS.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/SUBJECTS.md) - subject identity resolution.
- [RELATIONS.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/RELATIONS.md) - the relation grammar.
- [PROJECTIONS.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PROJECTIONS.md) - projection subscription protocol.
- [FAST_PATH.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/FAST_PATH.md) - real-time mutation channel.
- [LOGGING.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/LOGGING.md) - logging conventions and plugin integration.

These documents are read more often than the concept itself. The
concept tells you what the fabric is; the engineering docs tell you
how to build to it.
