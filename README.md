# Tutopanda Claude Code plugin

This plugin exposes Tutopanda's CLI and MCP server to Claude Code so you can ask Claude to generate, edit, and preview documentary-style videos end to end.

## Components
- `.claude-plugin/plugin.json`: plugin manifest (name `tutopanda-movie-producer`).
- `.mcp.json`: registers the Tutopanda MCP server (`tutopanda mcp --defaultBlueprint=video-audio-music.yaml --openViewer=false`).
- `commands/`: guided slash commands for setup, generation, editing, inspection, and viewer control.
- `skills/documentary-producer/`: model-invoked skill that teaches Claude how to drive the CLI safely.

## Prerequisites
- `tutopanda` CLI available on `PATH` (install from npm/registry as documented in `cli/readme.md`).
- Run `tutopanda init --rootFolder=<absolute-path>` once to seed blueprints and config (`~/.tutopanda/cli-config.json` by default).
- If you keep the config elsewhere, export `TUTOPANDA_CLI_CONFIG` in your shell before starting Claude Code so the MCP server picks it up.

## Using the plugin locally
1. From Claude Code, install the plugin from this directory (or add it to a local marketplace that points at `claude-plugin/`).
2. Use the `tutopanda-setup` command first to verify the CLI binary and configuration.
3. Use `tutopanda-generate` to run the `video-audio-music.yaml` blueprint and produce an MP4. Follow up with `tutopanda-viewer` to preview and `tutopanda-edit` to iterate.

The plugin does **not** install Tutopanda for you; keep the CLI up to date separately so commands and the MCP server remain available.

## Validation
- After installing the plugin, run `/help` (commands) and `/skills` (skills) in Claude Code to confirm the entries are registered.
- Run `/plugin` → Manage Plugins to verify the MCP server `tutopanda` is loaded; `claude --debug` will also show the MCP bootstrap logs.
- Smoke test with `tutopanda blueprints:list` to confirm the CLI sees your configured root and blueprints.

## Distribution note
The plugin intentionally avoids bundling or auto-installing the `tutopanda` binary because plugin installs should not run package managers on a user’s machine. Ship the CLI through your normal channel (npm `tutopanda` package) and ask users to install/update it before enabling the plugin.
