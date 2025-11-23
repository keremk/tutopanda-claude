---
description: Run Tutopanda query with the video-audio-music blueprint to produce a narrated documentary and exported MP4.
---

# Generate documentary video

Drive the full pipeline that writes narration, video clips, music, a Remotion timeline, and a final MP4 export.

## Inputs to collect (ask the user; do not invent defaults)
- `InquiryPrompt` (what the documentary covers)
- `Duration` (total seconds)
- `NumOfSegments` and optional `SegmentDuration`
- `VideoStyle`, `AspectRatio`, `Resolution`
- `VoiceId` and optional `Emotion`
- `Audience`, `Language`
- `MusicalStyle` for the score

Store them in an inputs YAML on disk (absolute path). Example structure:

```yaml
inputs:
  InquiryPrompt: "<prompt>"
  Duration: 90
  NumOfSegments: 5
  SegmentDuration: 18
  VideoStyle: "Cinematic"
  AspectRatio: "16:9"
  Resolution: "1080p"
  VoiceId: "Wise_Woman"
  Audience: "Adult"
  Language: "en"
  Emotion: "neutral"
  MusicalStyle: "Cinematic orchestral score"
```

## Command
Run from a shell inside the project or any directory (config path is read from `TUTOPANDA_CLI_CONFIG` or the default install location):

```bash
tutopanda query "<InquiryPrompt>" \
  --inputs=/absolute/path/to/inputs.yaml \
  --usingBlueprint=video-audio-music.yaml \
  --concurrency=<workers-if-needed> \
  --nonInteractive
```

## Outputs and follow-ups
- Capture the `movieId`, plan path, and friendly view path printed by the CLI.
- Final MP4 (`FinalVideo`) and artefacts are stored under the configured Tutopanda root for that movie id.
- Use the `tutopanda-viewer` command to preview the run and confirm audio/video sync.
