# Reusable clipping assets

Free to use in your Shorts. Drop them in as watermarks or overlays.

## logos/

Official platform logos from [simple-icons](https://simpleicons.org) (CC0, public domain). Each logo comes as SVG (vector) and a 512 px PNG on transparency.

- youtube, twitch, kick, tiktok, instagram, x

Use one as your clip watermark in `brand.json`:

```json
"watermark": "assets/logos/twitch.png"
```

Twitch, Kick and X are solid black on transparency: recolor or put them on a light background. YouTube red, TikTok and Instagram ship in brand colors.

The official GTA VI wordmark is trademarked and has no clean free source, so it is NOT bundled. If you have the rights, drop your own copy in this folder as `gta6.png` and use it the same way.

## overlays/

Transparent PNGs generated for this repo (free for any use, no attribution):

- live_badge.png - red LIVE badge for live-hunt clips
- rec_indicator.png - REC dot for raw/stream feel
- subscribe_pill.png - YouTube subscribe pill (YouTube cuts)
- follow_pill.png - follow pill (Instagram/Threads cuts)
- lower_third_bar.png - 1080 px bar to sit a streamer credit line on
- new_corner_tag.png - yellow NEW corner tag

Overlay them with clip.py's picture-in-picture options or in the app's Look tab; see SKILL-REFERENCE.md ("extras").
