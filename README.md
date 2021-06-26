Device configuration for Sony Xperia XZ1 Compact (lilac)
========================================================

Description
-----------

This repository is for LineageOS 18.1 on Sony Xperia XZ1 Compact (lilac).

How to build LineageOS
----------------------

* Make a workspace:

    ```bash
    mkdir -p ~/lineageos
    cd ~/lineageos
    ```

* Initialize the repo:

    ```bash
    repo init -u git://github.com/LineageOS/android.git -b lineage-18.1
    ```

* Create a local manifest:

    ```bash
    mkdir .repo/local_manifests
    vim .repo/local_manifests/roomservice.xml

    <?xml version="1.0" encoding="UTF-8"?>
    <manifest>
        <!-- SONY -->
        <project name="Flamefire/android_kernel_sony_msm8998" path="kernel/sony/msm8998" remote="github" revision="lineage-18.1" />
        <project name="Flamefire/android_device_sony_yoshino-common" path="device/sony/yoshino-common" remote="github" revision="lineage-18.1" />
        <project name="Flamefire/android_device_sony_lilac" path="device/sony/lilac" remote="github" revision="lineage-18.1" />

        <!-- Pinned blobs for lilac -->
        <project name="Flamefire/android_vendor_sony_lilac" path="vendor/sony/lilac" remote="github" revision="lineage-18.1" />
    </manifest>
    ```

* Sync the repo:

    ```bash
    repo sync
    ```

* Extract vendor blobs

    ```bash
    cd device/sony/lilac
    ./extract-files.sh
    ```

* Setup the environment

    ```bash
    source build/envsetup.sh
    lunch lineage_lilac-userdebug
    ```

* Build LineageOS

    ```bash
    make -j8 bacon
    ```
