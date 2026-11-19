# FaceSwap Studio — Stage 1

This starter validates uploaded video files before any processing job is created.
It does **not** perform face replacement.

## Requirements
- Python 3.11+
- FFmpeg installed and available as `ffmpeg`
- Git

## Run locally
```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r worker/requirements.txt
python worker/processor.py --video ./sample.mp4
```

The CLI checks:
- MP4/MOV extension and 100 MB maximum
- video can be opened
- duration/FPS/frame count are valid
- sampled frames contain exactly one detectable face

The face detector is a basic preflight check, not identity verification or liveness detection.
Do not use this result as proof that the person has consented.

## GitHub
Create a **private** repository named `faceswap-studio`, upload these files,
then open Code → Codespaces → Create codespace on main.

## Next stage
Add server-side consent verification, secure direct uploads, job records, and
a queue. GPU processing should only be enabled after consent and identity
checks are implemented and tested.
