# CS:S CSSDM prebuilt runbook

This repository captures the working deployment path for the Counter-Strike: Source Deathmatch stack we validated in WSL and then applied to the remote LinuxGSM server.

## What this repo is for

- The exact loader layout that worked
- The repeatable WSL test-server steps
- The remote deployment flow
- A manifest for the generated release zip

## Important note

We did not make meaningful source-code changes to CSSDM itself. The work that succeeded was a clean prebuilt stack plus correct loader/config layout, so a PR against the CSSDM source repo would not add much value.

## Working loader layout

- `cstrike/addons/metamod.vdf`
- `cstrike/addons/metamod/sourcemod.vdf`

## Release artifact

- `release/cssdm-wsl-release.zip`
- SHA256: `BE243B996FCED919D4A9FA90D8ADB80247C602AD8978D7C6CE88527C3A521422`

## Contents

- `docs/WSL-RUNBOOK.md`
- `docs/REMOTE-DEPLOY.md`
- `release/manifest.txt`

