---
layout: post
title: Create an Android App with HTML5
---

Frameworks such as Cordova make it possible to create an application with common web technologies like HTML and JavaScript.
The created application/website can be exported to different platforms: Browser (website), Native (electron), Android, iOS...
This is a quick guide through the first steps from installing cordova and android requirements to exporting the first HelloWorld app as `.apk`.


## Install cordova

Following the Get Started section from [cordova website](https://cordova.apache.org/)

```shell
npm install cordova
```

If npm is not installed run 

```shell
sudo apt install npm
```

and try again.

## Install Android Studio
Some dependencies are required to build software for android devices. The easiest way to solve them is installing the Android Studio IDE as recommended at the [Cordova Website](https://cordova.apache.org/docs/en/latest/guide/platforms/android/index.html#requirements-and-support).
[Download](https://developer.android.com/studio/#downloads) and extract the latest release (~700MB) and navigate to the exctracted bin folder and run the start script to set some initial configurations.

```shell
cd path/to/android-studio/bin
./studio.sh
```

Click through the installation wizzard and decide if you want to at a virtual device (to test your app in an emulator on your pc) at the cost of a 1.5GB download. 

Start Android Studio (maybe you have to create an empty project if you cant skip that step).
Open the Android SDK Manager (Tools > SDK Manager) and install the sdk api 19-28 which is the latest supported from cordova (2020/01).

![screenshot](img/screen_sdk_api.png)

Add this line to your `~.bashrc` with the correct path:
```bash
export PATH=${PATH}:/home/user/Android/Sdk/platform-tools:/home/user/Android/Sdk/tools
```

## Install Gradle

Gradle is a build tool that is used to build the Android App Package file `.apk`.
```shell
sudo apt install gradle
```

## Create the HelloWorld app
