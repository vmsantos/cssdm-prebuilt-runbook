# CSSDM WSL runbook

## Working layout

- Server: `~/cssdm-test-server`
- Game folder: `~/cssdm-test-server/cstrike`
- MetaMod VDF: `cstrike/addons/metamod.vdf`
- SourceMod VDF: `cstrike/addons/metamod/sourcemod.vdf`

## Known-good loader files

`cstrike/addons/metamod.vdf`

```text
"Plugin"
{
    "file" "addons/metamod/bin/server"
}
```

`cstrike/addons/metamod/sourcemod.vdf`

```text
"Plugin"
{
    "file" "addons/sourcemod/bin/sourcemod_mm_i486"
}
```

## Start

```bash
cd ~/cssdm-test-server
nohup ./srcds_run -game cstrike -console -usercon -ip 0.0.0.0 -port 27015 +map cs_office +maxplayers 16 >/tmp/cssdm-local.log 2>&1 &
```

## Verify

```bash
tr -d '\000' < /tmp/cssdm-local.log | tail -n 120
```

Expected lines:

- `[META] Loaded 1 plugin.`
- `SourceMod log file session started`
- `dm_preset_spawns.smx` loaded

## Release contents

Include the working `cstrike/addons` tree and the CSSDM config under `cstrike/cfg/cssdm`.
