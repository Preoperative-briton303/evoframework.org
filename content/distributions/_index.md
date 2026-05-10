+++
title = "Distributions"
description = "Anywhere with a CPU, RAM, and a bit of storage. Wearable to datacenter."
template = "section.html"
sort_by = "weight"
weight = 3
+++

## Reach

Evo is not a media-player framework. It is not an audio framework. It
is not even, in any deep sense, a Linux framework. The architecture
makes one assumption only: there is a CPU somewhere, with some RAM
and a little storage, that needs to compose contributions from
plugins around subjects. Everything else - the operating system, the
hardware class, the domain, the form factor, the power envelope - is
free.

The framework runs on Unix today, eight architectures, three ARM
profiles, glibc and musl. The contracts the framework defines do not
mention Unix. Ports to RTOS environments, bare-metal Cortex-M
targets, embedded WASM runtimes, and constrained RISC-V profiles are
open invitations - the plugin contract reduces to a respond/take-custody
shape that any reasonable runtime can satisfy.

<div class="reach-diagram-wrap">
<svg class="reach-diagram" viewBox="0 0 1000 460" preserveAspectRatio="xMidYMid meet" xmlns="http://www.w3.org/2000/svg" role="img" aria-labelledby="reach-diagram-title reach-diagram-desc">
<title id="reach-diagram-title">Hardware reach: from wearables to datacenter</title>
<desc id="reach-diagram-desc">Five deployment classes - wearable, edge IoT, appliance, vehicle/industrial, datacenter/GPU - all sitting on the same evo framework band.</desc>

<defs>
<linearGradient id="reach-card-bg" x1="0" y1="0" x2="0" y2="1">
<stop offset="0%" stop-color="#162a40"/>
<stop offset="100%" stop-color="#0c1d30"/>
</linearGradient>

<linearGradient id="reach-band-bg" x1="0" y1="0" x2="1" y2="0">
<stop offset="0%" stop-color="#0a1828" stop-opacity="0.95"/>
<stop offset="20%" stop-color="#143a5c"/>
<stop offset="50%" stop-color="#1a4a72"/>
<stop offset="80%" stop-color="#143a5c"/>
<stop offset="100%" stop-color="#0a1828" stop-opacity="0.95"/>
</linearGradient>

<linearGradient id="reach-brand" x1="0" y1="0" x2="1" y2="1">
<stop offset="0%" stop-color="#00d4aa"/>
<stop offset="100%" stop-color="#00a080"/>
</linearGradient>

<radialGradient id="reach-glow-bg" cx="50%" cy="55%" r="60%">
<stop offset="0%" stop-color="#00d4aa" stop-opacity="0.12"/>
<stop offset="100%" stop-color="#00d4aa" stop-opacity="0"/>
</radialGradient>

<filter id="reach-card-glow" x="-20%" y="-20%" width="140%" height="140%">
<feGaussianBlur stdDeviation="2.5" result="blur"/>
<feFlood flood-color="#00d4aa" flood-opacity="0.15"/>
<feComposite in2="blur" operator="in" result="glow"/>
<feMerge>
<feMergeNode in="glow"/>
<feMergeNode in="SourceGraphic"/>
</feMerge>
</filter>

<filter id="reach-band-glow" x="-5%" y="-50%" width="110%" height="200%">
<feGaussianBlur stdDeviation="7" result="blur"/>
<feFlood flood-color="#00d4aa" flood-opacity="0.28"/>
<feComposite in2="blur" operator="in" result="glow"/>
<feMerge>
<feMergeNode in="glow"/>
<feMergeNode in="SourceGraphic"/>
</feMerge>
</filter>

<filter id="reach-particle-glow" x="-200%" y="-200%" width="500%" height="500%">
<feGaussianBlur stdDeviation="2" result="blur"/>
<feFlood flood-color="#00d4aa" flood-opacity="0.95"/>
<feComposite in2="blur" operator="in" result="glow"/>
<feMerge>
<feMergeNode in="glow"/>
<feMergeNode in="SourceGraphic"/>
</feMerge>
</filter>
</defs>

<rect x="0" y="0" width="1000" height="460" fill="url(#reach-glow-bg)"/>

<g filter="url(#reach-card-glow)">
<rect x="25" y="10" width="150" height="140" rx="14" fill="url(#reach-card-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="25" y="10" width="150" height="3" rx="1.5" fill="url(#reach-brand)" opacity="0.6"/>
<circle cx="100" cy="42" r="10" fill="none" stroke="#00d4aa" stroke-width="2" opacity="0.85"/>
<circle cx="100" cy="42" r="3" fill="#00d4aa"/>
</g>
<text x="100" y="80" text-anchor="middle" class="reach-card-title">Wearable</text>
<text x="100" y="100" text-anchor="middle" class="reach-card-arch">ARM Cortex-M</text>
<text x="100" y="120" text-anchor="middle" class="reach-card-examples">watch . hearing aid</text>
<text x="100" y="138" text-anchor="middle" class="reach-card-examples">smart ring</text>

<g filter="url(#reach-card-glow)">
<rect x="225" y="10" width="150" height="140" rx="14" fill="url(#reach-card-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="225" y="10" width="150" height="3" rx="1.5" fill="url(#reach-brand)" opacity="0.6"/>
<polygon points="300,32 311,38 311,50 300,56 289,50 289,38" fill="none" stroke="#00d4aa" stroke-width="2" opacity="0.85"/>
<circle cx="300" cy="44" r="2.5" fill="#00d4aa"/>
</g>
<text x="300" y="80" text-anchor="middle" class="reach-card-title">Edge / IoT</text>
<text x="300" y="100" text-anchor="middle" class="reach-card-arch">ARM . RISC-V</text>
<text x="300" y="120" text-anchor="middle" class="reach-card-examples">field node . pipeline</text>
<text x="300" y="138" text-anchor="middle" class="reach-card-examples">submarine telemetry</text>

<g filter="url(#reach-card-glow)">
<rect x="425" y="10" width="150" height="140" rx="14" fill="url(#reach-card-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="425" y="10" width="150" height="3" rx="1.5" fill="url(#reach-brand)" opacity="0.6"/>
<rect x="487" y="33" width="26" height="20" rx="2" fill="none" stroke="#00d4aa" stroke-width="2" opacity="0.85"/>
<circle cx="492" cy="38" r="1.5" fill="#00d4aa"/>
<circle cx="508" cy="38" r="1.5" fill="#00d4aa"/>
<circle cx="492" cy="48" r="1.5" fill="#00d4aa"/>
<circle cx="508" cy="48" r="1.5" fill="#00d4aa"/>
</g>
<text x="500" y="80" text-anchor="middle" class="reach-card-title">Appliance</text>
<text x="500" y="100" text-anchor="middle" class="reach-card-arch">ARM . x86</text>
<text x="500" y="120" text-anchor="middle" class="reach-card-examples">Pi . NUC . kiosk</text>
<text x="500" y="138" text-anchor="middle" class="reach-card-examples">signage . instrument</text>

<g filter="url(#reach-card-glow)">
<rect x="625" y="10" width="150" height="140" rx="14" fill="url(#reach-card-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="625" y="10" width="150" height="3" rx="1.5" fill="url(#reach-brand)" opacity="0.6"/>
<circle cx="700" cy="42" r="11" fill="none" stroke="#00d4aa" stroke-width="2" opacity="0.85"/>
<line x1="689" y1="42" x2="711" y2="42" stroke="#00d4aa" stroke-width="2" opacity="0.85"/>
<line x1="700" y1="31" x2="700" y2="53" stroke="#00d4aa" stroke-width="2" opacity="0.85"/>
</g>
<text x="700" y="80" text-anchor="middle" class="reach-card-title">Vehicle / Industrial</text>
<text x="700" y="100" text-anchor="middle" class="reach-card-arch">ARM64 . Yocto</text>
<text x="700" y="120" text-anchor="middle" class="reach-card-examples">infotainment . SCADA</text>
<text x="700" y="138" text-anchor="middle" class="reach-card-examples">avionics . marine</text>

<g filter="url(#reach-card-glow)">
<rect x="825" y="10" width="150" height="140" rx="14" fill="url(#reach-card-bg)" stroke="#1f3a5c" stroke-width="1"/>
<rect x="825" y="10" width="150" height="3" rx="1.5" fill="url(#reach-brand)" opacity="0.6"/>
<rect x="887" y="32" width="26" height="4" rx="1" fill="none" stroke="#00d4aa" stroke-width="1.5" opacity="0.85"/>
<rect x="887" y="40" width="26" height="4" rx="1" fill="none" stroke="#00d4aa" stroke-width="1.5" opacity="0.85"/>
<rect x="887" y="48" width="26" height="4" rx="1" fill="none" stroke="#00d4aa" stroke-width="1.5" opacity="0.85"/>
</g>
<text x="900" y="80" text-anchor="middle" class="reach-card-title">Datacenter / GPU</text>
<text x="900" y="100" text-anchor="middle" class="reach-card-arch">x86-64 . ARM64</text>
<text x="900" y="120" text-anchor="middle" class="reach-card-examples">inference . gateway</text>
<text x="900" y="138" text-anchor="middle" class="reach-card-examples">edge cluster</text>

<line x1="100" y1="150" x2="100" y2="200" stroke="#00d4aa" stroke-width="1" stroke-dasharray="2 4" opacity="0.5"/>
<line x1="300" y1="150" x2="300" y2="200" stroke="#00d4aa" stroke-width="1" stroke-dasharray="2 4" opacity="0.5"/>
<line x1="500" y1="150" x2="500" y2="200" stroke="#00d4aa" stroke-width="1" stroke-dasharray="2 4" opacity="0.5"/>
<line x1="700" y1="150" x2="700" y2="200" stroke="#00d4aa" stroke-width="1" stroke-dasharray="2 4" opacity="0.5"/>
<line x1="900" y1="150" x2="900" y2="200" stroke="#00d4aa" stroke-width="1" stroke-dasharray="2 4" opacity="0.5"/>

<g filter="url(#reach-band-glow)">
<rect x="20" y="200" width="960" height="80" rx="20" fill="url(#reach-band-bg)" stroke="#256086" stroke-width="1.5"/>
<rect x="20" y="200" width="960" height="4" rx="2" fill="url(#reach-brand)"/>
</g>
<text x="500" y="248" text-anchor="middle" class="reach-band-title">one evo framework</text>
<text x="500" y="270" text-anchor="middle" class="reach-band-subtitle">same vocabulary at every scale</text>

<path id="reach-band-path" d="M 20,240 L 980,240" fill="none"/>

<circle r="3" fill="#00d4aa" filter="url(#reach-particle-glow)" opacity="0.9">
<animateMotion dur="6s" repeatCount="indefinite" begin="0s">
<mpath href="#reach-band-path"/>
</animateMotion>
</circle>
<circle r="3" fill="#00d4aa" filter="url(#reach-particle-glow)" opacity="0.7">
<animateMotion dur="6s" repeatCount="indefinite" begin="1.5s">
<mpath href="#reach-band-path"/>
</animateMotion>
</circle>
<circle r="3" fill="#00d4aa" filter="url(#reach-particle-glow)" opacity="0.7">
<animateMotion dur="6s" repeatCount="indefinite" begin="3s">
<mpath href="#reach-band-path"/>
</animateMotion>
</circle>
<circle r="3" fill="#00d4aa" filter="url(#reach-particle-glow)" opacity="0.5">
<animateMotion dur="6s" repeatCount="indefinite" begin="4.5s">
<mpath href="#reach-band-path"/>
</animateMotion>
</circle>

<text x="100" y="320" text-anchor="middle" class="reach-scale-label">RAM: kB</text>
<text x="100" y="338" text-anchor="middle" class="reach-scale-sublabel">few mW</text>

<text x="300" y="320" text-anchor="middle" class="reach-scale-label">RAM: MB</text>
<text x="300" y="338" text-anchor="middle" class="reach-scale-sublabel">~ 1 W</text>

<text x="500" y="320" text-anchor="middle" class="reach-scale-label">RAM: MB-GB</text>
<text x="500" y="338" text-anchor="middle" class="reach-scale-sublabel">few W</text>

<text x="700" y="320" text-anchor="middle" class="reach-scale-label">RAM: GB</text>
<text x="700" y="338" text-anchor="middle" class="reach-scale-sublabel">10-100 W</text>

<text x="900" y="320" text-anchor="middle" class="reach-scale-label">RAM: GB-TB</text>
<text x="900" y="338" text-anchor="middle" class="reach-scale-sublabel">kW</text>

<text x="500" y="410" text-anchor="middle" class="reach-bottom-text">CPU . RAM . a bit of storage. The rest is plugins.</text>
</svg>
</div>

## Who could ship a distribution

The framework is brand-neutral. Anyone with a hardware target and a
domain in mind can ship a vendor distribution: an automotive OEM
shipping a head unit, a satellite operator shipping a mission
computer, a wearables maker shipping a wristwatch, an industrial
controls integrator shipping a SCADA console. The set below is
illustrative, not announced.

<div class="card-grid">

<div class="card">
<h3>Aerospace</h3>
<div class="card-meta">
<span class="pill pill-info">Mission-critical</span>
<span class="pill pill-muted">Imagined</span>
</div>
<p>Mission computer for a probe. Telemetry recorder, image pipeline,
attitude controller, thermal management - all as plugins. Pieces are
signed and updated individually over a thin uplink; the framework
itself is rarely touched.</p>
<div class="card-links">
<span>Hardware: rad-hardened ARM, RISC-V</span>
</div>
</div>

<div class="card">
<h3>Submarine / marine</h3>
<div class="card-meta">
<span class="pill pill-info">Industrial</span>
<span class="pill pill-muted">Imagined</span>
</div>
<p>Bridge console for sub-sea operations. Sonar, navigation, life
support, propulsion telemetry as independent plugins composing into
a coherent operator surface. Plugins never coordinate; the steward
is the only place state changes - the property you want when the
crew is breathing your software.</p>
<div class="card-links">
<span>Hardware: industrial x86, ARM64</span>
</div>
</div>

<div class="card">
<h3>Automotive OEM</h3>
<div class="card-meta">
<span class="pill pill-info">Vehicle</span>
<span class="pill pill-muted">Imagined</span>
</div>
<p>Infotainment head unit, telematics gateway, ADAS coprocessor in
one stack. Same fabric across multiple vehicle compute zones. Each
zone admits the catalogue it needs; vendor plugins for the
proprietary protocols sit alongside brand-neutral plumbing for media,
networking, identity.</p>
<div class="card-links">
<span>Hardware: ARM64, x86-64 (Yocto)</span>
</div>
</div>

<div class="card">
<h3>Festival production</h3>
<div class="card-meta">
<span class="pill pill-info">Live event</span>
<span class="pill pill-muted">Imagined</span>
</div>
<p>Lighting, rigging, audio, video coordination across a festival
site. New act is a new plugin set loaded for that act's catalogue.
Plugins for DMX, MIDI show-control, network audio, video walls.
Operator sovereignty: a stage manager swaps the catalogue between
shows, no vendor in the loop.</p>
<div class="card-links">
<span>Hardware: ruggedized x86, Pi clusters</span>
</div>
</div>

<div class="card">
<h3>Wearables maker</h3>
<div class="card-meta">
<span class="pill pill-info">Personal device</span>
<span class="pill pill-muted">Imagined</span>
</div>
<p>Wristwatch counting heart rate, steps, sleep, plus a future
ambient-stress plugin that ships separately. Same fabric vocabulary
from MCU prototype to production silicon. The plugin contract
reduces to a respond/take-custody shape an embeddable runtime can
satisfy.</p>
<div class="card-links">
<span>Hardware: ARM Cortex-M / -A</span>
</div>
</div>

<div class="card">
<h3>Datacenter / NVIDIA partner</h3>
<div class="card-meta">
<span class="pill pill-info">Server</span>
<span class="pill pill-muted">Imagined</span>
</div>
<p>GPU inference appliance running models for industrial customers.
Each model is a plugin with its own signing posture; swap a model
without restarting the appliance. The fast path serves real-time
inference; the slow path serves projections to a fleet operator.</p>
<div class="card-links">
<span>Hardware: ARM64 + GPU, x86-64 + GPU</span>
</div>
</div>

<div class="card">
<h3>Medical device</h3>
<div class="card-meta">
<span class="pill pill-info">Regulated</span>
<span class="pill pill-muted">Imagined</span>
</div>
<p>Patient monitor in an ICU. Vitals, infusion, ventilator data
each a separate plugin signed under the device manufacturer's key,
with operator sovereignty so the hospital's biomed team has the
final word. Piece-granular signed updates fit a regulated change-
control regime cleanly.</p>
<div class="card-links">
<span>Hardware: medical-class embedded Linux</span>
</div>
</div>

<div class="card">
<h3>Industrial / SCADA</h3>
<div class="card-meta">
<span class="pill pill-info">Critical infra</span>
<span class="pill pill-muted">Imagined</span>
</div>
<p>Power substation control panel. One fabric across SCADA, HMI,
telemetry, alarm management. Vendor plugins for the IEC 61850
stack, brand-neutral plugins for everything else. Configuration is
data; a typo is a one-line edit, not an outage window.</p>
<div class="card-links">
<span>Hardware: industrial x86 (Yocto / RT Linux)</span>
</div>
</div>

</div>

## What ships today

These are the actual public artefacts. The reference generic device
for the audio domain is the canonical demonstration of every framework
function.

<div class="card-grid">

<div class="card">
<h3>evo-device-audio</h3>
<div class="card-meta">
<span class="pill pill-info">Reference generic</span>
<span class="pill pill-info">Audio</span>
<span class="pill pill-ok">Working</span>
</div>
<p>The reference generic device for the audio domain. Brand-neutral
plugins under the <code>org.evoframework.*</code> namespace: MPD
playback, ALSA composition, file-tag metadata, local artwork. Used
today as the canonical demonstration of every framework function;
read the source if you want to see the plugin contract concretely.</p>
<div class="card-links">
<a href="https://github.com/foonerd/evo-device-audio">Source</a>
<a href="https://github.com/foonerd/evo-device-audio-artefacts">Artefacts</a>
</div>
</div>

<div class="card">
<h3>Your distribution here</h3>
<div class="card-meta">
<span class="pill pill-muted">Open</span>
</div>
<p>The framework supports an open set of distributions across an open
set of domains. New domain? Start a <code>evo-device-&lt;domain&gt;</code>
reference. New brand on an existing domain? Start a
<code>evo-device-&lt;vendor&gt;</code> vendor distribution adopting
the relevant reference. The
<a href="https://github.com/foonerd/evo-core/blob/main/docs/engineering/BOUNDARY.md">BOUNDARY</a>
document is the normative checklist.</p>
<div class="card-links">
<a href="/build/">Build a distribution</a>
</div>
</div>

</div>

## What "tier" means

Reference generic devices are signed by the evo project's commons
key and live under the `org.evoframework.*` namespace. Their job is
to provide brand-neutral plumbing for one domain, ready for any
vendor distribution to adopt by name. The audio reference is the
canonical demonstration of the framework's full surface; future
references for video, home automation, instrumentation, vehicle
compute, and aerospace follow the same pattern.

Vendor distributions are signed by the vendor's own key and live
under per-vendor namespaces (`com.<vendor>.*`). Their job is to ship
a deployable device: catalogue choices, vendor plugins, branding,
packaging, release planes. Vendor distributions adopt one or more
reference generic devices; they do not duplicate the brand-neutral
work.

The framework, the reference generic devices, and the vendor
distributions all release independently and are signed independently.
A distribution bumps its framework pin when it chooses, and its
reference-device pin when it chooses; either bump may happen without
the other.
