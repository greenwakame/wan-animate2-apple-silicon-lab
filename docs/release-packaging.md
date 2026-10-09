# Release packaging — Phase H2f

Prepared 2026-10-09 JST. Local preparation only; Git and GitHub publication
operations have not been performed. Experimental freeze remains 2026-10-08 JST.
H2e visual QA is A / publication-ready.

## Repository identity

- Planned repository: https://github.com/greenwakame/wan-animate2-apple-silicon-lab
- Planned Pages entry: https://greenwakame.github.io/wan-animate2-apple-silicon-lab/
- Primary deliverable: site/index.html, served at the Pages project root.
- Original material: MIT, copyright (c) 2026 greenwakame.
- Default branch: main. Start with one branch; do not manually manage gh-pages.
- Suggested initial commit: Initial release: Apple Silicon Wan Animate 2 field report

Suggested repository description:

> Field report on Wan Animate 2 with ComfyUI/MPS on a 32GB Apple M5 MacBook Air: technical completion, identity failures, workflows, memory and runtime.

Suggested topics (not applied to GitHub):

`wan-animate`, `wan-animate-2`, `comfyui`, `apple-silicon`, `mps`, `local-ai`, `video-generation`, `generative-ai`, `machine-learning`, `experiment`.

## Static artifact deployment

.github/workflows/pages.yml uses GitHub's official Actions to package site/
without a build, generator, npm install or Jekyll step. It does not move content
into docs/. The contents of site/ become the artifact root: index.html, assets/,
knowledge/, LICENSE and THIRD_PARTY_NOTICES.md retain relative paths.

Triggers: push to main and workflow_dispatch. The package job also checks
github.ref == refs/heads/main so manual dispatch from another branch cannot
deploy it. The deploy job needs package, uses the github-pages environment,
and exposes steps.deployment.outputs.page_url as its environment URL.
Concurrency group pages does not cancel an in-progress deployment.

Global permission is contents: read. Packaging uses contents: read and
pages: read; deployment alone receives pages: write and id-token: write.
Checkout does not persist credentials. Configure Pages has enablement: false:
a future authorized phase must choose GitHub Actions as the Pages publishing
source. This file does not automatically enable Pages.

The upload uses artifact name github-pages and path site/. It explicitly sets
include-hidden-files: true to preserve the reviewed knowledge/.gitignore linked
from the frozen README. No other hidden site files are present. The official
upload action excludes .git and .github regardless. Do not put private state,
credentials or environment files under site/.

## Official action versions

Stable releases checked on their official release pages on 2026-10-09 JST.
Full immutable commit SHAs are used rather than floating major tags.

| Action | Release | Commit |
|---|---|---|
| [actions/checkout](https://github.com/actions/checkout/releases/tag/v7.0.1) | v7.0.1 | 3d3c42e5aac5ba805825da76410c181273ba90b1 |
| [actions/configure-pages](https://github.com/actions/configure-pages/releases/tag/v6.0.0) | v6.0.0 | 45bfe0192ca1faeb007ade9deae92b16b8254a0d |
| [actions/upload-pages-artifact](https://github.com/actions/upload-pages-artifact/releases/tag/v5.0.0) | v5.0.0 | fc324d3547104276b827a68afc52ff2a11cc49c9 |
| [actions/deploy-pages](https://github.com/actions/deploy-pages/releases/tag/v5.0.1) | v5.0.1 | 368f82528645a54fb793d4d04e342629a3f51346 |

References: [GitHub custom Pages workflows](https://docs.github.com/en/pages/getting-started-with-github-pages/using-custom-workflows-with-github-pages),
[upload action inputs](https://github.com/actions/upload-pages-artifact/blob/v5.0.0/action.yml).
Action runtime code will be fetched on GitHub's runner in a future run; no
action source, packages or model weights are downloaded into this local package.
GitHub-hosted ubuntu-latest is the intended runner.

## Legal and evidence packaging

Root LICENSE is standard MIT text. site/LICENSE is an exact deployment copy.
Root THIRD_PARTY_NOTICES.md describes dependencies, tested distributions and
upstream workflow provenance; site/THIRD_PARTY_NOTICES.md carries the same notice
with relative links adjusted to the deployed knowledge directory.

The 21 knowledge files remain in place. Only these two have authorized legal
updates: knowledge/README.md and knowledge/LICENSE-PLAN.md. The other 19 are
unchanged, including all manifests, workflow templates, experiment documentation
and the historical third-party notice. Its old undecided-license paragraph is a
historical H2 statement superseded by the current scope decision. The footer
links to the current release notice, not that frozen notice. No experimental
numbers, output fingerprints or v4 status are edited.

MIT covers original project material only. Wan/Wan Animate models and source,
Comfy-Org distributions, ComfyUI, upstream workflow concepts and private inputs
retain their respective terms; no model weights, third-party implementations
or private media are redistributed. See ../LICENSE-PLAN.md and
../THIRD_PARTY_NOTICES.md.

## Next authorized publication phase

1. Create the public repository at the planned identity and initialize main
   with the reviewed local package; use the suggested initial commit above.
2. Configure GitHub Pages source as GitHub Actions and allow the github-pages
   environment to deploy main.
3. Trigger workflow_dispatch or rerun the initial main workflow after Pages
   setup. An initial push before setup may fail metadata configuration; the
   workflow deliberately does not enable Pages itself.
4. Verify the actual Actions deployment and public project-subpath URLs,
   including CSS, all evidence downloads and current license/notices.
5. Apply the proposed description and topics. After verifying the deployment,
   update planned/unpublished wording to the actual release state. Integrate
   the main Showcase in its independent phase after the live destination is verified.

These are a future plan, not actions executed in H2f. Local validation cannot
confirm repository settings, account permissions or a successful hosted run.
Six known models (31.758971 GiB total) are retained until the separately decided
H3 cleanup. No main Showcase content is changed.

## Final local validation — 2026-10-09 JST

| Check | Result |
|---|---|
| HTML structure | PASS — balanced tags, unique IDs and valid anchors |
| CSS references | PASS — stylesheet exists; CSS bytes match H2e |
| Relative links | PASS — 115 local Markdown targets resolve; HTML targets resolve |
| Knowledge links | PASS — all 21 files remain present; legal links resolve |
| Pages YAML | PASS — parsed with existing Ruby/Psych; semantic checks passed |
| MIT LICENSE | PASS — standard text, 2026 greenwakame; site copy identical |
| LICENSE-PLAN | PASS — final MIT scope replaces undecided plan |
| Third-party notices | PASS — Apache-2.0 / GPL-3.0 retained; no code/weight redistribution claim |
| Absolute local paths | PASS — no private absolute filesystem path |
| Private username | PASS — no private local username; authorized public brand retained |
| Private media | PASS — no image, video or audio files |
| Model weights | PASS — no model files included or deleted |
| Unwanted binaries/state | PASS — all files UTF-8 text; no cache, browser state or execution UUID |
| Git state | PASS — no .git directory; no Git operation performed |
| V4 | PASS — UNRUN; output and runtime remain null |
| Experimental integrity | PASS — manifests and workflows retain their H2e SHA-256 |
| Pages subpath | PASS — relative site URLs remain inside the planned project prefix |
| Repository URL | PASS — consistent planned owner and repository |
| Pages URL | PASS — consistent planned canonical / OG / README destination |
| Publication quality | PASS — H2e A retained; HTML before footer and CSS unchanged |

The Pages YAML was parsed without installing a parser. The semantic audit
confirmed the four official immutable action pins, matching artifact names,
job dependency, least required job permissions, main restriction, environment
URL and absence of build/run steps. Hidden-site inventory contains only the
reviewed knowledge/.gitignore. Twenty-seven ignore fixtures for model formats,
private inputs, environments, caches, logs, databases and browser state matched;
all 53 actual public files are not ignored. This is a static pattern audit
without Git initialization.

Of the 21 knowledge files, 19 remain byte-identical to H2e. Only README.md legal
statements and LICENSE-PLAN.md changed as authorized. The page content before
the footer and the complete CSS remain byte-identical to H2e; footer edits only
update license scope and repository/notice download links. Existing head
metadata already meets the requirements; no favicon or nonexistent OG image
was added. No hosted workflow or deployment is claimed to have run.

### Frozen experimental fingerprints

| Source | SHA-256 |
|---|---|
| manifests/artifacts.json | ae06ac31e60f020aa1af09c0d6c37661e7d70d8c178938bd4eff42e7c73386fd |
| manifests/environment.txt | 7a0b801bd7958ee3769db0657d8d86c3cd3fcd59aab0aa5a0c8a58da9bebf12e |
| manifests/experiments.json | e37482a44169f7e9600baf6c36e94b1368291b172a97d931a73b9180a7aa15ae |
| manifests/models.json | 3a4278679e0f8407ef5844b2969c6b554bc53f708a464d555f6eb843f7b7fcb1 |
| workflows/animate2/animate2-v2-baseline.json | 7fc786ec1b21d251f4ae7ea7120bb739a16387e0ca4cd50ee1b56bf48dba6d00 |
| workflows/animate2/animate2-v3-reference-aligned.json | d8955a7bd0a01705f2ba91e62eb632d29ca199cf39ec38c9f3788c4238d8bfaf |
| workflows/animate2/animate2-v4-pose-end-070-unrun.json | c33d23cb8daa919dfe8f0a22c5e63a3ed3128bcc9df0b27ab8b2f6262fff860c |
| workflows/vace/vace-512-driver-baseline.json | 8283de5a49b9d001d75301f55486105e4edc949e8451d4301d06e5ce32780635 |

### Reviewed public tree (53 files)

```text
.github/workflows/pages.yml
.gitignore
LICENSE
LICENSE-PLAN.md
README.md
THIRD_PARTY_NOTICES.md
docs/environment.md
docs/experiment-log.md
docs/failures-and-lessons.md
docs/h2c-validation.md
docs/identity-observations.md
docs/limitations-and-unrun-experiments.md
docs/loadvideo-staging.md
docs/memory-and-runtime.md
docs/pages-design-foundation.md
docs/release-packaging.md
docs/sampling-mapping.md
docs/showcase-integration-plan.md
manifests/artifacts.json
manifests/environment.txt
manifests/experiments.json
manifests/models.json
results/README.md
site/LICENSE
site/README.md
site/THIRD_PARTY_NOTICES.md
site/assets/css/site.css
site/index.html
site/knowledge/.gitignore
site/knowledge/LICENSE-PLAN.md
site/knowledge/README.md
site/knowledge/THIRD_PARTY_NOTICES.md
site/knowledge/docs/environment.md
site/knowledge/docs/experiment-log.md
site/knowledge/docs/failures-and-lessons.md
site/knowledge/docs/identity-observations.md
site/knowledge/docs/limitations-and-unrun-experiments.md
site/knowledge/docs/loadvideo-staging.md
site/knowledge/docs/memory-and-runtime.md
site/knowledge/docs/sampling-mapping.md
site/knowledge/manifests/artifacts.json
site/knowledge/manifests/environment.txt
site/knowledge/manifests/experiments.json
site/knowledge/manifests/models.json
site/knowledge/results/README.md
site/knowledge/workflows/animate2/animate2-v2-baseline.json
site/knowledge/workflows/animate2/animate2-v3-reference-aligned.json
site/knowledge/workflows/animate2/animate2-v4-pose-end-070-unrun.json
site/knowledge/workflows/vace/vace-512-driver-baseline.json
workflows/animate2/animate2-v2-baseline.json
workflows/animate2/animate2-v3-reference-aligned.json
workflows/animate2/animate2-v4-pose-end-070-unrun.json
workflows/vace/vace-512-driver-baseline.json
```

Readiness: PASS for the next separately authorized public-repository and Pages
publication phase. Actual repository creation, branch upload, Pages enablement,
runtime permissions and live URL verification remain future operations.
