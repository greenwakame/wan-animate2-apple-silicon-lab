# LoadVideo output annotation and input staging

## Observed behavior

The original workflow used `vace13b_cleanhires_v4r1_512_17_00001_.mp4 [output]`. The backend validator resolved the output reference, but loading the workflow in the UI produced “メディア入力が不足しています” (missing media input). The root cause was not established. Backend resolution success and UI media availability are different observations; no confirmed ComfyUI defect mechanism is claimed.

## Recorded workaround

The VACE output was copied byte-identically to `input/wananimate2-driver-vace-512-17.mp4` in the original experiment. No re-encoding occurred. Both source and staged file have 105,180 bytes and SHA-256:

```text
d27024c4787635be5c881d94c5ad54ca5b99670b3482075c5b015694c2aed7a4
```

The staged driver is 512×512, 17 frames, 8 fps, 2.125 seconds. Subsequent UI load passed. v2/v3/v4 reference the staged input. H2 does not perform this copy again, operate the UI, or include either video in this candidate.

The public Animate templates use `driver.mp4` as a user-supplied input name. The VACE template uses `pose-control.mp4`; this is an OpenPose control, not the RGB Animate driver. Replace names locally only when inputs are available, and check bytes/SHA when reusing the historical driver. Do not silently re-encode or resample during a controlled comparison.

Both the generated original and staged driver contain embedded workflow/prompt metadata. Byte-identical staging retains this metadata; it does not sanitize media. See [third-party notices](../THIRD_PARTY_NOTICES.md).
