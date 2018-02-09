# Docker for Android SDK 26

Docker for Android SDK 26 with preinstalled build tools and emulator image

> Edit from [mindrunner/docker-android-sdk](https://github.com/mindrunner/docker-android-sdk)

**Installed Packages**
```bash
# sdkmanager --list
  Path                                        | Version | Description                                | Location                                    
  -------                                     | ------- | -------                                    | -------                                     
  build-tools;26.0.2                          | 26.0.2  | Android SDK Build-Tools 26.0.2             | build-tools/26.0.2/                         
  emulator                                    | 27.1.7  | Android Emulator                           | emulator/                                   
  patcher;v4                                  | 1       | SDK Patch Applier v4                       | patcher/v4/                                 
  platform-tools                              | 27.0.1  | Android SDK Platform-Tools                 | platform-tools/                             
  platforms;android-26                        | 2       | Android SDK Platform 26                    | platforms/android-26/                       
  system-images;android-26;google_apis;x86_64 | 8       | Google APIs Intel x86 Atom_64 System Image | system-images/android-26/google_apis/x86_64/
  tools                                       | 26.1.1  | Android SDK Tools                          | tools/  
```

**Usage**

- Interactive way
  ```bash
  $ docker run -it --rm --privileged androidsdk/android-26:latest bash
  # check installed packages
  $ sdkmanager --list
  # create and run emulator
  $ avdmanager create avd -n first_avd -k "system-images;android-26;google_apis;x86_64"
  $ emulator -avd first_avd -no-window -no-audio &
  $ adb devices
  # You can also run other Android platform tools, which are all added to the PATH environment variable
  ```

- Non-interactive way
  ```bash
  # check installed packages
  $ docker run -it --rm androidsdk/android-26:latest sdkmanager --list
  # create and run emulator
  $ docker run -it --rm androidsdk/android-26:latest avdmanager list avd
  # You can also run other Android platform tools, which are all added to the PATH environment variable
  ```