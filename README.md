# EPA Haweya — public release channel

This repository hosts **version metadata** and **Windows installers** for the EPA Haweya desktop app.

The application source code lives in a separate private repository.

## Layout

```
updater/
  version.json    ← read by the app at startup (Windows)
```

Installers are attached to [GitHub Releases](https://github.com/ALRASHIDI-D/epa-haweya-releases/releases), not committed to this tree.

## `version.json` fields

| Field | Description |
|-------|-------------|
| `latest_version` | Newest published semver (optional update if app is older) |
| `min_required_version` | Minimum semver allowed to run (force update if app is older) |
| `download_url` | Direct GitHub Release asset URL for the installer |
| `release_notes` | Shown in the update dialog |

## Publishing a release

1. Build the installer from the private app repo (`flutter build windows` + Inno Setup).
2. On GitHub: **Releases → Create a new release**.
3. Tag: `v1.1.0` (must match the version you ship).
4. Upload the installer (e.g. `setup.exe`).
5. Copy the asset download link into `updater/version.json` → `download_url`.
6. Update `latest_version` / `min_required_version` / `release_notes`.
7. Commit and push `version.json` to `main`.

Example `download_url`:

`https://github.com/ALRASHIDI-D/epa-haweya-releases/releases/download/v1.1.0/setup.exe`

## Verify

Open in a browser (no login required for a public repo):

https://raw.githubusercontent.com/ALRASHIDI-D/epa-haweya-releases/main/updater/version.json
