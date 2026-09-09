# mltfex_firmware

Compiled MLTFEX keypad firmware, for the companion configurator's update check.
Storage only — not a build or flashing guide.

- `manifest.json` — the file the configurator fetches on connect. Source of truth
  for the current version per model. Keyed by model key `<family>-<rows>row[-rh]`.
- `<model-key>.uf2` — the latest build for that model, committed directly and
  overwritten each release. Old versions live in git history.

## Releasing a new build

1. Build the firmware (see the private `umbra_fw` / `penumbra_fw` repos).
2. Copy the `.uf2` here as `<model-key>.uf2`, overwriting the old one.
3. In `manifest.json`, bump `fwVersion` (always) and `protocol` (only on a
   breaking wire change), update `sha256` (`sha256sum <file>`), `notes`, `date`.
4. Commit and push to `main`.
