# Ocarina of TIme Randomizer for Flatpak
This repository contains the manifests required to build the Ocarina of Time 
Randomizer on the Flatpak platform.

## Preparing a Release
These steps will ensure a release can be packaged into a Flatpak.

### Prerequisites
- [Install flatpak-node-generator from PyPI](https://pypi.org/project/flatpak-node-generator/) using `pip`
  - `pip install --user flatpak-node-generator`

### Update the release
To update the Flatpak, the release version of OoT-Randomizer needs to have an updated `package-lock.json` that matches `packages_release.json`, a tag on the commit with the updated package-lock.json, and a commit hash for that tagged version.

Push these changes to the main OoT-Randomizer repository.

### Generate a list of npm sources
Pull down the tagged release and run flatpak-node-generator on the package-lock.json file.
`flatpak-node-generator npm <path/to/OoT-Randomizer>/GUI/package-lock.json`
Do not commit or push the resulting `generated-sources.json` file to the main repository.

### Update the manifest and generated sources
`com.ootrandomizer.electrongui.yml` needs the `tag` and `commit` properties in the git source at the end of the file to be updated to match the release version. You must also replace the existing `generated-sources.json` with the newly generated one.

Push these changes to the Flatpak repository.
