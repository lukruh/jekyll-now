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

Some dependencies are required to build software for android devices. The easiest way to solve them is installing the Android Studio IDE.
Download and extract the latest release (~700MB) and navigate to the exctracted bin folder and run the start script to set some initial configurations.

```shell
cd path/to/android-studio/bin
./studio.sh
```

