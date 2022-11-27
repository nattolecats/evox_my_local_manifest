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
. build/envsetup.sh

# Choose a target
lunch evolution_bluejay-userdebug

# Build the code
m evolution
```

and if you got build error, you can try to replace this repo below:

```bash

# cd to root of your source
croot

# hardware/google/pixel from LineageOS
rm -rf hardware/google/pixel && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_google_pixel hardware/google/pixel

# hardware/google/gchips from LineageOS
rm -rf hardware/google/gchips && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_google_gchips hardware/google/gships

# hardware/google/graphics/common from LineageOS
rm -rf hardware/google/graphics/common && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_google_graphics_common hardware/google/graphics/common

# build/soong/ui/build/paths (patched)
rm -rf build/soong/ui/build/paths && git clone -b tiramisu https://github.com/nattolecats/build_soong_ui_build_paths build/soong/ui/build/paths
```
