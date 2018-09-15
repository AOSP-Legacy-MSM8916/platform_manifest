<img src="https://github.com/AOSP-Legacy-MSM8916/platform_manifest/raw/pie-r1/pie-logo.png">

AOSP LEGACY MSM8916 Manifest FOR ANDROID 9.0.0 (PIE)
====================

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

    repo init -u https://github.com/AOSP-LEGACY-MSM8916/platform_manifest.git -b android-9.0.0
    

Then to sync up:
----------------

    repo sync -f -c --no-clone-bundle build/make
    . build/envsetup.sh
    reposync -f -c --no-tags --no-clone-bundle --optimized-fetch --force-sync --prune

Build commands are:
----------------
    export JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4000m"
    export USE_CCACHE=1
    . build/envsetup.sh
    lunch aosp_$device-userdebug
    mka otapackage

Instructions
----------------
- We don't have project paths like LineageOS so you need to define QCOM HAL variants in your device's BoardConfig.mk; instructions mentioned below
- You can see our device sources
- Need CAF HALs ? Add these to BoardConfig.mk:
```
TARGET_QCOM_BLUETOOTH_VARIANT := bt-caf
TARGET_QCOM_WLAN_VARIANT := wlan-caf
TARGET_RIL_VARIANT := caf
```
- MSM8916 devices add these to BoardConfig.mk:
```
TARGET_QCOM_AUDIO_VARIANT := caf-msm8916
TARGET_QCOM_DISPLAY_VARIANT := caf-msm8916
TARGET_QCOM_MEDIA_VARIANT := caf-msm8916
```
