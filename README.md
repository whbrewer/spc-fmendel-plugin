# fmendel-spc

Consolidated package repo for the Mendel SPC app. Shared templates/assets live here, while platform-specific binaries are packaged into release zips.

## Repo Layout

- `app/` – shared app assets (`spc.json`, `mendel.j2`, `mendel.js`, `help.html`, `about.html`, `mendel.in`).
- `bin/linux-x86_64/` – Linux x86_64 `mendel` binary.
- `bin/darwin-x86_64/` – macOS x86_64 `mendel` binary.
- `scripts/package.sh` – builds platform-specific zip artifacts.
- `dist/` – generated release zips (not tracked).

## Build Release Zips

```bash
./scripts/package.sh
```

This writes:

- `dist/fmendel-spc-linux-x86_64.zip`
- `dist/fmendel-spc-darwin-x86_64.zip`

Each zip has the exact layout SPC expects (root contains `spc.json`, `mendel`, and assets).

## Install in SPC

Use the release asset URL that matches your platform:

```bash
./spc install https://github.com/whbrewer/spc-fmendel-plugin/releases/download/v2.0.1/fmendel-spc-linux-x86_64.zip
```

```bash
./spc install https://github.com/whbrewer/spc-fmendel-plugin/releases/download/v2.0.1/fmendel-spc-darwin-x86_64.zip
```

## Notes

- Add more platforms by dropping a binary in `bin/<platform>/mendel` and extending `scripts/package.sh`.
- The `command` in `app/spc.json` remains `<rel_apps_path>/mendel/mendel` so the packaged binary must be named `mendel` at the zip root.
