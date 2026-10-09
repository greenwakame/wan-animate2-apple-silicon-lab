# Wan Animate 2 on Apple Silicon — M5 / 32GB Experiment Notes

## Planned GitHub Pages site

[Read the field report](https://greenwakame.github.io/wan-animate2-apple-silicon-lab/) — planned destination, not yet published.

The Pages field report is the primary deliverable. Its local entry point is
[site/index.html](site/index.html); this README indexes the supporting evidence
and restoration material. The central conclusion is **TECHNICAL PASS ≠ VISUAL
SUCCESS**. See the [release packaging and deployment plan](docs/release-packaging.md).

**This is not a recommended production configuration.** This repository candidate is an experiment, engineering notes and feasibility study for Wan VACE and Wan Animate 2 on an Apple M5 MacBook Air with 32 GiB unified memory and MPS.

## What this repository is

A knowledge freeze of a paused local investigation: environment pins, model retrieval identities, result metrics, failure observations and sanitized workflow templates. Freeze date: 2026-10-08 JST. Technical completion and visual quality are assessed separately.

## What this repository is NOT

A success recipe, proof of comfortable performance on M5 / 32GB, a production recommendation, a quality-success claim, or an official exact reproduction of the upstream Animate 2 sampler. This candidate has not been initialized as a Git repository or published. Original repository material is MIT-licensed; third-party terms remain separate.

## Tested hardware and software

| Item | Experiment snapshot |
|---|---|
| Hardware | Apple M5 MacBook Air, 32 GiB unified memory, arm64, MPS |
| OS | macOS 27.0.1, build 26A434 |
| ComfyUI | 0.37.0; HEAD 73c9bad4d21e7addbe1d13bc92eee0f1431b017d |
| Python | 3.12.14 |
| PyTorch | torch 2.15.0.dev20260929; torchvision 0.30.0.dev20260929; torchaudio 2.11.0 |
| Video tools | ffmpeg / ffprobe 9.0.2 |

The host MPS result is authoritative. A sandbox reported MPS unavailable; that was not treated as a host MPS failure. See [environment details](docs/environment.md) and the [complete environment freeze](manifests/environment.txt).

## Models

Animate 2 used Wan Animate 2 INT8 ConvRot, UMT5 XXL FP16, CLIP Vision H and Wan 2.1 VAE BF16. VACE used Wan 2.1 VACE 1.3B FP16, the same UMT5, and the older Wan 2.1 VAE. No model weights are included. The [six-record model manifest](manifests/models.json) is the single source of truth for URLs, revision-specific retrieval, filenames, categories, sizes and SHA-256. Use each category beneath ComfyUI's models directory. The two VAE files are distinct.

The tested files are Comfy-Org distributions packaged for ComfyUI; they are not asserted byte-identical to original upstream Wan checkpoints.

## Technical success, visual limitations, runtime and memory

At 512×512, 17 frames and batch 1, the Animate 2 INT8 path completed sampling, VAE decoding and video saving. This does not demonstrate that arithmetic used native INT8 kernels. Outputs are 8 fps and 2.125 seconds with no audio.

| Experiment | Technical result | Visual observation | Approximate runtime |
|---|---|---|---|
| VACE-512 | PASS | Successful driver baseline in this project | Not frozen |
| Animate 2 v2 | PASS | Identity relatively good F1–F11; collapse from F12; severe F17 collapse | 2h 55m 37s / 10,537 s |
| Animate 2 v3 | PASS | Reference alignment: D / worse; face/hood collapse from F1 | 2h 23m 41s / 8,621 s |
| Animate 2 v4 | UNRUN | No visual result; pose_end_percent 0.7 planned | None |

v2 post-run memory was available 6.42 GiB, compressed 15.78 GiB and swap 17.76 GiB. v3 post-run values were 6.30 / 15.57 / 17.69 GiB. These are **post measurements, not peaks**. MPS and CPU offload share the same physical unified memory. Long runtime and large compression/swap prevent an assessment of practical or comfortable use. See [memory/runtime](docs/memory-and-runtime.md) and [identity observations](docs/identity-observations.md).

## Experiments and current stopping point

The investigation moved from VACE 1.3B, reference identity comparisons and OpenPose crouch/jump/landing control through 384→512 resolution and a VACE RGB driver to Animate 2 base sampling, v2 generation and v3 reference alignment. A prior HyperFrames integration proof is recorded as project context; private assets are excluded.

v3 reduced subject oversizing but worsened identity and motion readability. One fixed-condition run does not prove that reference shrinking is generally harmful. v4 changes pose_end_percent 1.0→0.7 relative to v2; it passed historical static and UI checks but generation was **NOT RUN**. The percentage concerns denoising progression, not 70% of video duration. The project paused at memory feasibility C and then due to hardware/runtime/disk limits. See [chronology](docs/experiment-log.md), [experiment manifest](manifests/experiments.json) and [unrun experiments](docs/limitations-and-unrun-experiments.md).

## Reproduction status and required private inputs

The four public JSON files are **template / reference workflows**, not ready-to-run reproductions. Private character descriptions are replaced with `<CHARACTER_DESCRIPTION>`; VACE's private negative prompt is replaced with `<NEGATIVE_PROMPT>`. Private/source character PNGs, reference sheets, generated MP4s, staged drivers and HyperFrames assets are not included. Supply your own authorized inputs:

| Template | User-supplied files beneath ComfyUI input | Preparation |
|---|---|---|
| VACE 512 driver | reference.png; pose-control.mp4 | 512×512 padded reference; 512×512 OpenPose crouch/jump/landing control, 17f, 8fps |
| Animate 2 v2 | reference.png; driver.mp4 | Original padded reference; 512×512 RGB driver, 17f, 8fps |
| Animate 2 v3 | reference-aligned.png; driver.mp4 | Separate aligned reference canvas: content 174×342 at (168,118) on 512×512 |
| Animate 2 v4 UNRUN | reference.png; driver.mp4 | Same reference/driver as v2; pose_end_percent=0.7 |

Replace placeholders and choose local filenames. H2 checked JSON syntax, graph links, preserved numeric settings and privacy; it did not load these public templates into a running server or generate anything. Private prompts/assets are necessary for exact reproduction of the recorded outputs, so a public template with different inputs will produce a different experiment.

## Repository contents

- [Experiment log](docs/experiment-log.md): ordered observations and hypotheses.
- [Environment](docs/environment.md): hardware/software snapshot and restore limits.
- [Sampling mapping](docs/sampling-mapping.md): values, semantic mapping and approximation caveats.
- [Memory and runtime](docs/memory-and-runtime.md): pre/post measurements and interpretation limits.
- [LoadVideo staging](docs/loadvideo-staging.md): UI/backend discrepancy and byte-identical workaround.
- [Identity observations](docs/identity-observations.md): v2/v3 frame observations and media metadata warning.
- [Failures and lessons](docs/failures-and-lessons.md): controlled comparisons and stop-on-error policy.
- [Limitations and unrun experiments](docs/limitations-and-unrun-experiments.md): v4 and unresolved questions.
- [VACE workflow](workflows/vace/vace-512-driver-baseline.json), [Animate v2](workflows/animate2/animate2-v2-baseline.json), [v3](workflows/animate2/animate2-v3-reference-aligned.json), [v4 UNRUN](workflows/animate2/animate2-v4-pose-end-070-unrun.json).
- [Models](manifests/models.json), [artifacts](manifests/artifacts.json), [experiments](manifests/experiments.json), [environment freeze](manifests/environment.txt).
- [Results](results/README.md), [third-party notices](THIRD_PARTY_NOTICES.md), [MIT License](LICENSE), [license scope](LICENSE-PLAN.md), [.gitignore](.gitignore).

## License

Original HTML, CSS, documentation, manifests and project-authored helper material
are covered by the [MIT License](LICENSE), copyright (c) 2026 greenwakame.
Third-party models, source, workflow concepts and private media are not relicensed.
See the [license scope](LICENSE-PLAN.md) and [third-party notices](THIRD_PARTY_NOTICES.md).
No model weights, ComfyUI source or private media are redistributed here.

## Known limitations

Only short 17-frame experiments are frozen. Peak memory, exclusive physical memory, per-stage timings, repeated seeds and long-video behavior were not established. The sampling solver is an approximation. Private media rights are unreviewed. A commit ID and pip pins do not prove a clean source checkout or ensure that nightly wheels remain available.

## How to resume later — After deleting local model weights

1. Prepare ComfyUI 0.37.0 at the recorded commit. Preserve the existing source, private inputs, workflows, results and environment; the candidate does not back up the full source tree or private media.
2. Retain the current Python environment when possible. If rebuilding is needed, use Python 3.12.14 and [environment.txt](manifests/environment.txt) as a snapshot, obtain compatible pinned packages, and verify MPS on the host. Nightly wheel availability/compatibility needs a fresh check.
3. Retrieve the six weights using [models.json](manifests/models.json), preferably its revision-specific download URLs. This phase does not perform downloads.
4. Verify each exact byte count and SHA-256 before loading. Stop on a mismatch.
5. Place each file into ComfyUI models / its manifest category, using the exact filename and case.
6. Supply your own private reference, control and driver inputs; keep original private assets for reproducing the historical local experiment.
7. Adapt the sanitized workflow template to your local input names and replace prompt placeholders. Review host memory feasibility before any future UI validation or generation. Keep driver, seed and sampling fixed for a one-variable comparison.

Further runs require a separate decision. This freeze does not establish that v4 improves quality. The original-material MIT decision is complete. Public release requires a separately authorized publication phase.

## Japanese notes / 日本語概要

M5 MacBook Air・32 GiB・MPSで512×512／17フレームの技術生成は完走しましたが、長時間実行と大きな圧縮・swapを伴いました。v2はF12以降にidentity崩壊、v3はF1から悪化、v4は未実行です。快適動作や品質成功を示すものではありません。モデルとprivate mediaは非同梱で、公開JSONは入力・prompt差し替えが必要なテンプレートです。
