---
description: Re-run a Tutopanda movie with updated inputs or blueprint settings.
---

# Edit a Tutopanda movie

Use this to regenerate artefacts after tweaking inputs or friendly edits.

## Prerequisites
- Tutopanda CLI is initialized and the `movieId` already exists in storage.
- The updated inputs YAML is on disk (explicit path). Do not assume the implicit `inputs.yaml`; confirm the exact file with the user.

## Command

```bash
tutopanda edit \
  --movieId=<existing-movie-id> \
  --inputs=/absolute/path/to/inputs.yaml \
  --usingBlueprint=video-audio-music.yaml \
  --concurrency=<workers-if-needed> \
  --nonInteractive
```

Options:
- Add `--dryRun` to see pending work without writing artefacts.
- Use `--upToLayer=<n>` when you only want to rebuild up to a specific layer.

## After the edit
- Capture the refreshed friendly view path printed by the CLI.
- If the run succeeded, use `tutopanda-viewer` to spot-check the new MP4 or timeline.
