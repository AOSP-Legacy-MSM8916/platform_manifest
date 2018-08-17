<img src="https://raw.githubusercontent.com/AOSP-Legacy-MSM8916/platform_manifest/pie-logo.png">

AOSP LEGACY MSM8916 Manifest FOR ANDROID 9.0.0 ( PIE )
====================

Create AOSP folder
----------------------

    mkdir ~/aosp
    cd ~/aosp
    

GIT config (nickname, e-mail)
-----------------------------

    git config --global user.email "mail@domain.com"
    git config --global user.name "login"
    

To initialize your local repository use
---------------------------------------

    repo init -u https://github.com/AOSP-LEGACY-MSM8916/platform_manifest.git -b pie-r1
    

Then to sync up:
----------------

    repo sync --current-branch --no-tags --no-clone-bundle --optimized-fetch --force-broken --force-sync -j16

Build command is
----------------
    export JACK_SERVER_VM_ARGUMENTS="-Dfile.encoding=UTF-8 -XX:+TieredCompilation -Xmx4000m"
    . build/envsetup.sh
    lunch aosp_$device-userdebug
    make -jx otapackage

Instructions
----------------
- We don't have project paths like LineageOS So You Need To Add QCOM Targets in Your BoardConfig Makefile.
- You Can See Our Device Sources
- ADD THIS TO B*C*.mk 
TARGET_QCOM_AUDIO_VARIANT := caf-msm8916
TARGET_QCOM_DISPLAY_VARIANT := caf-msm8916
TARGET_QCOM_MEDIA_VARIANT := caf-msm8916
-Need CAF ?
TARGET_QCOM_BLUETOOTH_VARIANT := bt-caf
TARGET_QCOM_WLAN_VARIANT := wlan-caf
TARGET_RIL_VARIANT := caf
