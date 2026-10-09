# Failures and engineering lessons

## Separate different failure boundaries

Backend LoadVideo validation passed for an output annotation while UI loading reported missing media. The byte-identical input staging workaround resolved the observed UI load. Its success is not proof of the underlying cause.

v2/v3 technical generation succeeded but visual quality was inadequate. v4 historical static/UI validation passed while generation was not run. Keep these statuses separate in reports and manifests. A stalled UI interaction, stale element, connection error, schema failure and memory-feasibility stop are different failures; do not turn an incomplete check into PASS.

## Preserve one-variable comparisons

Keep seed, driver SHA, model, dimensions, frame count and sampling fixed. In v3 the intended experimental change was the prepared spatial reference, which combined resizing/placement/padding; this single comparison cannot attribute causality to each component. In v4 the sole experimental semantic change relative to v2 is pose_end_percent 1.0→0.7; output prefix changes are identification only. Do not introduce a fallback sampler, silent resize, new seed, additional queue or re-encode after an error and still label it the same experiment.

## Public template metadata cleanup

H2 observed stale `widgets_values_named` in the v4 source: pose_end_percent remained 1.0 even though `widgets_values` specifies 0.7; the named SaveVideo prefix also still named v2. The public copy synchronizes these values to the intended settings/public prefix. Private source bytes remain unchanged. This cleanup is not a historical generation result.

Public copies omit workflow UUID, browser viewport state, source provenance blocks, upstream model-download metadata in nodes and all original node titles; they retain core node identifiers/version hints, graph sockets, numeric settings and links. Private appearance text is replaced in both positional and named widgets, input names are portable, and output prefixes identify each public template. Required sampling/provenance knowledge is written explicitly in reviewed docs/manifests instead of copying incidental metadata.

## Stop-on-error and resume policy

Stop at a failed validation or unsuitable memory boundary; report what did and did not run. Do not automatically queue again or change conditions to obtain a PASS. The project stopped before v4 and remains paused. After restoration, verify file identities and host capability before a separately decided future test. Preserve failed v3 results and original private inputs as comparison evidence.

See [unrun experiments](limitations-and-unrun-experiments.md) and [restoration guide](../README.md#how-to-resume-later--after-deleting-local-model-weights).
