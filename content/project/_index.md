+++
title = "Project"
description = "About evo, the actor taxonomy, license posture, and how to participate."
template = "section.html"
sort_by = "weight"
weight = 5
+++

## About evo

Evo is a reaction. The maintainer spent years shipping appliance-class
devices on stacks designed for something else: web runtimes pressed
into service as embedded backends, applications accumulating shared
mutable state until race conditions became the default behaviour,
release cycles measured in months because every change had to ship
together. Each platform had a clean concept and execution that
could not keep up. The user felt it as the device becoming worse
over time. The maintainer felt it as fear of the next change.

Evo is the system the maintainer built to do it differently. Pure
Rust, no garbage collector, no JavaScript runtime on the device, no
PHP backend, no shell pipelines holding state. One long-running
steward process is the sole authority on every transition; plugins
never address each other; the catalogue is data; every piece is
independently versioned and signed; the operator has the final word
on local trust.

The framework is pre-1.0. The audio reference generic device exists
and is the canonical demonstration of every framework function. The
first vendor distribution is scaffolded and dormant pending its
first vendor-specific plugin or branding work. Single-maintainer
driven; open to contributions on the contracts the engineering
documents name.

## Actors {#actors}

Five positions in the evo ecosystem. Each owns part of the
supply chain.

| Position | Role |
|----------|------|
| Evo project | Maintains the steward, fabric, SDK, tooling. Signs the framework binaries and the brand-neutral plugin commons. |
| Reference generic device | Curates a brand-neutral plugin set for one domain (audio, video, home, instrument, etc.). Plugins live under `org.evoframework.*`. |
| Vendor | Commercial or organisational entity that signs plugins under a claimed namespace (`com.<vendor>.*`) with formal commitments. |
| Individual author | Person or small team signing plugins under their own name. |
| Operator | The person running the device. Sole authority on local trust and revocation. |

The full actor taxonomy, vendor contract, and namespace governance
are in
[VENDOR_CONTRACT.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/VENDOR_CONTRACT.md).

## License {#license}

The framework runtime in `evo-core` is licensed under the Business
Source License 1.1. The plugin SDK, the operator CLI, the trust
primitive, the proc macro, and the example plugins are licensed
under the Apache License, Version 2.0. The reference generic devices
(`evo-device-audio`) and the vendor distributions
(`evo-device-volumio`) are Apache 2.0. The
[evo-catalogue-schemas](https://github.com/foonerd/evo-catalogue-schemas)
repository is Apache 2.0. This website is Apache 2.0.

The licence text lives in each repository's `LICENSE` file. The
Apache licence does not grant rights to use the project's
trademarks; trademarks are governed separately.

## Trademark {#trademark}

`evo` and `evoframework` are trademarks of Just a Nerd. Factual
reference, accurate compatibility statements, educational and
editorial use, and fair-use commentary are explicitly permitted
without prior permission. Branding products, naming domains, and
deceptive use suggesting affiliation are not.

The full trademark policy is in
[TRADEMARK.md](https://github.com/foonerd/evoframework.org/blob/main/TRADEMARK.md)
at the root of this site's repository, and is published at the
root of every public `evo-*` repository.

## Contribute

Contributions are welcomed on the contracts the engineering
documents name: plugin contract additions, new shelf shapes in the
catalogue schemas, new reference generic devices for new domains,
new vendor distributions, documentation improvements, and the
website itself.

Issues and pull requests live on each repository's GitHub page. The
top-level org for browsing every repository at once is
[github.com/foonerd](https://github.com/foonerd). Contributions are
accepted under the Developer Certificate of Origin
(<https://developercertificate.org/>); commits should carry a
`Signed-off-by:` trailer.

For trademark permission requests outside the explicitly-permitted
uses, open an issue at the canonical project repository titled
`[trademark]` followed by a brief description of the proposed use.

## Status

The project's current state, in plain terms:

- The framework runtime, the plugin SDK, the operator CLI, the
  client protocol, and the catalogue schemas all exist and are
  released as tagged versions on GitHub.
- The audio reference generic device exists and ships four
  brand-neutral plugins (MPD playback, ALSA composition, file-tag
  metadata, local artwork) signed by the evo project's commons
  signing key.
- The first vendor distribution is scaffolded and dormant: the
  catalogue is in place, the trust material is bundled, and the
  release planes are wired; vendor-specific plugins and branding
  have not yet landed.
- The website you are reading is itself pre-1.0 scaffolding;
  content lands as it is written.

Each repository's `README.md` and `CHANGELOG.md` carry the precise
current state.
