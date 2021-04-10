# ChompChomp Development Guide

-----

[Back to homepage](../..) • [software development guides](..)

-----

> This is currently a work-in-progress guide. Please feel free to contribute to it.

Congratulations! So you want to get involved in ChompChomp's development. Your contributions will be greatly appreciated.

## Table of Contents

* [Prerequisites](#prerequisites)
* [Setup](#setup)
  * [Node.js Setup](#nodejs-setup)
  * [Expo Setup](#expo-setup)
  * [Device Setup](#device-setup)
    * [Android Device Setup](#android-device-setup)
    * [iOS Device Setup](#ios-device-setup)
* [Developing](#developing)
  * [Editor](#editor)
  * [Project Structure](#project-structure)
  * [Making an Edit](#making-an-edit)

## Prerequisites

You'll need the following already set up in order to follow the [setup portion of this guide](#setup):

• `git`: You can follow the [git setup guide](../../software/git) in order to set up git.
• A GitHub account, and contributor access to the [`ChompChomp`](https://github.com/dudesof708/ChompChomp) repository.

## Setup

You can go the [table of contents](#table-of-contents) in order to jump to any section of setup.

### Node.js Setup

1. Navigate to the [Node.js website](https://nodejs.org/en/) and download the latest LTS installer. You are encouraged to download any additional tools reccommended by Node.js.

*Note:* if you are a Linux user, you may have to access a NodeSource distribution. It is assumed that if you are a Linux user you know what you are doing.

### Expo Setup

1. Open a Terminal and run `npm i expo-cli --global`.

### Device Setup

If you have an Android device, jump to the [Android device setup](#android-device-setup) section. If you have an iOS device, jump to the [iOS device setup](#ios-device-setup) section. You can set up both if you have both.

#### Android Device Setup

1. Download the [Expo Go](https://play.google.com/store/apps/details?id=host.exp.exponent) app from the Play Store. Every step after this is ***optional***.

*Optional Steps:*

1. Download the [Android SDK Platform Tools](https://dl.google.com/android/repository/platform-tools-latest-windows.zip) onto your computer.
2. Extract the folder to a folder on your computer you won't easily delete, like `C:\Software\platform-tools` on Windows or `/home/<username>/platform-tools` on macOS or Linux.
3. Open a Terminal or Command Prompt window and navigate to the folder you extracted using the `cd` (**c**hange **d**irectory) command. For example, if I extracted it to `C:\Software\platform-tools`, I would write `cd C:\Software\platform-tools`.
4. On your Android device, enable Developer Options. First navigate to **Settings**, and scroll to the bottom and find **About Phone**.
5. Tap **Build Number** seven times. You should see a toast telling you Developer Mode is now enabled.
6. Navigate back one screen, and you'll find a **Developer Options** button. Tap it, and enable the option that says something like **Enable USB debugging**. The exact wording may depend on your device and version of Android.
7. Plug your Android device into your computer. In your Terminal, type `adb devices` on Windows or `./adb devices` for macOS and Linux computers.
8. If prompted on your Android device, accept the prompt to allow USB debugging on your device.

#### iOS Device Setup

1. Download the [Expo Go](https://apps.apple.com/us/app/expo-go/id982107779) app from the App Store.

> If you own a Mac, there are additional advanced setup steps you can take advantage of, but they will not be covered in this guide beacuse I don't own a Mac. If you are a Mac user and would like to contribute usage of Xcode or other iOS debugging tools, by all means, please submit an improvement for this section.

## Developing

If you already have an editor you like, jump to [project structure](#project-structure).

### Editor

> This section is a work-in-progress.

### Project Structure

> This section is a work-in-progress.

### Making an Edit

> This section is a work-in-progress.
