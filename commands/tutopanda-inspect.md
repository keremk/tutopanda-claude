---
description: Inspect prompts, artefacts, and timelines for an existing Tutopanda movie.
---

# Inspect a Tutopanda run

Use this to debug or export metadata for a generated documentary.

## Command

```bash
tutopanda inspect \
  --movieId=<movie-id> \
  --prompts \
  --all
```

Guidance:
- `--movieId` is required. Normalize to the storage id the CLI expects (e.g., `q123456`).
- `--prompts` dumps prompt/response pairs; drop it if you only want artefact paths.
- `--all` includes the entire manifest; omit if you only need specific sections.
- If you edited friendly files, run `tutopanda edit` before inspecting to align the manifest with disk.
