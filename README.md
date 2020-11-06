Device configuration for Sony Xperia XZ1 Canada variant (poplar_canada)
========================================================

Description
-----------

This repository is for AOSPA ruby on Sony Xperia XZ1 Canada variant (poplar_canada).

How to build AOSPA ruby
----------------------

* Make a workspace:

        mkdir -p ~/aospa
        cd ~/aospa

* Initialize the repo:

        repo init -u https://github.com/AOSPA/manifest -b ruby

* Create a local manifest:

        cd .repo & mkdir local_manifests
        cd local_manifests & nano roomservice.xml
        
<?xml version="1.0" encoding="UTF-8"?>
        <manifest>
                <!-- SONY -->
        <project name="T3RY4/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="aospa-ruby" />
        <project name="T3RY4/android_device_sony_yoshino-common" path="device/sony/yoshino-common" remote="github" revision="aospa-ruby" />
        <project name="T3RY4/android_device_sony_poplar_canada" path="device/sony/poplar_canada" remote="github" revision="aospa-ruby" />
                <!-- Pinned blobs for poplar_canada -->
        <project name="T3RY4/android_vendor_sony_poplar_canada" path="vendor/sony/poplar_canada" remote="github" revision="aospa-ruby" />
        </manifest>

* Sync the repo:

        repo sync -f --force-sync --no-clone-bundle

* Extract vendor blobs

        cd device/sony/poplar_dsds
        ./extract-files.sh ~/path/to/blobs

* Setup the environment

        source build/envsetup.sh
        lunch aospa_poplar_canada-userdebug

* Build AOSPA ruby

        # Go to the root of the source tree...
        $ cd ~/aospa
        # ...and run the builder tool.
        $ ./rom-build.sh poplar_canada
