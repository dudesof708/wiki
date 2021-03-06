# Sputnik App

-----

[Back to homepage](../..) • [software development guides](..)

-----

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
    * [VS Code](#vs-code)
    * [Vim](#vim)
    * [Expo Snack](#expo-snack)
    * [Xcode](#xcode)
  * [Setting Up](#setting-up)
  * [Making an Edit](#making-an-edit)
  * [Testing Your Changes](#testing-your-changes)

## Prerequisites

You'll need the following already set up in order to follow the [setup portion of this guide](#setup):

* `git`: You can follow the [git setup guide](../../software/git) in order to set up git.
* A GitHub account.

## Setup

You can go the [table of contents](#table-of-contents) in order to jump to any section of setup.

### Node.js Setup

1. Navigate to the [Node.js website](https://nodejs.org/en/) and download the latest LTS installer. You are encouraged to download any additional tools reccommended by Node.js.

*Note:* if you are a Linux user, you may have to access a NodeSource distribution. It is assumed that if you are a Linux user you know what you are doing.

### Expo Setup

1. Open a Terminal and run

   ```bash
   npm i expo-cli --global
   ```

2. Log in to expo with the command:

   ```bash
   expo login
   ```

   This will bring up a page in your web browser where you can either login or create an account on Expo's servers. Join the Dudes of 708 development team (owner: Gideon Tong).

### Device Setup

If you have an Android device, jump to the [Android device setup](#android-device-setup) section. If you have an iOS device, jump to the [iOS device setup](#ios-device-setup) section. You can set up both if you have both.

#### Android Device Setup

1. Download the [Expo Go](https://play.google.com/store/apps/details?id=host.exp.exponent) app from the Play Store.
2. Log into your Expo account. Every step after this is ***optional***.

![Expo Go on the Play Store](https://i.imgur.com/9ieXXvy.png)

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
2. Log into your Expo account.

> If you own a Mac, there are additional advanced setup steps you can take advantage of, but they will not be covered in this guide beacuse I don't own a Mac. If you are a Mac user and would like to contribute usage of Xcode or other iOS debugging tools, by all means, please submit an improvement for this section.

![Expo Go on the App Store](https://i.imgur.com/gyxfKNl.png)

## Developing

If you already have an editor you like, jump to [project structure](#project-structure).

### Editor

I personally use [VS Code](https://code.visualstudio.com/), but I'm going to try to cover all the potential ways you may want to develop. If you don't already use an editor, download [VS Code](https://code.visualstudio.com/) and head on to the [VS Code section](#vs-code)

Otherwise, pick your editor of choice:

* [VS Code](#vs-code)
* [Vim](#vim)
* [Expo Snack](#expo-snack)
* [Xcode](#xcode)

#### VS Code

![VS Code](https://i.imgur.com/mwHT7ZV.png)

You can download VS Code at [this link](https://code.visualstudio.com/). Thankfully, because VS Code is designed as an Electron app, it provides Javascript/Typescript extensions, debugging, and IntelliSense out of the box. ChompChomp is written in pure Javascript with React extensions, and does not support Typescript at this time.

This is really all you need, but you should set up [Expo Tools](https://marketplace.visualstudio.com/items?itemName=byCedric.vscode-expo) and [React Native Tools](https://marketplace.visualstudio.com/items?itemName=msjsdiag.vscode-react-native) (both are one click extensions to add) for your VS Code environment.

Next, proceed to [setting up](#setting-up).

#### Vim

![Vim](https://i.imgur.com/Jx1F46g.png)

Why are you reading this if you already know your way around Vim? Set it up for JavaScript/TypeScript bindings and you'll be fine. Next, proceed to [setting up](#setting-up).

#### Expo Snack

![Expo Snack](https://i.imgur.com/cTgvHYw.png)

> This isn't actually a screenshot of the code, but this is Expo Snack.

Expo Snack runs in the browser and basically acts like a Repl.it, if you have used that before. It provides a way to develop and test without leaving your browser. You can access it [here](https://snack.expo.io/).

It provides all the libraries and tools built-in, and is a conveneint way to develop. It isn't officially supported by ChompChomp but you are free to use this to develop if you wish to sync your changes to `git` manually.

Next, proceed to [setting up](#setting-up).

#### Xcode

Xcode is the official code editor by Apple for Macs, and is only available for macOS. You can download it at [this link](https://developer.apple.com/xcode/). It is also the only way to self-compile the iOS version of ChompChomp, so you'll need to follow this setup guide even if you don't use Xcode normally so you can compile.

Download Xcode from the link above and run it. Apple will set up all the developer tools for you automatically. You'll also need an Apple ID, which frankly is weird if you have a Mac but don't have one.

Next, proceed to [setting up](#setting-up).

### Setting Up

1. Clone the Sputnik App repository. If you don't know how, please see the [setting up git](../../software/git) guide.
2. Open Terminal or Command Prompt and navigate to the ChompChomp repository you cloned. Then run

   ```bash
   npm ci
   ```

   This process will take several minutes to complete if you're running for the first time. If you need to update your packages, use the following command instead:

   ```bash
   npm i
   ```

If you are curious how the files are laid out, please see [file structure](#file-structure), or you can see [the code structure](#code-structure) if you want to get a sense of how the code is formatted so you can make similar contributions.

### Making an Edit

Use an editor of your choice to edit a file, and the commit it. If you don't know how, see the [guide to using git](../../software/git).

### Testing Your Changes

Run this command to start the development server:

```bash
expo start
```
