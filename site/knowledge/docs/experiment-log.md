# Experiment chronology

This is relative chronology from the prior project record and H1 inventory, frozen 2026-10-08 JST. Exact run timestamps are not reconstructed. Observations below describe recorded results; hypotheses describe intended tests, not established causes.

| Sequence | Stage | Observation | Hypothesis / purpose |
|---:|---|---|---|
| 1 | VACE 1.3B baseline | Technical MPS baseline output exists. | Establish a short video generation path. |
| 2 | Reference identity experiments | Front, left, cleaned and padded reference comparisons were recorded. | Improve identity retention; no universal optimum established. |
| 3 | OpenPose crouch/jump/landing control | Control v2/v3/v4r1 iterations and outputs exist. | Make crouch, airborne phase and landing readable. |
| 4 | 384 to 512 | Control and padded reference were prepared at 512x512. | Test resolution with matching input dimensions. |
| 5 | Successful VACE 512 driver | 512x512, 17 frames, 8 fps, 2.125 seconds output retained. | Use the VACE output as the Animate 2 RGB driver. |
| 6 | HyperFrames integration proof | Prior project record reports integration proof; private assets remain outside this candidate. | Check downstream integration; not evidence of Animate 2 quality. |
| 7 | Animate 2 feasibility investigation | Hardware, formats and native ComfyUI nodes were investigated. | Determine whether a small MPS run is feasible. |
| 8 | INT8 model installation | H1/H2 verify the local INT8 file against Comfy-Org bytes and SHA. | Reduce stored model size; INT8 kernel execution was not proven. |
| 9 | Sampling mapping | 20-step simple sigma sequence matched in the prior comparison; local DPM solver remains an approximation. | Map base conditional-only guidance semantics. |
| 10 | v2 Animate 2 technical generation | PASS, approximately 10537 seconds; identity collapses after F11. | ANIMATE2-V2 |
| 11 | v3 spatial Reference alignment experiment | PASS technically, approximately 8621 seconds; diagnostic D / worse from F1. | ANIMATE2-V3 |
| 12 | v4 pose_end=0.7 planned but unrun | Historical static/UI validation PASS; generation NOT RUN. | ANIMATE2-V4-UNRUN |
| 13 | Project paused | Paused due to hardware, runtime and disk limits; H1/H2 did not resume generation. | Freeze knowledge and preserve future restore information. |

The successful VACE driver SHA is d27024c4787635be5c881d94c5ad54ca5b99670b3482075c5b015694c2aed7a4. v2 and v3 share that driver and seed 12345. The v3 spatial reference change was a single comparison under fixed conditions. v4 is based on v2, with pose_end_percent as its sole intended experimental semantic change; the output prefix only identifies a different result. See [experiments.json](../manifests/experiments.json) for structured settings and [artifacts.json](../manifests/artifacts.json) for original/sanitized SHA lineage. Earlier workflow and generated-output identities remain inventoried without distributing private originals.

No generation was performed for H2. Historical static/UI validation is not a generation result, and technical PASS is not visual PASS.
