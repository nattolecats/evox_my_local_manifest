# local_manifests
local_manifest for my unofficial Evolution X build.

# Bring up a build

$ repo init -u https://github.com/Evolution-X/manifest -b tiramisu

$ git clone -b tiramisu https://github.com/nattolecats/local_manifests .repo/local_manifests

$ repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags

$ . build/envsetup.sh

$ lunch evolution_bluejay-userdebug

$ mka evolution
