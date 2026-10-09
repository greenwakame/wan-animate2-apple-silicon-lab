# Recorded results without media

No private/source character images, reference sheets, generated MP4s, staged drivers or HyperFrames assets are included. Model weights are also excluded. H1 found workflow/prompt metadata in all 20 generated outputs and the staged driver; visible-media review alone cannot establish public-release safety.

| Experiment | Original output filename | Bytes | Dimensions / frames / fps | Technical / visual result |
|---|---|---:|---|---|
| VACE-512 | vace13b_cleanhires_v4r1_512_17_00001_.mp4 | 105,180 | 512×512 / 17 / 8 | Successful project driver baseline |
| ANIMATE2-V2 | wananimate2_rgbdriver_smoke_512_17_v2_00001_.mp4 | 160,876 | 512×512 / 17 / 8 | Technical PASS; F12 onward collapse |
| ANIMATE2-V3 | wananimate2_rgbdriver_smoke_512_17_refaligned_v3_00001_.mp4 | 141,731 | 512×512 / 17 / 8 | Technical PASS; visual D / worse from F1 |
| ANIMATE2-V4-UNRUN | None | — | Planned 512×512 / 17 / 8 | Generation NOT RUN |

All three recorded videos are 2.125 seconds with no audio. Runtime: v2 approximately 10,537 seconds; v3 approximately 8,621 seconds. Pre/post memory and caveats are in [memory-and-runtime.md](../docs/memory-and-runtime.md).

```text
VACE-512 output SHA-256
d27024c4787635be5c881d94c5ad54ca5b99670b3482075c5b015694c2aed7a4

ANIMATE2-V2 output SHA-256
2a5195ed39e3e6522bdfd603bc0a92d5ca5f5cd2cbe07e098a3c8179a3791140

ANIMATE2-V3 output SHA-256
45cf2edab69190c0bd403f80d65e105ad2b072a919a015704b939d3be8557b5f
```

The [artifact manifest](../manifests/artifacts.json) preserves 20 output identities and selected input lineage. Failed outputs remain private comparison evidence; they are not discarded or relabeled as successes. Sanitized workflows have their own SHA identities and cannot recreate the private outputs without the original inputs/prompts. Media rights and metadata sanitization must be reviewed separately before any later release.
