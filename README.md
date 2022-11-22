# local_manifests
Manifest for Pixel 6a on my unofficial Evolution X build.

### Sync ###

```bash
# Initialize local repository
repo init -u https://github.com/Evolution-X/manifest -b tiramisu

# Clone my manifest
git clone -b tiramisu https://github.com/nattolecats/local_manifests .repo/local_manifests

# Sync
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags

```

### Build ###

```bash

# Set up environment
$ . build/envsetup.sh

# Choose a target
$ lunch evolution_bluejay-userdebug

# Build the code
$ m evolution
```
