# Limitations and unrun experiments

## v4 pose_end_percent=0.7 — explicitly UNRUN

Baseline: v2. Only intended experimental semantic change: pose_end_percent 1.0→0.7. Output prefix changes distinguish future results. Original workflow SHA-256: 09616b54976d8d959aca3b69434ce60110a056bfc45783afde1ff8885dd7821a.

Historical static validation PASS; historical UI validation PASS; **generation NOT RUN**. The experiment stopped at memory feasibility C, followed by a project pause for hardware/runtime/disk limits. No v4 generated output, runtime, visual observation or generation-memory measurements exist in this freeze. H2 only performs static checks of the public template.

pose_end_percent describes the denoising progression interval of pose conditioning, not video time, frame 70%, or a cutoff after F12. Hypothesis: earlier pose-conditioning release might improve late identity retention. No observed result supports that hypothesis yet.

## Scope limits

- Two Animate technical completions are frozen at 512×512, 17 frames, batch 1; no broad hardware benchmark or long-video feasibility claim.
- v2 late collapse and v3 degradation have no confirmed cause; no multi-seed or replicated comparison.
- v3 spatial-reference preparation includes scale and position changes; a single run cannot isolate them or generalize reference-size advice.
- Sampling mapping is a closest approximation with first-sigma/timestep differences, not upstream exact reproduction.
- Peak memory, exclusive physical usage and per-stage timing are unmeasured.
- Native INT8 arithmetic/kernel use was not demonstrated by loading an INT8 stored checkpoint.
- The current source checkout's equality to its HEAD is unverified. Nightly package availability and future compatibility remain uncertain.
- Private media/prompt rights and final repository licensing remain unreviewed. Public templates require user inputs and are not exact historical reproductions.

## Future tests requiring a separate decision

v4 could be evaluated against v2 using identical private reference, byte-identical driver, seed and sampling only if host memory/runtime feasibility is accepted. Repeated seeds, smaller settings or other reference preparations would be new experiments, not retroactive results. H2 does not authorize or execute them. Review the candidate and license in H2b before any GitHub publication.
