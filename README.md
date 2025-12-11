# MMAI

Pre-trained models for VCMI's combat AI powered by machine learning.

<img src="screenshots/screenshot-01.png" alt="components" height="300px">

## Mod release workflow

[This](https://github.com/vcmi-mods/mmai/actions/workflows/create-release.yml)
GHA workflow should be used for mod releases. It will:

1. Parse `models/sources.json`, download the
  models (provided by
  [vcmi-gym](https://github.com/smanolloff/vcmi-gym)) and update
  `config/settings.json`
  
1. Create a release tagged `vcmi-VCMIVER-latest`, where `VCMIVER` is the
  compatibility version extracted from mod.json.
1. Upload a `mod.zip` release asset to be downloaded by VCMI's mod manager.

If another release with this tag already exists, it is re-tagged as
`vcmi-VCMIVER-TIMESTAMP` so the new mod becomes downloadable via the old
URL.

### Examples

#### 1. Mod release for a new VCMI major/minor version

A new VCMI version `1.8.0` is released and mod compatibility must be updated accordingly:
1. Create new branch `vcmi-1.8`
1. Update `mmai/mod.json` with min compatibility version = `1.8.0`
1. Run the [workflow](https://github.com/vcmi-mods/mmai/actions/workflows/create-release.yml) for branch = `vcmi-1.8`

Release `vcmi-1.8-latest` will appear shortly.

#### 2. Mod release for a new VCMI patch version

A new VCMI version `1.8.1` is released and mod compatibility must be updated accordingly:
1. Update `mmai/mod.json` with min compatibility version = `1.8.1`
1. Run the [workflow](https://github.com/vcmi-mods/mmai/actions/workflows/create-release.yml) for branch = `vcmi-1.8`

Release `vcmi-1.8-latest` will appear shortly. The previous release with the same name is renamed to `vcmi-1.8-TIMESTAMP`
where TIESTAMP is the current time in `YYYYMMDD` format
