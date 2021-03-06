# Setting Up IDEs

-----

[Back to homepage](../../..) • [software resources guide](..) • [Unity setup guide](..)

-----

An **IDE** is an Integrated Development Environment. You can think of Unity as an IDE for developing the game objects, assets, and the world itself. But what about the code that powers the game? Unity uses a programming language called **C#** to power its scripts, and this requires something known as the **.NET Framework** from Microsoft. This guide will walk you through setting up everything.

## Quickstart

If you're an experienced developer, follow the quickstart. Otherwise, jump down to [Installation](#installation) to follow a more detailed guide with screenshots.

1. Get a text editor of your choice. I use [VS Code](https://code.visualstudio.com/). If you also use VS Code, install the [C# Plugin](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).
2. Install the [.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/sdk-for-vs-code), and refresh your PATH.

## Installation

1. You'll need a text editor of your choice. I reccommend [VS Code](https://code.visualstudio.com/), as it has a lot of powerful features, like [linting](../../../glossary#l), [IntelliSense](../../../glossary#i), and more.
2. Now you'll need a .NET Framework SDK. Download the [.NET Core SDK for VS Code](https://dotnet.microsoft.com/download/dotnet-core/sdk-for-vs-code) or the [.NET Core SDK](https://dotnet.microsoft.com/download) if you chose another code editor.
   ![.NET Installer](https://i.imgur.com/aYdqEhY.png)
3. If you chose to go with VS Code, I reccommend installing the [C# Plugin](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) so you get support in your code editor for all of its fancy features.
4. Reboot your computer.

### Footnotes

The C# extension in VS Code replicates the C# functionality you might see in VS Community (the most popular IDE for C# development), which includes a feature called CodeLens which can display things like the number of times your variable is referenced. If you're like me, you probably find this super annoying, so I was able to disable it by unchecking the setting: **Extensions > C# configuration > Csharp > Reference Code Lens**.

If you need steps on how to do this:

![Disabling CodeLens](https://i.imgur.com/wky43K8.png)

1. Press `Ctrl + Comma` on your keyboard, then search for `codelens`.
2. Under **Extensions**, click **C# configuration**.
3. Find **Reference Code Lens** and uncheck it.
