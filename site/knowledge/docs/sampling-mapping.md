# Animate 2 base smoke sampling mapping

This is the prior comparison decision frozen for the local experiment, not an official exact reproduction. It concerns the non-distilled base model, with no LoRA.

| Parameter | Local value |
|---|---|
| steps | 20 |
| ComfyUI CFG | 1.0 |
| shift | 5.0 |
| scheduler | simple |
| sampler | SamplerDPMPP_2M_SDE |
| solver | midpoint |
| eta | 0.0 |
| s_noise | 1.0 |
| noise_device | cpu |
| denoise | 1.0 |
| seed | 12345, fixed |
| add_noise | true |

## Semantic mapping and remaining differences

The upstream guide=0 conditional-only semantics are represented by ComfyUI CFG=1.0, which selects the conditional prediction without classifier-free extrapolation. This does not mean that the numeric guidance values are interchangeable across implementations. The prior decision describes upstream guide≤1 as the conditional-only branch.

The shift transform is equivalent: for normalized sigma s, shifted sigma = shift*s / (1 + (shift-1)*s). The 20-step simple sigma sequence matched in the prior comparison. These two checks do not establish identical full sampling trajectories.

The local DPM solver is the closest approximation selected in the investigation. DPM++ 2M SDE with eta=0 and midpoint remains different from the upstream implementation. There is a local first-sigma correction/offset, and upstream uses integer model timesteps whereas ComfyUI uses floating timesteps. Different solver history, timestep handling and rounding can affect the output even when the listed sigmas agree. No bitwise/output-equivalence claim is made; H2 did not repeat the numerical comparison.

The local workflow places ModelSamplingSD3 (shift 5) before BasicScheduler and SamplerCustom. Preserve these connections as well as the values. CFG=1 does not justify deleting the linked negative conditioning from a template; it preserves the recorded graph.

This mapping is specific to Animate 2. The VACE driver uses KSampler: 20 steps, CFG 6, uni_pc, simple, denoise 1, seed 12345, ModelSamplingSD3 shift approximately 8 and VACE strength 1. Those settings are frozen separately in [experiments.json](../manifests/experiments.json).

The public template retains numeric sampling settings but replaces private appearance prompts. It cannot reproduce the original output SHA. Upstream implementation reference: [Wan Animate 2 pipeline](https://github.com/Wan-Video/Wan-Animate-2/blob/main/pipelines/wan_animate_2_pipeline.py); that URL is a contextual reference, not a frozen upstream-code dependency.
