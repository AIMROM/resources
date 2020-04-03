# AIMROM

If you're going to build AIMROM for your device, please head to [Getting Started](https://github.com/AIMROM/manifest/blob/10.0/README.mkdn#getting-started) section of our manifest. This README is intended for anyone interested to become a maintainer of AIMROM.

## Table of Contents

* [General Requirements](#general-requirements)
* [Applying for Maintainership](#applying-for-maintainership)

## General Requirements

1. You **MUST** own the device. Blind and untested builds are not allowed. Exemptions are given for devices with little hardware derivations, as long as you still own the base device.
2. You are applying to maintain your devices, *not to do some sort of buildbotting*. Please take that into consideration! You gain some, you lose some.
3. Have done **AT LEAST** one working UNOFFICIAL build.
4. All sources used to build the ROM **MUST BE** made public via [AIMROM-DEVICES](https://github.com/AIMROM-DEVICES) organisation, **MUST BE** buildable and **MUST** reproduce a similar working build. In addition, device sources published **MUST** have proper authorships and **MUST** have working `aim.dependencies`. This implies that you have a knowledge of Git as well and not just editing files using *GitHub file editor*.
5. Maintainers are *expected* to know what they're doing and what issues to be resolved. Feel free to ask team members if you need help beyond your knowledge.
6. Maintainers are **ONLY** allowed to include same amount of device-specific features as stock firmware, in order to keep consistency of user experiences between devices.
7. Maintainers are **PROHIBITED** to include features that aren't licensed to ship with certain devices. This includes but not limited to Qualcomm aptX, aptX HD, aptX Low Latency (LL), aptX Adaptive, etc. exFAT are *exempted* from this prohibition since Microsoft has published specifications of the file system to encourage its use on open source communities.
8. Kernels shipped with the ROM are *discouraged* to contain excess features that a little to no people will use. This includes but not limited to custom governors, custom I/O schedulers, custom hotplugs, kernel tweaks, etc., unless it's necessary to have the device to function properly.

**We also take into decision your attitude towards community you're maintaining the device on. We won't accept any maintainers with major attitude issues as we don't want to bring ourselves into trouble!**

## Applying for Maintainership
Please fork [packages_apps_freedomhub](https://github.com/AIMROM/packages_apps_freedomhub) and make a Pull Request against `10.0` branch containing the following changes below existing entries (sample, please change accordingly):

* `res/values/maintainers.xml`:
  ```
  +  <string name="device_goldfish">Android x86 emulator (goldfish)</string>
  +  <string name="goldfish_maintainer">John Doe (johndoe)</string>
  ```

* `res/xml/maintainers.xml`:
  ```
  +        <Preference
  +            android:title="@string/goldfish_maintainer"
  +            android:summary="@string/device_goldfish"
  +            android:icon="@drawable/ic_devs_phone" >
  +            <intent
  +                android:action="android.intent.action.VIEW"
  +                android:data="https://github.com/johndoe" />
  +        </Preference>
  ```

If device(s) you're applying requires new vendor entry to be added:

* `res/values/maintainers.xml`:
  ```
  +  <string name="android_devices_cat">Android</string>
  ```

* `res/xml/maintainers.xml`:
  ```
  +    <PreferenceCategory
  +        android:key="android_devices"
  +        android:title="@string/android_devices_cat" >
  +
           ... (device list)
  +
  +    </PreferenceCategory>
  ```

When creating Pull Request, please state which device you're applying as well as link to your repository (READ: yours, not LineageOS, not PixelExperience, not [insert 69 ROMs here]). Please follow the formatting given to make it easier for us to keep list clean.
