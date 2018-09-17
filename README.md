<img src="https://github.com/AOSP-Legacy-MSM8916/platform_manifest/raw/pie-r1/pie-logo.png">

The Android Open Source Project 9.0 for MSM8916
====================
By TeamLegacy
----------

Create the source directory
---------------------------

    mkdir ~/aosp
    cd ~/aosp
    

Configure git (nickname, e-mail)
-------------------------------------

    git config --global user.email "mail@domain.com"
    git config --global user.name "login"
    

To initialize your local repository use
---------------------------------------

    repo init -u https://github.com/AOSP-Legacy-MSM8916/platform_manifest -b android-9.0.0
    

Then to sync up:
----------------

    repo sync -f -c --no-clone-bundle build/make
    . build/envsetup.sh
    repofastsync

Build instructions:
----------------
    export JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4000m"
    export USE_CCACHE=1
    . build/envsetup.sh
    lunch aosp_$device-userdebug
    mka otapackage

Device configuration instructions:
----------------
- Add a bunch of board flags:
```
BOARD_USES_ADRENO := true
QCOM_HARDWARE_VARIANT := msm8916                # MSM8916 devices only
TARGET_USES_QCOM_BSP := true
TARGET_COMPILE_WITH_MSM_KERNEL := true          # If building kernel inline
TARGET_USES_QCOM_MM_AUDIO := true               # If using CAF audio HAL
```
- Add your own apns-conf.xml and copy it, like this:
```
# APN
PRODUCT_COPY_FILES += $(LOCAL_PATH)/configs/apns-conf.xml:system/etc/apns-conf.xml
```
- We don't have project paths like LineageOS so you need to define QCOM HAL variants in your device's BoardConfig.mk; instructions mentioned below.

- To use CAF HALs, add these board flags:
```
TARGET_QCOM_AUDIO_VARIANT := caf-msm8916        # MSM8916 devices only
TARGET_QCOM_DISPLAY_VARIANT := caf-msm8916      # MSM8916 devices only
TARGET_QCOM_MEDIA_VARIANT := caf-msm8916        # MSM8916 devices only
TARGET_QCOM_BLUETOOTH_VARIANT := bt-caf
TARGET_QCOM_WLAN_VARIANT := wlan-caf
TARGET_RIL_VARIANT := caf
```

- Our device sources are available on the device maintainer's github account

Buildbots can stay away and butt other "AOSP-based" or "Lineage-based" ROMs. We're better off without them.
