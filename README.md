# local_manifests
Pixel 6a custom manifest for my unofficial Evolution X build.

### Sync ###

```bash
# Initialize local repository
repo init -u https://github.com/Evolution-X/manifest -b tiramisu

# Clone my custom manifest
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

If you got something went wrong, try replace this repos below:

```bash

# Go to root of your source
croot

# Avoid hardware source code error
rm -rf hardware/google/pixel && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_google_pixel hardware/google/pixel
rm -rf hardware/google/gchips && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_google_gchips hardware/google/gchips
rm -rf hardware/google/graphics/common && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_google_graphics_common hardware/google/graphics/common
rm -rf hardware/qcom/sm7250/display && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_qcom_sm7250_display hardware/qcom/sm7250/display
rm -rf hardware/qcom/sm7250/media && git clone -b lineage-20.0 https://github.com/LineageOS/android_hardware_qcom_sm7250_media hardware/qcom/sm7250/media

# Avoid neuralnetworks bug
rm -rf external/armnn && git clone -b topaz https://github.com/AOSPA/android_external_armnn external/armnn
rm -rf external/android-nn-driver && git clone -b topaz https://github.com/AOSPA/android_external_android-nn-driver external/android-nn-driver

```
and pick these commits for necessary:

Avoid ninja error of Google Camera: 
https://github.com/nattolecats/vendor_gms/commit/38a6d64ef03b72bb6c3571a4d67f9a651c152014

Avoid compile error: no matching constructor for initialization of 'aidl::android::hardware::power::stats::AocStateResidencyDataProvider'
https://github.com/AOSPA/android_device_google_gs101/commit/a40e7ad35d3199cafcc97a96f4671c4060bdefc1

for SafetyNet:
https://github.com/nattolecats/frameworks_base/commit/b1e97799758c60485a3beb899278c0e7fefe4b96
