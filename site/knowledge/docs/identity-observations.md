# Identity observations and media exclusion

Frame labels are one-based (F1–F17). These are qualitative observations from prior visual review, not automated similarity scores or a statistical evaluation. H2 does not re-generate or publicly distribute the private review frames.

## v2: technical PASS, visual limitation

F1–F11 retained the reference identity relatively well. Identity collapsed from F12 onward, with severe collapse at F17. Completing sampling, decoding and MP4 saving is technical success; it is not visual-quality success. The result does not establish production usability or stable identity across a longer sequence.

## v3: reference alignment worsened this fixed-condition run

Reference content was resized to 174×342 and pasted at x168, y118 on a 512×512 canvas. The experiment kept the v2 driver, seed and sampling settings. Subject oversizing was reduced, but face/hood collapse appeared from F1; a right-side vertical artifact persisted, normal identity did not recover, and motion readability decreased. The diagnostic result was D / worse.

Hypothesis: reference scale/alignment might reduce spatial disagreement with driver F1. Observation: that prepared reference worsened this run. It does not establish that reference shrinking in general is harmful or isolate scale, placement, padding and content as independent causes. No multi-seed repeat was run.

## v4: no visual observation

pose_end_percent=0.7 is a planned denoising-progress experiment based on v2. Historical static/UI checks passed; generation NOT RUN. It cannot be called an improvement or a failed visual generation.

## Private media and metadata warning

H1 found workflow/prompt metadata in all 20 generated MP4 files and the staged driver. Videos can expose private prompt and provenance information even when their visible pixels appear suitable for release. No PNG/JPEG, generated video, staged driver, private character sheet or HyperFrames asset is included. The [results index](../results/README.md) and [artifact manifest](../manifests/artifacts.json) retain filenames, metrics and hashes without media. Any later public media release requires its own rights and metadata review.
