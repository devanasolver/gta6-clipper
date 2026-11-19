<h1 align="center">gta6-clipper</h1>

<p align="center">
  <b>Type one sentence in Claude Code. Get finished 9:16 GTA 6 Shorts from live streams and videos.</b><br>
  It finds the loud, chat-heavy moments, frames the streamer and the game, adds word-by-word captions and a hook, and waits for your approval.
</p>

<!-- TODO: put the video URL in the first link below when the video is published -->
<p align="center"><b><a href="#how-it-works">▶ Watch how it works (video soon)</a></b> &nbsp;·&nbsp; <b><a href="https://github.com/devanasolver/gta6-clipper">Free download</a></b></p>




---

## Install (works with any AI agent)

Any coding agent that can read a skill folder can run this: Claude Code, Codex, Gemini CLI, Cursor, OpenCode, Antigravity and others. The agent reads `SKILL.md` and does the work.

Clone the repo into your agent's skills folder (or any folder you run your agent in):

```
git clone https://github.com/devanasolver/gta6-clipper
```

then tell your agent:

```
Set up the gta6-clipper skill on this PC
```

Setup takes about 3 minutes. Skill folders per agent: Claude Code `~/.claude/skills/gta6-clipper`, OpenCode `~/.config/opencode/skills/gta6-clipper`; other agents: keep the folder anywhere and open your agent in it. If it finds an NVIDIA graphics card it also downloads about 2 GB of GPU packages (an optional speed-up; without a card it uses the CPU and nothing else changes).

**No paid AI plan?** In the app, choose **Settings > AI tool**: OpenCode runs on free models with no account, Ollama runs fully local, and **No AI** still makes Shorts, cut on chat and loudness spikes. Free models pick weaker moments than paid ones, so review before you post.

<details>
<summary>Install by hand (Windows, macOS, Linux)</summary>

Download the zip from https://github.com/devanasolver/gta6-clipper (or `git clone` it) into your agent's skills folder (or any folder you run your agent in), then:

#### Install (Windows, macOS, Linux; Python 3.9 to 3.12)

Open a terminal in the skill folder, then:

| Step | Windows (PowerShell) | macOS (Terminal) | Linux (Debian/Ubuntu) |
|---|---|---|---|
| ffmpeg + ffprobe | `winget install Gyan.FFmpeg` | `brew install ffmpeg` | `sudo apt install ffmpeg` |
| Python venv | `py -3.12 -m venv .venv` | `python3 -m venv .venv` | `python3 -m venv .venv` (`sudo apt install python3-venv`) |
| Activate | `.venv\Scripts\activate` | `source .venv/bin/activate` | `source .venv/bin/activate` |
| Libraries (includes yt-dlp + deno) | `pip install -r requirements.txt` | same | same |

- Open a NEW terminal after installing ffmpeg. Check: `ffmpeg -version`, `python -m yt_dlp --version`. Every script stops with the install line above if ffmpeg is missing.
- GPU is optional. Windows/Linux with an NVIDIA card: `pip install -r requirements-gpu.txt` (Windows is wired in; on Linux also `export LD_LIBRARY_PATH=$(python -c "import nvidia.cublas.lib,nvidia.cudnn.lib,os;print(os.path.dirname(nvidia.cublas.lib.__file__)+':'+os.path.dirname(nvidia.cudnn.lib.__file__))")`). Mac (Intel or Apple Silicon) and no-GPU PCs: nothing to do, transcription falls back to CPU int8 on its own (model "base").
- Colour emoji in captions need Segoe UI Emoji (Windows), Apple Color Emoji (Mac) or `sudo apt install fonts-noto-color-emoji` (Linux); without it the emoji style is skipped, nothing breaks. Caption fonts ship in `fonts/`.
- Scheduled runs (Autopilot tab, always shown as a dry preview first): Windows = Task Scheduler (`schtasks`), macOS = launchd agent `~/Library/LaunchAgents/io.clipper.autopilot.plist` (`launchctl load -w`), Linux = a `crontab` line tagged `# clipper-autopilot` (a systemd user timer preview is shown too). Turn off = the "off" command in the same preview. The computer must be on and logged in at that time.
- Always run with `python` from the venv (the skill calls `sys.executable`, never a hard-coded path).


</details>

## How it works

<img src="docs/img/how.png" alt="How it works: find, transcribe, pick, render, review, post" width="100%">

1. **You type one line.** `make 10 GTA 6 Shorts`, or `clip kaicenat live`, or paste a YouTube, Twitch or Kick link.
2. **It finds and transcribes.** New GTA 6 videos or a live stream, transcribed on your own PC for free.
3. **It picks the moments.** Loudness, chat speed and keywords score every window. Optionally an AI reads a shortlist and widens the good ones.
4. **It renders.** 9:16, face-tracked cam on top, game below, word-by-word captions, a hook title, a cover and ready-to-paste post text.
5. **You review.** One Short at a time: approve or reject. Nothing is ever posted without you.
6. **You post.** Copy the text, schedule it in the app, or connect any posting tool you like.

Want a change? Open a Short and say it in plain words: *"end 2 s earlier"*, *"bigger captions"*, *"new hook"*. The original is kept.

## The app


Start it any time with `python app.py <your workspace folder>` (it opens http://localhost:8765).

<table>
<tr>
<td width="50%"><img src="docs/img/home.png" alt="Home"><br><b>Home.</b> What needs review, what is approved, what the live hunt is watching.</td>
<td width="50%"><img src="docs/img/shorts.png" alt="Shorts by day"><br><b>Shorts by day.</b> Every Short with a quality check (pass, warn, fail) and filters.</td>
</tr>
<tr>
<td><img src="docs/img/review.png" alt="Review"><br><b>Review.</b> One Short at a time. A approves, X rejects, arrows move on.</td>
<td><img src="docs/img/one-short.png" alt="One Short with Ask the AI"><br><b>One Short.</b> Ask the AI to change it in plain words. The original is kept.</td>
</tr>
<tr>
<td><img src="docs/img/one-short-look.png" alt="Look tab"><br><b>Look tab.</b> Formats, layouts, caption themes, meme sounds, extra aspect ratios.</td>
<td><img src="docs/img/streamers.png" alt="Streamers and live hunt"><br><b>Streamers.</b> Add a Twitch, YouTube or Kick link or a name; tick "Watch live".</td>
</tr>
<tr>
<td colspan="2"><img src="docs/img/past-streams.png" alt="Past streams"><br><b>Past streams.</b> Missed the live? Open a streamer's last 5 streams (Twitch, Kick, YouTube) and click <b>Make Shorts</b>. Or paste any stream or VOD link.</td>
</tr>
<tr>
<td colspan="2"><img src="docs/img/clip-rules.png" alt="Clip rules per streamer"><br><b>Clip rules.</b> Each streamer gets a badge: <b>Clipping allowed</b>, <b>Has clip tips</b>, <b>No clipping</b> or <b>Rules unknown</b>. Click it to see the source. The app will not clip a streamer who said no unless you confirm you have their permission.</td>
</tr>
<tr>
<td colspan="2"><img src="docs/img/opencode.png" alt="OpenCode in Settings"><br><b>Any AI tool.</b> Claude Code, Codex, Gemini, Kimi, <b>OpenCode</b> (works on its free models), Ollama, your own command, or No AI.</td>
</tr>
<tr>
<td><img src="docs/img/schedule.png" alt="Schedule"><br><b>Schedule.</b> Drag Shorts onto the week, or spread them automatically. Preview first.</td>
<td><img src="docs/img/settings.png" alt="Settings"><br><b>Settings.</b> Language, updates, and how much AI to use.</td>
</tr>
</table>

## Live hunt: 8 GTA 6 streams at once

Tick "Watch live" on a streamer and the app records the stream, watches chat speed and loudness, and cuts a Short the moment chat spikes. 
- **Spike detection:** a chat spike is a few times the stream's own baseline, so a quiet streamer and a huge one are judged fairly.
- **Setup first:** the Short starts 17-20 s before the spike so the viewer sees what caused it.
- **Up to 60 s,** because real viral moments run 6 to 61 s.
- **Credit built in:** every Short carries a credit line to the streamer in its post text.


## What you can type

| Prompt | What happens |
|---|---|
| `make 10 GTA 6 Shorts` | Finds the newest GTA 6 videos, picks the best moments and renders up to 10 Shorts |
| `make Shorts from <link>` | Same, from one YouTube, Twitch or Kick video |
| `clip <streamer> live` | Records the stream and cuts a Short on every chat spike |
| `add my voice to this clip` | Adds your own voice-over to a finished Short |
| `open the clipper app` | Opens the web app with all your Shorts |

## How much AI

Transcription, framing, captions and rendering run on your PC for free. Only the choice of moments can use AI. Measured on a real run (usage is a share of one Claude Pro session):

| Mode | What picks the moments | Cost per 10 Shorts |
|---|---|---|
| Free | Loudness, chat and keyword scoring. Weakest picks | 0 |
| Smart (default) | AI reads a shortlist of the 30 best windows and may widen them | about 8-25% of a Claude Pro session |
| Deep | AI reads the full transcripts; catches quiet stories | about 30-90% of a Claude Pro session |
| Live spike (optional AI check) | AI looks at one chat spike | about 1-4% of a session |

Live hunt defaults to Free (no AI) with a cap on AI checks per hour. Your own agent plan (or free/local models) is the only thing used; no API keys are needed.

## Posting

The app builds your posting schedule: drag Shorts onto the week, spread them automatically, export the schedule as CSV. Posting itself is always your call: upload manually, or connect any scheduler you like. If you already use Blotato, the app can send approved Shorts through its API with your own key (Settings > Connections) - optional, paid third-party service. This fork contains no affiliate links, partner links or promo codes anywhere.

## Updates

The app checks for updates every 5 hours from this GitHub repo. "Update now" replaces only the app files and keeps your workspace, brand settings, keys and clips. See [CHANGELOG.md](CHANGELOG.md).

<img src="docs/img/updates.png" alt="Updates in Settings" width="480">

## Propose a change

Use the "Propose a change" button in the app, or open an issue: https://github.com/devanasolver/gta6-clipper/issues/new. Every idea is read.

## What it does not do yet

- It does not know what will go viral. It finds loud, chat-heavy moments and ranks them; you decide what to approve.
- It does not post by itself unless you connect Blotato and approve the schedule.
- Live hunt on a weak PC is limited to a few streams at once; recording 8 needs a strong machine and a good connection.
- Some Shorts fail the built-in quality check (too short, no speech); the app marks them so you can skip or fix them.

## FAQ

**Is it free?** Yes. The tool is free and runs locally; the agent uses your own plan, free models or no AI at all. Blotato is an optional paid service.

**Who owns the clips?** The streamers do. Credit them and respect their rules; see [NOTICE.md](NOTICE.md).

**Does it work without an AI?** Yes, Free mode scores loudness, chat and keywords and renders automatically.

## License

MIT, see LICENSE. Bundled fonts keep their own OFL licenses (`fonts/`); models are listed in `models/NOTICES.txt`.

## Credits

Fork of [gta6-clipper](https://gitlab.com/nocodehack.io/gta6-clipper), originally built by NoCodeHack (MIT license; original copyright kept in LICENSE). This version removes all affiliate/partner links and works with any AI agent.

Maintained by **Anas**:

- [AiAffHub.com](https://aiaffhub.com) - AI startups x AI creators UGC marketplace
- [YouTube: Anas | Build Online](https://youtube.com/@anasstyb)
- [Facebook community](https://facebook.com/groups/685198062141316)

Uses ffmpeg, faster-whisper, yt-dlp, streamlink, OpenCV and MediaPipe. Streamers in the images are credited on the clips they appear in. Fan-made, not affiliated with Rockstar Games, Take-Two or any streamer.
