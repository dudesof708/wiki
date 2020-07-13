# Preprocessing Videos

-----

[Back to homepage](../..) • [software resources guide](..)

-----

We use `ffmpeg` to preprocess our videos. Jump to [Windows](#windows), [macOS](#macos), or [Linux](#linux).

## Windows

1. Download the latest build of ffmpeg from [this website](https://ffmpeg.zeranoe.com/builds/).
2. Unzip the folder to a common directory, like `C:\ffmpeg`. Take note of this directory for later.
3. Open Windows Search, and type `Edit the system environment variables`. Select the option that appears.
4. Click the button that says **Environment Variables**.
   ![Environment Variables](https://i.imgur.com/0DWtMyg.png)
5. Under **User variables**, select the one that says **Path** and click **Edit...**
   ![Environment Variables](https://i.imgur.com/NbcSa3V.png)
6. Click **New**, and add the folder with `\bin` appended to the end of the original folder name you created. So if you unzipped it to `C:\ffmpeg`, add `C:\ffmpeg\bin`.
7. Save and exit all dialog boxes, and reboot your computer.

## macOS

You'll need a package manager, like [Homebrew](https://brew.sh/).

Now run:

```bash
brew install ffmpeg
```

## Linux

Linux users should be able to figure it out, the package is called `ffmpeg` in most major distributions. But if you really need a guide...

### Ubuntu or Debian

If you have the `apt` package manager, simply run:

```bash
sudo apt install ffmpeg -y
```

### Arch Linux or Manjaro

If you have the `pacman` package manager, simply run:

```bash
sudo pacman -S ffmpeg
```

### Fedora or CentOS

If you have RPM, simply run:

```bash
sudo dnf install ffmpeg
```
