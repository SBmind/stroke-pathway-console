# Stroke Pathway Console

Prototype dashboard for the **acute stroke patient journey**, built around the
*Siriraj Stroke Fast Track Activation Protocol v1.0 (onset < 24 h)*.

> **All data is simulated.** Numbers are generated in the browser from a seeded
> random model and do not reflect any real patient or real hospital performance.

## Views

| View | What it shows |
|---|---|
| **Live fast-track board** | Activations currently in the pathway: team acknowledgments (RAD / NEU / INR / ANES), location, current protocol step, time since the 99499 call, next time target and alert state. |
| **Patient journey** | One activation end to end: interval tiles (activation → CT, → rt-PA, mCTA → INR call, → groin), a protocol-step timeline, the full event log with the responsible role, and the answer at each protocol decision. |
| **Protocol map** | The v1.0 flowchart redrawn as an interactive diagram; the selected patient's path is highlighted with T0+minutes at each node. |
| **Cohort & KPIs** | Six months of simulated activations: median intervals, monthly activation-to-needle trend, pathway flow (CT finding → treatment → 90-day mRS), and protocol-adherence measures. |
| **Data model** | The JSON record the console reads, the event codes, the time targets, and a suggested HIS / OMOP CDM mapping. |

## Run it

It is a single file with no build step and no server.

* Open `index.html` in any modern browser, **or**
* Publish with GitHub Pages: *Settings → Pages → Deploy from a branch → `main` / root*.
  The site will be at `https://SBmind.github.io/stroke-pathway-console/`.

Fonts are loaded from Google Fonts; everything else is inline.

## Feeding real data

The console reads one JSON array of activations (see the *Data model* tab).
To connect it to HIS / OMOP data, replace the `COHORT` and `LIVE` generators
in `index.html` with a `fetch()` of that array. Every interval is derived from
the `events[]` timestamps, so upstream systems never need to compute
door-to-needle-style metrics themselves.

Time targets are prototype defaults (`TARGETS` in the script) and are meant to
be set by the stroke committee.

## Files

* `index.html` – the dashboard (single file)
* `protocol-v1.0.png` – the source protocol flowchart
* `LICENSE` – MIT

