---
description: Verify Tutopanda CLI is installed and initialized before invoking any movie workflows.
---

# Tutopanda setup

Use this before other Tutopanda commands.

## Steps
- Check the binary: run `tutopanda --version` (or `tutopanda --help`) to confirm it is on PATH. If absent, ask the user to install the published CLI; do not install it automatically.
- Initialize storage once per machine with the user's chosen absolute path: `tutopanda init --rootFolder=<root>`. Confirm the config file was written (default is `~/.tutopanda/cli-config.json`).
- If the config lives outside the default path, export `TUTOPANDA_CLI_CONFIG` accordingly before continuing.
- Verify blueprints are reachable: `tutopanda blueprints:list` should succeed from the configured root.
- Capture the root folder and config path for later commands (query/edit/viewer) so subsequent steps use the same location.
