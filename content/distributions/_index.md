+++
title = "Distributions"
description = "Reference generic devices and vendor distributions built on the evo fabric."
template = "section.html"
sort_by = "weight"
weight = 3
+++

A distribution of evo is a curated catalogue plus a plugin set plus
branding plus packaging. Two tiers exist: reference generic devices,
brand-neutral plugin commons for one domain, signed by the evo
project; and vendor distributions, branded products that adopt one or
more reference generic devices and add the vendor layer on top.

The framework supports an open set of reference generic devices and
an open set of vendor distributions. The architecture imposes no
upper bound on either.

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
references for video, home automation, and instrumentation follow
the same pattern.

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
