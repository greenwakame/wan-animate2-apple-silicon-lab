# Memory and runtime observations

Apple M5 MacBook Air, 32 GiB unified memory, MPS; Animate 2 INT8 ConvRot, 512×512, 17 frames, batch 1. Values are from prior runs, preserved by H1; H2 performs no generation. GiB are binary units.

| Run | Approximate runtime | Pre available | Pre compressed | Pre swap | Post available | Post compressed | Post swap |
|---|---|---:|---:|---:|---:|---:|---:|
| v2 | 2h 55m 37s / 10,537 s | 13.00 | 3.03 | 0.00 | 6.42 | 15.78 | 17.76 |
| v3 | 2h 23m 41s / 8,621 s | 13.09 | 2.88 | 0.00 | 6.30 | 15.57 | 17.69 |

v4 has no runtime, output or pre/post generation measurement: generation NOT RUN. VACE runtime was not frozen here; it is unknown, not zero. The v2/v3 runtimes describe approximately the recorded end-to-end generation, not isolated sampling or a benchmark with controlled background activity.

## Interpretation limits

- Post measurement != peak memory. No continuous peak series is available.
- RSS aggregate != physical exclusive usage; summing resident sets can count shared mappings more than once.
- memory_pressure free percentage != Activity Monitor green/yellow/red; it is not a recorded color-state measurement.
- MPS uses shared unified memory. CPU offload does not provide separate physical RAM.
- System available/compressed/swap values include other host processes; they are not an exclusive allocation budget for the model.
- A shorter v3 runtime does not demonstrate an optimization: one run per condition, different reference content and no stage timing/controlled repeats.

The 32GB M5 technically completed these short runs. The long runtime and large memory compression/swap do not support an assessment of practical or comfortable operation. v4 was stopped at the prior memory feasibility C decision, then the project was paused. Preserve the current environment; model storage size and runtime physical memory demand are different quantities.

See [identity observations](identity-observations.md) for visual failures and [experiments.json](../manifests/experiments.json) for machine-readable pre/post values.
