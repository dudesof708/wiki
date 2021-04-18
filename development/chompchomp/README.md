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
    * [VS Code](#vs-code)
    * [Vim](#vim)
    * [Expo Snack](#expo-snack)
    * [Xcode](#xcode)
  * [Setting Up](#setting-up)
  * [Project Structure](#project-structure)
    * [File Structure](#file-structure)
    * [Code Structure](#code-structure)
    * [Data Storage Format](#data-storage-format)
      * [Queue](#queue-data)
      * [History](#history-data)
  * [Making an Edit](#making-an-edit)
  * [Testing Your Changes](#testing-your-changes)
  * [Building the App](#building-the-app)
    * [iOS Builds](#ios-builds)
    * [Android Builds](#android-builds)
  * [Deploying Updates](#deploying-updates)

## Prerequisites

You'll need the following already set up in order to follow the [setup portion of this guide](#setup):

* `git`: You can follow the [git setup guide](../../software/git) in order to set up git.
* A GitHub account, and contributor access to the [`ChompChomp`](https://github.com/dudesof708/ChompChomp) repository.

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

You can download VS Code at [this link](https://code.visualstudio.com/). Thankfully, because VS Code is designed as an Electron app, it provides Javascript/Typescript extensions, debugging, and IntelliSense out of the box. ChompChomp is written in pure Javascript with React extensions, and does not support Typescript at this time.

This is really all you need, but you should set up [Expo Tools](https://marketplace.visualstudio.com/items?itemName=byCedric.vscode-expo) and [React Native Tools](https://marketplace.visualstudio.com/items?itemName=msjsdiag.vscode-react-native) (both are one click extensions to add) for your VS Code environment.

Next, proceed to [setting up](#setting-up).

#### Vim

Why are you reading this if you already know your way around Vim? Set it up for JavaScript/TypeScript bindings and you'll be fine. Next, proceed to [setting up](#setting-up).

#### Expo Snack

Expo Snack runs in the browser and basically acts like a Repl.it, if you have used that before. It provides a way to develop and test without leaving your browser. You can access it [here](https://snack.expo.io/).

It provides all the libraries and tools built-in, and is a conveneint way to develop. It isn't officially supported by ChompChomp but you are free to use this to develop if you wish to sync your changes to `git` manually.

Next, proceed to [setting up](#setting-up).

#### Xcode

Xcode is the official code editor by Apple for Macs, and is only available for macOS. You can download it at [this link](https://developer.apple.com/xcode/). It is also the only way to self-compile the iOS version of ChompChomp, so you'll need to follow this setup guide even if you don't use Xcode normally so you can compile.

Download Xcode from the link above and run it. Apple will set up all the developer tools for you automatically. You'll also need an Apple ID, which frankly is weird if you have a Mac but don't have one.

Next, proceed to [setting up](#setting-up).

### Setting Up

1. Clone the [`ChompChomp`](https://github.com/dudesof708/ChompChomp) repository. If you don't know how, please see the [setting up git](../../software/git) guide.
2. Open Terminal or Command Prompt and navigate to the ChompChomp repository you cloned. Then run

   ```bash
   npm ci
   ```

   This process will take several minutes to complete if you're running for the first time. If you need to update your packages, use the following command instead:

   ```bash
   npm i
   ```

### Project Structure

If you are curious how the files are laid out, please see [file structure](#file-structure), or you can see [the code structure](#code-structure) if you want to get a sense of how the code is formatted so you can make similar contributions.

#### File Structure

The project is broken up into a few important folders and files (you can click on the names of files and folders to view them):

* [`assets`](https://github.com/dudesof708/ChompChomp/tree/master/assets): Stores asset files, images, icons, and other such static files that remain largely unchanged
* [`components`](https://github.com/dudesof708/ChompChomp/tree/master/components): Small Javascript files that may be used once or more than once, but do not represent an entire view
  * [`ErrorDialog.js`](https://github.com/dudesof708/ChompChomp/blob/master/components/ErrorDialog.js): Dialog box for errors
  * [`LoadingDialog.js`](https://github.com/dudesof708/ChompChomp/blob/master/components/LoadingDialog.js): Loading dialog box
  * [`OfflineBanner.js`](https://github.com/dudesof708/ChompChomp/blob/master/components/OfflineBanner.js): Banner that shows an alert if you are offline
  * [`SmallOfflineBanner.js`](https://github.com/dudesof708/ChompChomp/blob/master/components/SmallOfflineBanner.js): Small offline banner for specific item adding screens
  * [`StoreSelector.js`](https://github.com/dudesof708/ChompChomp/blob/master/components/StoreSelector.js): The dialog box that allows you to select a store
  * [`UploadErrorDialog.js`](https://github.com/dudesof708/ChompChomp/blob/master/components/UploadErrorDialog.js): The dialog box that shows up when the upload fails
* [`config`](https://github.com/dudesof708/ChompChomp/tree/master/config): Config files for various parts of the app
* [`views`](https://github.com/dudesof708/ChompChomp/tree/master/views): Different screens for the app
  * [`CameraScreen.js`](https://github.com/dudesof708/ChompChomp/blob/master/views/CameraScreen.js): Screen for taking photos
  * [`ConfigScreen.js`](https://github.com/dudesof708/ChompChomp/blob/master/views/ConfigScreen.js): Screen for changing settings
  * [`HistoryScreen.js`](https://github.com/dudesof708/ChompChomp/blob/master/views/HistoryScreen.js): Screen for looking at your upload history
  * [`HomeScreen.js`](https://github.com/dudesof708/ChompChomp/blob/master/views/HomeScreen.js): The home screen
  * [`ItemUploadScreen.js`](https://github.com/dudesof708/ChompChomp/blob/master/views/ItemUploadScreen.js): Screen to create a new item or add data about an existing item
  * [`QueueScreen.js`](https://github.com/dudesof708/ChompChomp/blob/master/views/QueueScreen.js): Screen to check items you've yet to upload
  * [`QuickAddScreen.js`](https://github.com/dudesof708/ChompChomp/blob/master/views/QuickAddScreen.js): Screen if you don't want to add data while walking around
  * [`ScannerScreen.js`](https://github.com/dudesof708/ChompChomp/blob/master/views/ScannerScreen.js): Screen for scanning barcodes
* [`App.js`](https://github.com/dudesof708/ChompChomp/blob/master/App.js): Main entrypoint of the app, defines the screens of the app
* [`app.json`](https://github.com/dudesof708/ChompChomp/blob/master/app.json): App definition file

#### Code Structure

A quick overview of the way our code is structured:

* All objects, views, components, etc. are just wrapped functions. Classes don't make sense, as if you're writing some sort of data class or handler, it shouldn't be included in ChompChomp, but in its own library as a repository.
* We should strive to make ChompChomp just a frontend, and do little processing on the device.
* We use CamelCase for naming convention, with a capital letter for wrapped functions and objects and a lowercase letter like camelCase for variables.

**Components** appear in the `components` folder and represent parts of views that may or may not be reused. This can include selection boxes, dialog boxes, repeated text input boxes, etc.

**Views** appear in the `views` folder, and there is one file/function for every view that appears in the app. Each one is linked to the `App.js` file.

#### Data Storage Format

The app stores a few pieces of information

##### Queue Data

Queue data is stored in the key `queue` and is stored as a JSON string array. Each element is a JSON object containing several keys:

* `type`: One of `new`, `update`, or `quick`. New items contain full information, updates contain only the barcode, store, and price, and quick items contain only barcode and images.
* `payload`: The relevant payload to upload.

An example is below:

```json
[
  {
    "type": "new",
    "payload": {
      "date": "2021-04-18T22:34:11.088180+00:00",
      "store": "7 West Los Angeles, CA",
      "name": "String Cheese",
      "price": "1.99",
      "weight": "16",
      "barcode": "01234567"
    }
  },
  {
    "type": "update",
    "payload": {
      "barcode": "87654321",
      "store": "65 Danville, CA",
      "date": "2021-04-19T22:34:29.089034+00:00",
      "price": "2.99"
    }
  },
  {
    "type": "quick",
    "payload": {
      "barcode": "55555555",
      "images": [
        ...
      ]
    }
  }
]
```

##### History Data

History data is stored in the key `history` and is stored as a JSON string array. Each element is a string containing the name of the item uploaded to the database. If there is more than the maximum in the list, the oldest is pushed off the list (it behaves as a queue).

An example is below:

```json
[
  "String Cheese",
  "Cheddar Cheese",
  "Mozarella Cheese",
  "American Cheese",
  "Feta Cheese"
]
```

### Making an Edit

Use an editor of your choice to edit a file, and the commit it. If you don't know how, see the [guide to using git](../../software/git).

### Testing Your Changes

Run this command to start the development server:

```bash
expo start
```

### Building the App

Your changes are automatically built whenever you change the version number in `app.json`. Simply bump the minor revision number by 1 and you'll get a build back within the hour. Typically builds on the server take about 20-30 minutes for Android and 10-20 minutes for iOS. iOS builds are currently not supported by the ChompChomp development server, as you get a package back, so you'll need to build iOS manually.

*Step by step:*

1. Open the `app.json` file.
2. Find the version number that says something like 1.0.0.
3. Change the number so it says 1.0.1.
4. Save and commit your changes.

To build for iOS and test it on your device as a fully compiled app, head below to [iOS Builds](#ios-builds). To build it for Android instead, head below to [Android Builds](#android-builds).

#### iOS Builds

> This section is a work-in-progress.

#### Android Builds

> This section is a work-in-progress.

### Deploying Updates

> This section is a work-in-progress.
