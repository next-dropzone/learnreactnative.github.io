---
layout: post
title: React Native Default Structure
date: 2018-04-27 00:00:00 +0300
description: 
img: react-native-default-structure.png # Add image post (optional)
tags: [react native, mobile, mobile app, mobile development, react, react native training, learn react native] # add tag
---

One of the great things about React Native is the flexibility. You can do just about anything including organize the project however you want. This is great! But can be daunting as well, especially to new developers.

Before diving into coding let's do a quick overview of what you're getting by default. This will help you understand what you are working with and what everything means.

### Understanding the Default Structure

![react native default structure](/assets/img/react-native-default-folder-structure.png)

`android/`  This is the directory where all of the native Android code lives. If you dive in there you’ll find .gradle files, .java files, and .xml files. This is the directory you would open with Android Studio. You’ll rarely have to work in this directory.

`ios/`  Like the android directory this is where all of your native iOS code lives. You’ll find your xcode project in there, .plist files, .h files, .m files, etc. So if you want to open your project in xcode you would open ios/<PROJECT_NAME>.xcodeproj. You’ll rarely have to work in this directory.

`index.js`  This is the entry point for your iOS & Android app into the React Native code. It’s where you’ll want to register your app (via AppRegistry).

`Everything else`  You probably won’t have to worry about the other stuff — it’s mostly configuration for React Native and the rest is your standard node files/directories (node_modules/ and package.json).
