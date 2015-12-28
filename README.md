#Grarak's 12.1 based device tree for the OnePlus 2
This tree is forked from Grarak's tree. I'll be making a few modifications for my personal use.

###Syncing repo
Add this to your localmanifest
```xml
<manifest>
  <project path="device/oneplus/oneplus2" name="myctek/android_device_oneplus_oneplus2" remote="github" revision="cm-12.1" />
  <project path="kernel/oneplus/msm8994" name="myctek/android_kernel_oneplus_msm8994" remote="github" revision="cm-12.1" />
  <project path="vendor/oneplus" name="myctek/android_vendor_oneplus" remote="github" revision="cm-12.1" />
```

###Building
```bash
. build/envsetup.sh
lunch cm_oneplus2-(eng/userdebug/user)
make #recipe
```
