# Wan Animate 2 — Pages draft

Local, static publication draft from Phase H2c. Entry point: index.html. Intended public URL: https://greenwakame.github.io/wan-animate2-apple-silicon-lab/. It is not published. Original material is MIT-licensed; see LICENSE and THIRD_PARTY_NOTICES.md in this directory.

## Source layout

index.html — complete field report; no script required.
assets/css/site.css — system fonts, editorial layout, CSS diagrams, responsive rules and reduced-motion support.
knowledge/ — 21 reviewed evidence files, including the historical .gitignore.
H2f updates only README.md license statements and LICENSE-PLAN.md; the other
19 knowledge files retain their H2e bytes. All experimental data is unchanged.
LICENSE and THIRD_PARTY_NOTICES.md — current release legal material, copied
from the repository with relative notice links adapted for the deployed site.

Canonical experiment data stays in docs/, manifests/ and workflows/.
Keep the frozen knowledge evidence unchanged outside separately authorized
updates. H2f's two legal exceptions are documented above; root README/.gitignore
and current notices now serve release packaging, while their knowledge copies
retain the historical H2 context. Compare experimental files by SHA-256. Update visible HTML from those canonical values. Do not place private inputs, character media, generated MP4s or weights anywhere under this directory.

## Local preview

Serve this directory with an existing Python runtime: python3 -B -m http.server 8765 --bind 127.0.0.1 --directory site (from the repository root). Open http://127.0.0.1:8765/. Stop the temporary preview when finished. No dependencies need installation.

For a subpath test, expose the contents of site/ beneath /wan-animate2-apple-silicon-lab/ with an in-memory route mapping; do not change URL references to absolute root paths.

The prepared .github/workflows/pages.yml uploads the contents of site/ directly
as the Pages artifact root. No build, Jekyll, npm or framework is involved.
main pushes and workflow_dispatch trigger packaging; deployment is restricted
to main and the github-pages environment. Configure the Pages source as GitHub
Actions in the separately authorized publication phase, then trigger/rerun the
workflow. H2f does not enable Pages or execute the workflow.

The upload action explicitly includes hidden files so the reviewed
knowledge/.gitignore remains available to frozen README links. It is the only
hidden site file; keep private state and secrets outside site/.
See ../docs/release-packaging.md for action pins, metadata and release checks.

## Static validation checklist

1. index.html exists.
2. assets/css/site.css exists.
3. No JS is used; essential content is static.
4. Relative asset and evidence references resolve.
5. No /Users or other absolute local filesystem paths.
6. No private local username or character identity leaks (the authorized public Greenwakame brand and account links are intentional).
7. No private media files.
8. No model weight files.
9. Experimental numbers derive from frozen knowledge.
10. v4 remains UNRUN, without fabricated output or runtime.
11. Runtime values match the experiment manifest.
12. Before/after memory values match the experiment manifest.
13. Model total equals the sum of six byte counts, expressed in GiB.
14. Technical and visual success are separate outcomes.
15. Responsive CSS includes desktop, tablet and minimum 320px mobile layouts.
16. prefers-reduced-motion disables smooth scrolling.
17. No framework, CDN or package dependency.
18. No package install required or performed.
19. Every local URL remains within the project subpath.
20. Basic HTML structure, IDs, anchors and accessible labels are valid.

## Browser visual QA handoff

Review at 1440px, 1024px, 768px, 390px and 320px. Check no horizontal overflow, stacked timeline and large metrics on mobile, legible hero and numbers, evidence download behavior, keyboard focus and native details disclosures. Ensure the frame strip is understood as qualitative markers and memory bars as separate system indicators on a common 0–32 GiB scale; post-run is not peak.

The draft is ready for browser QA. Static checks do not by themselves prove all viewport layouts, screen-reader behavior or browser contrast results. No generation, deployment or publication is part of this handoff.

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

H2e local visual QA passed at 1440x900, 768x1024, 390x844 and 320x700.
See ../docs/pages-design-foundation.md for the measured results. Visual assessment:
A; no outstanding P0/P1/P2 presentation issues in those viewports. This remains
an unpublished local draft; no Git or Pages operation was performed.
