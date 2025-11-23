---
description: Start, open, and stop the Tutopanda viewer for generated movies.
---

# Tutopanda viewer control

Use this to preview timelines and exports in the bundled viewer.

## Commands
- Start the viewer in the foreground (useful for local dev):
  ```bash
  tutopanda viewer:start
  ```
- Open a specific movie (starts the viewer in the background if needed):
  ```bash
  tutopanda viewer:view --movieId=<movie-id>
  ```
- Stop the background viewer started by `viewer:view`:
  ```bash
  tutopanda viewer:stop
  ```

Tips:
- Use the same config path/root folder established during setup so the viewer resolves artefacts correctly.
- If the viewer is already running, avoid starting another instance; reuse the existing server and just call `viewer:view`.
