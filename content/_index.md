+++
title = "evo framework"
description = "A brand-neutral steward for appliance-class devices. Everything is a plugin."
template = "index.html"
sort_by = "weight"
+++

<p class="home-hero">
Everything is a plugin. The framework just stewards them.
</p>

<p class="home-subhead">
Evo is a Rust framework for appliance-class devices where features
are independent, signed plugins composed by a central steward that
knows nothing about the domain. Adding a capability is a new plugin.
Replacing one is replacing one signed file. The system stays
coherent as the plugin set grows.
</p>

## The problem

Appliance-class devices keep being built on stacks that were designed
for something else. A web runtime running as a backend daemon. An
event loop holding global state that two plugins both want to mutate.
A monolithic application that admits "extensions" but still owns the
truth. The result is a class of device that starts clean, accumulates
race conditions, develops a slow response surface, and ships a new
feature only by editing the centre. The user feels it as the device
becoming worse over time. The maintainer feels it as fear of the next
change. Both are symptoms of the same architectural choice, made
early, which the system can no longer escape.

## The move

Evo inverts the arrangement. The framework has no domain knowledge.
The device is described by a catalogue file, a small data document
that declares which concerns the device has, plus a set of plugins
that satisfy those concerns. There is no central application that
plugins are guests of. The catalogue is the device's specification;
the framework, which evo calls the steward, administers it. Plugins
contribute, and the steward composes their contributions into the
coherent thing the user sees.

## Why this is different

If you have used a device whose backend is a Node.js or Python
application server: the application owns the truth. Plugins are
callbacks the application invokes. Two plugins interested in the
same state coordinate through shared variables, and the application
is responsible for serialising them, which it usually does by
accident. Race conditions are the default; absence of races is a
feature you pay for plugin by plugin. In evo, the steward is the
only place state changes; plugins never see each other; the race
condition is not mitigated, it is structurally absent.

If you have built a plugin for an audio appliance: the plugin model
is usually a fixed set of extension points (decoder, source, output)
hung off the side of a core application. The application owns
playback, metadata, networking, the UI; plugins narrow the gaps.
Replacing the playback engine is forking the project. In evo, the
playback engine itself is a plugin. So is metadata, artwork, the
network manager. Nothing is privileged. Replacing the playback
engine is replacing one signed artefact.

If you have shipped firmware with a release cycle measured in
months: every change ships together because the build is monolithic.
Fixing a typo in an ALSA parameter means cutting a release. In evo,
a typo is a one-line config edit on the device; a plugin bug fix is
replacing one binary; a framework update is a deliberate act. Three
independent release cadences, three independent signing keys, three
planes (source, artefact, operational) that never blur into each
other.

## What this discipline buys

- Adding a feature is a new plugin. The framework is unchanged.
- Replacing a component is replacing one signed file. Nothing else
  moves.
- Two vendors building similar devices share the same brand-neutral
  plugins; only the vendor layer differs.
- Fixing a typo in a hardware parameter is a one-line config edit,
  not a rebuild and a re-flash.
- The integration cost of the plugin ecosystem stays flat as it
  grows. Plugin authors learn the contract once.

## Three tiers

Evo is not framework + your app. It is three tiers, each with its
own release cadence, its own signing key, and its own job.

```
DISTRIBUTION   evo-device-<vendor>      catalogue . plugins
                                        branding . packaging
                            |
                            v
STEWARD        evo-core                 catalogue . admission
                                        subjects . relations
                                        custody ledger
                                        projections . happenings
                            |
                            v
CONSUMERS      frontend . CLIs . bridges . automation
```

The framework holds the middle. Distributions adopt reference
generic devices and add the vendor layer. Devices fetch what each
manifest names, on the channel they track. None of these tiers know
about each other except through the contracts.

## A real device exists

<div class="card-grid">

<div class="card">
<h3>evo-device-audio</h3>
<div class="card-meta">
<span class="pill pill-info">Reference generic</span>
<span class="pill pill-ok">Working</span>
</div>
<p>The reference generic device for the audio domain. Brand-neutral
plugins under <code>org.evoframework.*</code>: MPD playback, ALSA
composition, file-tag metadata, local artwork. Used today as the
canonical demonstration of every framework function.</p>
<div class="card-links">
<a href="https://github.com/foonerd/evo-device-audio">Source</a>
<a href="https://github.com/foonerd/evo-device-audio-artefacts">Artefacts</a>
</div>
</div>

<div class="card">
<h3>evo-device-volumio</h3>
<div class="card-meta">
<span class="pill pill-info">Vendor</span>
<span class="pill pill-warn">Dormant</span>
</div>
<p>The first vendor distribution. Adopts evo-device-audio by name and
will add Volumio-specific plugins under <code>com.volumio.*</code>,
branding, and packaging on top.</p>
<div class="card-links">
<a href="https://github.com/foonerd/evo-device-volumio">Source</a>
<a href="https://github.com/foonerd/evo-device-volumio-artefacts">Artefacts</a>
</div>
</div>

</div>

## Sixty seconds

A steward, a one-shelf catalogue, and a client. No audio, no hardware.
The fabric is the same shape regardless of domain.

```bash
# Clone, build, and run a steward locally:
git clone https://github.com/foonerd/evo-core.git && cd evo-core
cargo build --workspace

mkdir -p /tmp/evo
cat > /tmp/evo/catalogue.toml <<'EOF'
[[racks]]
name = "example"
family = "domain"
kinds = ["registrar"]
charter = "Minimal example rack."

[[racks.shelves]]
name = "echo"
shape = 1
description = "Echoes inputs back."
EOF

cargo run -p evo -- \
    --catalogue /tmp/evo/catalogue.toml \
    --socket /tmp/evo/evo.sock \
    --log-level info
```

In another terminal, probe it:

```python
import socket, struct, json, base64
s = socket.socket(socket.AF_UNIX); s.connect("/tmp/evo/evo.sock")
req = json.dumps({
    "op": "request", "shelf": "example.echo", "request_type": "echo",
    "payload_b64": base64.b64encode(b"hello").decode()
}).encode()
s.send(struct.pack(">I", len(req)) + req)
n = struct.unpack(">I", s.recv(4))[0]
resp = json.loads(s.recv(n).decode())
print(base64.b64decode(resp["payload_b64"]).decode())  # -> "hello"
```

The full client protocol with example clients in seven languages is
in [CLIENT_API.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/CLIENT_API.md).

## The words evo uses

Evo's vocabulary is load-bearing. Every word below appears with the
same meaning across the framework, the documentation, and the
catalogue files.

| Word | Role |
|------|------|
| Steward | Sole authority. Admits plugins, places contributions, composes projections, dispatches actions, emits notifications. |
| Catalogue | The data document that declares the device's concerns. Read by the steward at startup. |
| Rack | A concern. Belongs to a family (domain, coordination, infrastructure) and a kind (producer, transformer, presenter, registrar). |
| Shelf | A slot or slot-set of declared shape within a rack. |
| Slot | A typed opening that admits one or more plugin contributions. |
| Plugin | Any capability that stocks a slot. The only entity in the running system that is not the steward. |
| Subject | A thing the catalogue has opinions about. Canonical identity held by the steward; reconciles plugin-specific addressings. |
| Relation | Typed directed connection between subjects. |
| Projection | Composed view emitted by the steward, keyed to a rack or a subject. |
| Happening | A transition event the steward emits on its notification stream. |
| Appointment | Time-originated instruction. |
| Watch | Condition-originated instruction. |
| Custody ledger | Registry of active warden assignments and their state. |
| Fast path | Real-time mutation channel alongside the structural slow path. |
| Distribution | A curated catalogue plus plugin set, shipped as a branded device. |
| Essence | The single sentence the steward enforces at startup and on admission. |

## Where to go next

<div class="cta-row">

<a class="cta" href="/concept/">
<strong>Read the concept</strong>
<span>The fabric in evo's own words.</span>
</a>

<a class="cta" href="/build/">
<strong>Build a plugin</strong>
<span>Stock a shelf in someone's catalogue.</span>
</a>

<a class="cta" href="/build/">
<strong>Build a distribution</strong>
<span>Ship a device on the evo fabric.</span>
</a>

</div>

## Project status

Pre-1.0. The framework runtime and the SDK are written; the audio
reference generic device exists and is the canonical demonstration of
every core function; the first vendor distribution is scaffolded and
dormant pending its first vendor-specific plugin.

The framework is licensed under the Business Source License 1.1; the
SDK, the operator CLI, the trust primitive, the proc macro, and the
example plugins are licensed under the Apache License 2.0. The names
"evo" and "evoframework" are trademarks; see the
[trademark policy](/project/#trademark).

Single-maintainer-driven. Open to contributions on the contracts the
engineering documents name. Issue and PR flow lives on
[GitHub](https://github.com/foonerd).
