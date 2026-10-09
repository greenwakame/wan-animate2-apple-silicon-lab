# Pages design foundation — Phase H2c

The primary planned deliverable is a research / field report website at https://greenwakame.github.io/wan-animate2-apple-silicon-lab/. This phase creates a local publication draft, without Git initialization, repository creation, deployment configuration or publication.

## Information architecture

One complete landing page communicates the conclusion without opening supporting documents. Reading order: hero → executive result → tested system → VACE / v2 / v3 / v4 lineage → visual diagnostics → runtime and memory → six engineering findings → restore and artifacts → limitations → deliberately unrun v4 → provenance links. Native details disclosures hold the longer run conditions and historical chronology.

The dominant message is **TECHNICAL PASS ≠ VISUAL SUCCESS**. Runtime and memory describe observed single runs; v4 has no output, runtime or visual result. The v2 frame strip locates qualitative observations, not measured similarity scores. The v3 graphic depicts recorded reference preparation geometry only.

## Design relationship

Greenwakame Lab's charcoal/navy background, green primary accent, cyan secondary accent, mono labels, large typography and thin grids are inherited from the local main Showcase source. This independent subsystem emphasizes experiment IDs, telemetry and evidence instead of copying the Works layout. Amber denotes constraints and muted red denotes failures. No stock imagery, private media, artificial benchmarks, external fonts, framework, JS or animation is required.

## Portable static architecture

- Entry point: site/index.html.
- Styling: site/assets/css/site.css.
- Portable evidence: site/knowledge/ contains the 21 existing reviewed knowledge files, including the small exclusion-rules file.
- Source of truth remains root README.md, docs/, manifests/, workflows/, results/README.md and notices. Experimental evidence copies must remain byte-identical; H2f legal exceptions and release notices are documented in release-packaging.md.
- site/README.md is an authoring and QA handoff, not a deployed entry page.
- All internal files use relative URLs; anchors resolve within the landing page. No root /assets path or local absolute filesystem path is used.
- If published later, deploy the CONTENTS of site/ as the Pages artifact root so index.html lives directly beneath /wan-animate2-apple-silicon-lab/. Do not deploy it as /site/.
- A deployment method, license and social poster are intentionally not finalized in H2c. No Pages workflow or config is added now.

The evidence mirrors preserve working downloads at a project subpath without depending on unpublished GitHub raw links. Markdown files open as evidence documents; HTML navigation and essential content do not require a Markdown renderer.

## Data and schema contract

experiments.json schema_version remains 1: the H2c adjustment is an additive clarification, not a newly published incompatible schema. For v3 and v4, baseline_experiment_id is ANIMATE2-V2. changed_variable describes a treatment changed from that baseline; fixed_variables contains only maintained baseline values. run_conditions retains the former full configuration unchanged. v3 reference has the original description plus before/after SHA. v4 output-prefix naming is separate artifact_identification, not a semantic experiment treatment. Existing results, SHAs, numeric settings and status are preserved.

Separately authorized experimental edits must update canonical knowledge first, refresh matching site/knowledge experiment files, then reconcile visible HTML values. H2f changes only release metadata and the explicitly allowed legal statements. No client-side fetch is necessary: the reviewed publication snapshot is static and readable with scripting disabled.

## Handoff and gates

Next phase: browser visual QA at desktop / tablet / mobile (minimum 320px), keyboard navigation, disclosure behavior, contrast and long-string wrapping. Use the 20-item checklist in site/README.md. Validate links beneath the simulated project subpath and compare all knowledge copies by SHA-256. Check that post-run ≠ peak is visible near memory graphics.

After QA, separately decide repository license, publication workflow, repository creation and Pages enablement. Create a dedicated 16:9 poster later if desired. Integrate the Works entry only after its public destination is verified; see showcase-integration-plan.md. H2c does not authorize future generation, model deletion or publication.

## H2e — Visual polish and bilingual editorial layer

English remains the visual and structural language: titles, navigation, IDs, status,
metrics and artifact actions. Japanese provides short context blocks for conclusions,
limitations and restoration; there are no line-by-line translations.

The hero now places technical and visual outcomes beside the title, before hardware
metadata on mobile. Major findings 01–02 use larger editorial blocks. Memory bars
carry direct BEFORE / AFTER labels; the swap anchor retains the post-run-versus-peak
warning. Tablet chronology uses two columns; narrow frame diagrams use readable
qualitative intervals instead of tiny frame numbers. Links have at least 44px hit
areas; artifact downloads state their file type and action.

Only HTML/CSS presentation changed. Frozen knowledge, manifests, workflows and
the 2026-10-08 freeze date remain unchanged. No runtime dependencies or publication
operations were added. V4 remains VALIDATED / UNRUN, with historical validation
distinguished from static checks of public templates.

### H2e validation — 2026-10-09 JST

All 20 requested checks passed in this local review. The four exact viewports
were inspected with disclosures closed and all six disclosures open:

| Viewport | Hero status bottom | Document client / scroll width |
| --- | ---: | ---: |
| 1440 x 900 | 669.6px | 1425 / 1425px |
| 768 x 1024 | 584.1px | 753 / 753px |
| 390 x 844 | 486.4px | 375 / 375px |
| 320 x 700 | 469.6px | 305 / 305px |

No horizontal overflow, clipped headings or overflowing SHA fingerprints were
observed. Hero Japanese summaries occupy two lines: 17px on desktop/tablet,
16px on mobile. Supporting Japanese is 15-17px. Status chips are 13px; memory
values are 15px. Mobile frame observations use three readable intervals.

Keyboard skip navigation and cyan 3px focus outlines passed. Enter and Space
toggle native details. Reduced-motion emulation reports auto scrolling, and
disabling JavaScript leaves main content identical. Temporary emulation was
restored after QA. All 19 unique local HTTP resources returned 200 and matched
their on-disk bytes. Nineteen displayed attributed values match the frozen
experiment and model records. Six BEFORE/AFTER memory groups use direct labels;
the swap anchor carries the adjacent post-run-versus-peak qualification.

The 21 site knowledge files and all other files outside the four permitted
modifications retain their prior SHA-256. No dependencies, media, private inputs,
model downloads, generation or Git/GitHub operations were introduced.
Screenshots were inspected in the browser; no persistent QA image deliverables
were retained.

A subjective comparison against the live Greenwakame Lab Home, Works and
HyperFrames Lab detail page rates this draft A: no material visual inferiority
when moving from the showcase into the field report. No P0/P1/P2 presentation
issues remain in the tested viewports. Publication-ready is YES for visual
presentation; this is not a publication action. At the H2e review the license decision was pending. H2f adopts MIT for original
material and prepares the artifact workflow; Pages has not been enabled.
