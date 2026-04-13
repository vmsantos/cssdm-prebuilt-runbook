# Remote deploy notes

## What was done

The remote Oracle Cloud CS:S server was not reinstalled from scratch. The existing LinuxGSM install was kept, the old addon tree was cleared, and the working prebuilt WSL tree was copied into the live serverfiles path.

## Working assumptions

- The server user is `cssserver`
- LinuxGSM lives in `/home/cssserver`
- Game files live in `/home/cssserver/serverfiles/cstrike`

## Deployment flow

1. Stop the server process.
2. Replace the `addons` tree with the known-good prebuilt tree.
3. Copy the CSSDM config under `cfg/cssdm`.
4. Restart `srcds_run`.
5. Confirm:
   - `meta list`
   - SourceMod log session starts
   - CSSDM plugin loads

## Why it worked

The key fix was using a clean prebuilt layout with the documented VDF paths:

- `cstrike/addons/metamod.vdf`
- `cstrike/addons/metamod/sourcemod.vdf`

That removed the path/layout mismatch that had been causing the loader problems.
