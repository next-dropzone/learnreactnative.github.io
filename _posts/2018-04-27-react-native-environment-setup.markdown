---
layout: post
title: React Native Environment Setup
date: 2018-04-26 00:00:00 +0300
description: There are a couple of things you need to install to set up the environment for React Native. We will use linux as our building platform. # Add post description (optional)
img: environment-setup.png # Add image post (optional)
tags: [react native, mobile, mobile app, mobile development, react, react native training, learn react native] # add tag
---

### NodeJS and NPM

You can follow the [link](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-16-04). to install NodeJS.

### Install React Native

Run the following code to install React Native.

```
npm install -g react-native-cli
```

### Android - Install Android Studio

You can install Android studio by following this [link](https://developer.android.com/studio/install).

### IOS - Install XCode

For IOS development you will need XCode [link](https://itunes.apple.com/us/app/xcode/id497799835?mt=12).

### Create First App

We will initialize our first app by running the code given below in the terminal from the folder where we want to create the app.

```
react-native init AwesomeApp
```

### Run React Native Packager

First, we need to open the app folder in terminal.

```
cd AwesomeApp
```

Now, we can run the packager.

```
react-native start
```

### Run the App on Android emulator

This step will open your app in the Android emulator. Run the following command in another terminal.

```
react-native run-android
```