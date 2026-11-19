# Changelog

All notable changes to gta6-clipper. Newest first.

## 1.0.7
### Added
- OpenCode as an AI tool (Settings > AI tool). The install and setup sentences also work inside OpenCode, on its free models.
- Clip rules: each streamer shows Clipping allowed, Has clip tips, No clipping or Rules unknown, with the source. Live hunt and Make Shorts stop on "No clipping" unless you confirm you have permission. The list updates with the app.
### Testing
- OpenCode 1.19.6 on Windows, free model: install 80 s, setup 3.5 min, app AI test OK.

## 1.0.6
### Added
- Past streams: every streamer has a "Past streams" list (last 5 ended streams on Twitch, Kick and YouTube) with a "Make Shorts" button.
- "Paste a link" accepts a live stream, a past stream (VOD) or any video.
### Fixed
- Live hunts keep running and stay visible after the app restarts.
- "1 clip found" instead of "1 clips found", in all 8 languages.

## 1.0.5
### Added
- README with screenshots, a live-hunt gallery and an install-in-one-sentence section.
- Live hunt can watch up to 8 streams at once (Twitch, YouTube, Kick); each chat spike is rendered into a finished Short.
### Changed
- Spacing between blocks is applied globally, so cards no longer touch their buttons.

## 1.0.4
### Fixed
- Live clips that were mostly gameplay without speech are now kept whole instead of being cut to about one second.
- Live spikes are rendered into the same Library as the batch Shorts, one at a time.
### Changed
- Maximum Short length raised from 32 s to 60 s, because viral moments run 6 to 61 s.

## 1.0.3
### Changed
- AI cost labels now show a measured range as a share of a Claude Pro session (Smart about 8-25%, Deep about 30-90% per 10 Shorts) instead of a flat estimate.

## 1.0.2
### Added
- "Connect Blotato" dialog with four steps and the official Blotato MCP command.
### Changed
- The Blotato card is separated from the buttons below it; the side-menu Auto-post button opens the dialog.

## 1.0.1
### Added
- Visible Blotato auto-post card on Home, an Auto-post button in the side menu and a banner on the Approved page.
### Changed
- Moments are anchored on the chat spike and start with their setup; windows up to 60 s are allowed.

## 1.0.0
### Added
- Skill that finds GTA 6 videos and streams, transcribes on your PC, picks the best moments and renders finished 9:16 Shorts with face-tracked framing, word captions, hook title, cover and post text.
- Local web app: Home, Shorts by day, one-at-a-time review (approve or reject), Approved, scheduling, streamers, brand and settings.
- Live hunt: records a stream, watches chat speed and loudness and cuts a Short on a spike.
- Pick modes Free, Smart and Deep; Ask the AI to change a Short in plain words.
- Updates every 5 hours that keep your workspace, brand and clips.
