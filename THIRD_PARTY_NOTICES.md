# Third-party notices

This inventory identifies references, dependencies and tested distributions.
No ComfyUI code, Wan Animate source or model weights are redistributed by this
repository. The repository's MIT License applies only to original project material;
all third-party material remains under its respective upstream terms.

| Project / distribution | Recorded license | Source |
|---|---|---|
| Wan-Video/Wan-Animate-2 | Apache-2.0 | [Repository](https://github.com/Wan-Video/Wan-Animate-2), [LICENSE](https://github.com/Wan-Video/Wan-Animate-2/blob/main/LICENSE) |
| Comfy-Org/Wan-Animate-2 model repository | Apache-2.0, declared on model card | [Distribution](https://huggingface.co/Comfy-Org/Wan-Animate-2) |
| Comfy-Org/Wan_2.1_ComfyUI_repackaged | Apache-2.0, declared on model card | [Distribution](https://huggingface.co/Comfy-Org/Wan_2.1_ComfyUI_repackaged) |
| ComfyUI | GPL-3.0 | [Repository](https://github.com/Comfy-Org/ComfyUI), [LICENSE at recorded commit](https://github.com/Comfy-Org/ComfyUI/blob/73c9bad4d21e7addbe1d13bc92eee0f1431b017d/LICENSE) |

The licenses above were confirmed in H1 and reviewed via the linked official pages during H2 on 2026-10-08. Model URLs, upload revisions, bytes and SHA-256 are in [models.json](manifests/models.json). A model-card license label does not resolve all rights in inputs, outputs or separately distributed components.

## Workflow references and provenance

The sanitized workflow JSON files refer to third-party node type names, including ComfyUI's WanVaceToVideo, WanAnimate2ToVideo, ModelSamplingSD3, LoadVideo, SamplerCustom and SamplerDPMPP_2M_SDE. They derive from locally adapted workflow graphs with upstream blueprint structure. Relevant upstream context includes ComfyUI blueprints named `Motion Transfer (Wan Animate 2).json` and `FLF2V (Wan2.1 VACE).json`. Node references do not bundle implementations or transfer ownership of the upstream structure.

Animate templates retain the generic upstream runtime negative prompt and a generic motion prompt; private appearance text is replaced. Upstream negative-prompt source reference: [Wan Animate 2 pipeline](https://github.com/Wan-Video/Wan-Animate-2/blob/main/pipelines/wan_animate_2_pipeline.py), historically retrieved 2026-10-06. No upstream Python source is copied. Original/sanitized workflow identities are in [artifacts.json](manifests/artifacts.json). Review attribution and any applicable redistribution conditions before publication; do not assume a new license for original documentation covers third-party material.

## Private inputs and outputs

No private/source character PNG, reference sheet, generated MP4, staged driver or HyperFrames asset is included. Public-release rights have not been determined. H1 found workflow/prompt metadata in all 20 generated MP4s and the staged driver. This candidate excludes those files; a later media release requires separate rights and metadata review.

## Original repository material

Original project HTML, CSS, documentation, manifests and helper material are
MIT-licensed, copyright (c) 2026 greenwakame. See [LICENSE](LICENSE) and the
[scope decision](LICENSE-PLAN.md). This does not relicense the upstream workflow
concepts, graph structure, retained generic prompts, models or source referenced
above. Private/user-provided media are not included.

## GitHub Actions deployment dependencies

The release workflow references GitHub's official actions/checkout,
actions/configure-pages, actions/upload-pages-artifact and actions/deploy-pages.
Their implementation code is fetched by GitHub Actions only when a future
workflow runs; it is not vendored in this repository. Each action retains its
own upstream license. The checked release versions and immutable commit pins
are recorded in [release-packaging.md](docs/release-packaging.md).
