#Grarak's 12.1 based device tree for the OnePlus 2
This tree is forked from Grarak's tree. I'll be making a few modifications for my personal use. You can build from these sources if you want.

###How to build?
These instructions are ubuntu-centric.
First, download and install the required packages for the whole process.
To do that, open Terminal, and type:
```xml
sudo apt-get install bison build-essential curl flex git gnupg gperf libesd0-dev liblz4-tool libncurses5-dev libsdl1.2-dev libwxgtk2.8-dev libxml2 libxml2-utils lzop openjdk-7-jdk openjdk-7-jre pngcrush schedtool squashfs-tools xsltproc zip zlib1g-dev
```
If you use a 64-bit system, you'll also need the following packages:
```xml
g++-multilib gcc-multilib lib32ncurses5-dev lib32readline-gplv2-dev lib32z1-dev
```
Also install the Android SDK, by typing:
```xml
sudo apt-get install android androidsdk-uiautomatorviewer android-copyright android-src-vendor android-emulator android-tools-adb android-headers android-tools-adbd androidsdk-ddms android-tools-fastboot androidsdk-hierarchyviewer android-tools-fsutils androidsdk-traceview
```
Setup your git using the following commands:
```xml
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR EMAIL ADDRESS"
```
Now we have to setup directories for installing repo, by typing:
```xml
mkdir ~/bin
PATH=~/bin:$PATH
```
Download repo and make it executable, by typing:
```xml
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
```
To load profile again, type:
```xml
. ~/.profile
```
Now we have to setup directories for downloading CyanogenMod sources, by typing:
```xml
mkdir ~/"DIRECTORY_NAME"
cd ~/"DIRECTORY_NAME"
ls
```
To initialize the repo, and its 12.1 branch, type:
```xml
repo init -u git://github.com/CyanogenMod/android.git -b cm-12.1
```
Now to create the local_manifests.xml file:
```xml
mkdir .repo/local_manifests
nano .repo/local_manifests/local_manifests.xml
```
Now we have to add sources to the local_manifests.xml file, copy the following code as it is:
(Save the local_manifests.xml code by using the key combination Ctrl+O, after you've done copying the following code)
```xml
<?xml version="1.0" encoding="UTF-8"?>
<manifest>
<project path="device/oneplus/oneplus2" name="myctek/android_device_oneplus_oneplus2" remote="github" revision="cm-12.1" />
<project path="kernel/oneplus/msm8994" name="myctek/android_kernel_oneplus_msm8994" remote="github" revision="cm-12.1" />
<project path="vendor/oneplus" name="myctek/proprietary_vendor_oneplus" remote="github" revision="cm-12.1" />
<project path="external/mm-dash" name="CyanogenMod/android_external_mm-dash" remote="github" revision="cm-12.1" />
<project path="device/qcom/common" name="CyanogenMod/android_device_qcom_common" remote="github" revision="cm-12.1" />
</manifest>
```
Now sync the repo using:
(Sources are huge, so syncing will take time depending on your internet speed)
```xml
repo sync
```
Building:
```bash
. build/envsetup.sh
lunch cm_oneplus2-(eng/userdebug/user)
make #recipe
```
