# Environment snapshot and restore limits

Frozen from H1 on 2026-10-08 JST; H2 does not install/update packages, start/stop ComfyUI or run model inference.

| Item | Recorded value |
|---|---|
| macOS | 27.0.1 |
| Build | 26A434 |
| Hardware | Mac17,3; Apple M5 MacBook Air |
| Architecture | arm64 |
| Unified memory | 32 GiB / 34,359,738,368 bytes |
| ComfyUI | 0.37.0 |
| ComfyUI HEAD | 73c9bad4d21e7addbe1d13bc92eee0f1431b017d |
| Python | 3.12.14 |
| torch | 2.15.0.dev20260929 |
| torchvision | 0.30.0.dev20260929 |
| torchaudio | 2.11.0 |
| MPS built / available | true / true on host |
| ffmpeg / ffprobe | 9.0.2 / 9.0.2 |

**The host result is authoritative for this experiment.** A historical sandbox check returned MPS available=false; the same environment on the host returned true. No model load or MPS arithmetic test was added during H1/H2.

The hardware model is intentionally retained as public environment knowledge; it is a model identifier, not a serial number. No personal machine name is recorded.

The [environment freeze](../manifests/environment.txt) contains the full H1 pip freeze with version pins only, preceded by environment facts in comments. Examples include frontend 1.52.7, transformers 5.17.0, safetensors 0.8.0, numpy 2.5.3, pillow 12.3.0 and av 19.0.0. No local paths, usernames or environment command headers are retained.

The HEAD was read from the local Git metadata in H1; no Git command was used. A clean working tree at that commit was not established. Preserve the local source tree separately. The pins are a snapshot rather than a portable, hash-locked environment specification. Availability of matching nightly wheels and future MPS compatibility are unverified; retain the current environment and its relevant nightly package cache. H2 does not nominate the environment for deletion.

For restoration, follow [After deleting local model weights](../README.md#how-to-resume-later--after-deleting-local-model-weights). File categories and verification identities are in [models.json](../manifests/models.json).
