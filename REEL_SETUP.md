# Health reels: cloud setup status (19 Nov 2026)

## What I absorbed
The Playbook, README, Master Prompt and the 31-page Handbook. That covers R15/R17/R19/R35, the standing rules (top-30% / kallaway split, box-karaoke captions, no crossfades on jump cuts, spoken words beat the script, Commons-only photos, generated lo-fi music, −14 LUFS / −1 dBTP), the 7 palettes, the 4 looks with their ffmpeg recipes, the engine pipeline and the deliverables.

## Installed and tested (environment "Health reels")
| Need | Status |
|---|---|
| ffmpeg 6.1 (deblock, hqdn3d, cas, loudnorm, atempo, rubberband, silencedetect) | ✅ upscale chain tested |
| Python venv `/opt/reelkit/venv` | ✅ |
| opencv + YuNet, mediapipe + selfie segmenter | ✅ |
| faster-whisper medium (CPU) | ✅ |
| skia-python + EGL libraries | ✅ |
| rembg `isnet-general-use` | ✅ |
| Montserrat + Playfair Display | ✅ `/opt/reelkit/fonts` |
| **`/effects` skill** (`Vibha-Ramprakash/claude-video-effects`, 51 effects, fx.py + words.py) | ✅ installed at `~/.claude/skills/effects`, spotlight + reject-stamp test stills render |
| Network: Hugging Face (+ its download hosts), Wikimedia Commons | ✅ |

The setup script reinstalls all of the above in every fresh session. It hasn't been tested yet: it runs for the first time when a new session starts on this environment.

## Kit status
- ✅ HealthReelKit received (26 Nov), ported to Linux and dry-run end to end (see `HealthReelKit/LINUX_CLOUD.md`).
- ⚠️ Not committed: this repo is public. The kit needs a private home.

## Decisions recorded
- **Naming:** reels go in the local folder you share, named `R1 - <Reel topic>`, `R2 - <Reel topic>`, … Numbering restarts at R1 there, replacing the old `D:\Claude\R<n>` scheme.
- **No reels now.** Raw clips will come with each future reel.

## Why Hugging Face
faster-whisper is the speech-to-text step. It downloads its model (Whisper medium, about 1.5 GB) from Hugging Face; that's the only place it's published. It's a download only: nothing of yours is sent there. Whisper gives word-level timestamps, which drive:
- cutting pauses, stutters and retakes (plan_cut / tr_base),
- syncing every caption word, keyword, stat and graph to when you say it,
- the effects skill's "on the word X" timing (`words.py`).
