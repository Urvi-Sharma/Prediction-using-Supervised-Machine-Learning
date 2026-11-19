# Health reels: cloud setup status (19 Nov 2026)

## What I absorbed
The Playbook, README, Master Prompt and the 31-page Handbook. That covers R15/R17/R19/R35, the standing rules (top-30% / kallaway split, box-karaoke captions, no crossfades on jump cuts, spoken words beat the script, Commons-only photos, generated lo-fi music, −14 LUFS / −1 dBTP), the 7 palettes, the 4 looks with their ffmpeg recipes, the engine pipeline and the deliverables.

## Installed in this cloud environment ("Health reels")
| Need | Status |
|---|---|
| ffmpeg 6.1 (deblock, hqdn3d, cas, loudnorm, atempo, rubberband, silencedetect) | ✅ preinstalled, upscale chain tested |
| Python venv `/opt/reelkit/venv` (Linux equivalent of the Windows effects venv) | ✅ |
| opencv + YuNet face model, mediapipe + selfie segmenter (track.py, look.py masks) | ✅ tested |
| faster-whisper **medium** (int8, CPU) | ✅ downloaded and tested |
| skia-python (vector explainers) + EGL libraries | ✅ tested |
| rembg `isnet-general-use` (cut-outs / thumbnails) | ✅ tested |
| Montserrat + Playfair Display (variable fonts, weight 900 works) | ✅ `/opt/reelkit/fonts` |
| pyloudnorm, soundfile, scipy, av | ✅ |
| Network: Hugging Face, Wikimedia Commons (+ upload) | ✅ allowed |

New environment **"Health reels"** (personal): the allowed hosts above, `HF_HOME` + `PYTHONIOENCODING=utf-8`, and a setup script that reinstalls all of this on every fresh session. The script hasn't been tested yet: it runs for the first time when a new session starts on this environment.

## ❗ What I still need from you
1. **The kit's code. This is the blocker.** Only the 4 documents were uploaded. `engine/` (plan_cut, cut_base, tr_base, look, track, spot, build, mid, tail_new, mix, mixlib, gen_lofi, commons/pick/fetch/cutout, sheet, thumb, palettes.json, reel.example.json), `looks/`, `explainer/` and `reference/` all live on your PC at `D:\Claude\HealthReelKit`. Please zip and upload `HealthReelKit` (the reference .mp4s can be left out if they're large).
2. **The `/effects` skill** (`~/.claude/skills/effects/` on your PC, without its `.venv`). spot.py and the spotlight, LED sign, iMessage and checklist effects need fx.py. Zip and upload it too. I'll install it as a skill here and port it to Linux.
3. **Where the kit should live permanently.** Cloud containers get wiped. I recommend a **new private GitHub repo** (e.g. `health-reel-kit`) that I push the ported kit into. Each reel session then clones it, and finished reels' notes and credits can go there too. The current repo (`Prediction-using-Supervised-Machine-Learning`) is unrelated ML coursework, so I'd rather not mix it in. Create the repo and add it to this environment (or tell me to use this one).
4. **Raw clips per reel.** Upload them into the chat. WhatsApp clips are small, so that works. Send phone originals when you have them; they look much sharper than 480×854.

## How the cloud workflow differs from your PC
- **Paths:** I'll port the kit from `D:\Claude\...` and `.venv\Scripts\python.exe` to `/opt/reelkit/venv/bin/python` and a `reels/R<n>/` working folder. Folder numbering continues from **R36** unless you tell me another number. I can't see `D:\Claude\R*` from here, so tell me if other sessions have used later numbers.
- **Delivery:** the FINAL.mp4, thumbnail and shot-list .md get sent to you as files in the chat. Download them from there.
- **Speed:** 4 CPU cores, no GPU. Expect look.py and Whisper to be slower than on your PC (roughly 30–60 min of rendering per reel). I'll run long renders in the background.
- **Alternative:** with Claude Code Remote Control on your PC, a session can run directly on `D:\Claude` with your existing venv. No folders are shared yet.
