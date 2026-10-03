# Content Pipeline

The production system behind an Instagram content operation: a royalty-free
audio library organized by taste lanes, a systems registry that links every
episode to its repos with zero recall, and (coming) the post scheduler.

Built by Nate Hogsten (nlhogsten) with his Muse agent, Oct 2026. Part of the
[Muse-usable systems](https://github.com/nlhogsten/art-engine) ecosystem —
each repo is a skill other Muse agents can use, not just read.

## What's here

- **`registry.yaml`** — the canonical map of systems → repo URLs → credit
  lines. Pipeline cards carry `systems:` / `terms:` / `inspired_by:` fields;
  the Review stage renders caption reference blocks straight from this file.
  Add new systems here first; everything downstream follows.
- **`audio/manifest.json`** — 13 license-verified royalty-free tracks across 5
  taste lanes (dreamy-digicore, dusty-lofi, wonky-bass, jersey-bounce,
  deep-japanese-house), each with mood tags, BPM estimates, source URL,
  license, and a ready-to-paste attribution string. Full tracks + 25s reel cuts.
- **Audio files** stay local (VM), not in git — the manifest is the portable part.

## The audio model

Three sources, each doing what it's legal for:

1. **Spotify** = taste intelligence. The deep-dive analysis defines the lanes;
   it never provides audio.
2. **Royalty-free / CC** = the actual audio. Ingested with the yt-dlp engine
   (lineage: [Musik-Getter](https://github.com/nlhogsten/Musik-Getter),
   Nate's original Mar 2026 downloader). Every track's license verified before
   it enters the library.
3. **Your own mixes** = the future. Original audio, zero licensing questions.

Copyright guardrail: the pipeline ingests royalty-free/CC sources only.
No ripped commercial tracks — Instagram's audio detection would mute them
and poison the operation.

## Requirements

- python3, ffmpeg, yt-dlp (for ingestion)

## License

MIT — Nate Hogsten, 2026.
