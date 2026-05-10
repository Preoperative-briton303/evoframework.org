+++
title = "Docs"
description = "Engineering reference: contracts, protocols, schemas, and operator concerns."
template = "section.html"
sort_by = "weight"
weight = 4
+++

The engineering documentation set lives alongside the framework
source. Each document below is the single normative source for one
concern. They are read more often than the concept itself.

The documents are grouped by what you are doing.

## Start here

| Document | If you are... |
|----------|---------------|
| [CONCEPT](/concept/) | new to evo. The fabric contract: essence, steward, racks, shelves, plugins, subjects, relations, projections, happenings. |
| [BOUNDARY.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/BOUNDARY.md) | starting an `evo-device-<vendor>` repository, or deciding whether a change belongs in the framework or a distribution. |
| [SCHEMAS.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/SCHEMAS.md) | looking for any schema. Consolidated authoritative reference for every TOML file, JSON shape, wire frame, happening variant, and data structure across the fabric. |

## Plugin authors

| Document | Purpose |
|----------|---------|
| [PLUGIN_CONTRACT.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PLUGIN_CONTRACT.md) | What every plugin must satisfy: instance shape, interaction shape, lifecycle, manifest, errors. |
| [PLUGIN_PACKAGING.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PLUGIN_PACKAGING.md) | Manifest, signing, identity, on-device filesystem layout, install and update lifecycle. |
| [evo-catalogue-schemas](https://github.com/foonerd/evo-catalogue-schemas) | Per-shelf shape schemas. The contract a plugin reads to know what it must implement. Versioned independently. |

## Distribution authors

| Document | Purpose |
|----------|---------|
| [BOUNDARY.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/BOUNDARY.md) | The normative split between framework and distribution. |
| [VENDOR_CONTRACT.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/VENDOR_CONTRACT.md) | Actor taxonomy, namespace governance, vendor signing posture, trust roots. |
| [evo-device-volumio SHOWCASE.md](https://github.com/foonerd/evo-device-volumio/blob/main/SHOWCASE.md) | Worked example: source repo, artefacts repo, signed pieces, three planes, three workflows. |

## Consumers

| Document | Purpose |
|----------|---------|
| [CLIENT_API.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/CLIENT_API.md) | The client socket protocol, with example clients in seven languages. |
| [PROJECTIONS.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/PROJECTIONS.md) | Projection subscription and reconciliation. |
| [FAST_PATH.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/FAST_PATH.md) | The real-time mutation channel. |

## Internals

| Document | Purpose |
|----------|---------|
| [STEWARD.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/STEWARD.md) | Steward startup, admission, essence enforcement. |
| [SUBJECTS.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/SUBJECTS.md) | Subject identity resolution. |
| [RELATIONS.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/RELATIONS.md) | Relation grammar. |
| [LOGGING.md](https://github.com/foonerd/evo-core/blob/main/docs/engineering/LOGGING.md) | Logging conventions and plugin integration. |

## On this site

The engineering documents above currently live in the framework
repository. As the project matures, key documents will be transcribed
to this site under their own URLs (for example, `/docs/boundary/`,
`/docs/plugin-contract/`) so they can be cross-linked, searched, and
versioned alongside the homepage prose. The repository remains the
canonical source of truth.
