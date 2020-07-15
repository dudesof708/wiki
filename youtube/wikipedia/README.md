# Wikipedia Speedrunning

-----

[Back to homepage](../..) • [YouTube reference](..)

-----

## Table of Contents

* [Dudes of 708 App Usage](#dudes-of-708-app-usage)
* [Screen Recording Setup](#screen-recording-setup)
  * [OBS Setup](#obs-setup)
  * [Livesplit Setup](#livesplit-setup)

## Dudes of 708 App Usage

The [wikipedia-speedrun](https://github.com/dudesof708/wikipedia-speedrun) Dudes of 708 app will allow you to generate two endpoints for which the entire group can then speedrun and try to get from start to finish. It has features like points tracking as well, so you can easily keep track of the score.

How to use it is coming soon, as well as a cheating feature (a required feature of *any* app).

## Screen Recording Setup

We will use OBS for the screen recorder and Livesplit to keep track of our times.

### Livesplit Setup

1. Download Livesplit from [this link](https://livesplit.org/) and open it.
2. You'll be greeted with something that looks like the screenshot below. Right-click it and click **Edit layout...**
   ![LiveSplit](https://i.imgur.com/tY1JAxU.png)
3. You'll be greeted with the Layout Editor. Remove an item by selecting it in the menu and pressing the *Minus* button to the left. Remove everything ***except*** **Timer**.
   ![Layout Editor](https://i.imgur.com/XTNKGqm.png)
4. You'll be left with just a timer. Right-click it one more time and click **Settings**.
5. Set your hotkeys to your preferred setting. The ones you should care about are **Start/Stop** and **Reset**. I've left mine as the default, but if you don't have a numpad, you'll have to change them. Since we're speedrunning Wikipedia, you probably won't need to press any keys, so it won't matter which buttons you choose anyways.
6. To exit LiveSplit, right-click it and click **Exit**.

### OBS Setup

This guide is simple, so hopefull you can follow it. If you'd like to make it more detailed, submit a pull request.

1. Download OBS from [this link](https://obsproject.com/).
2. If you have your own OBS setup already, skip to step 3.
   1. Create a new profile using **Profile > New**, and a new scene collection using **Scene Collection > New**. Name them whatever you want.
   2. Click on **Settings**, and set your base and output resolution to the same thing. For high-end computers, use `3840x2160`. For most computers, use `1920x1080`. For low-end machines, use `1280x720`.
   3. Click on **Audio**, and set your desktop audio and mic/auxiliary audio both to **Default**.
   4. Exit the Settings panel.
3. We'll now set up our scene. If you're not looking at a blank scene, create a new one with the *Plus* button in the bottom left.
4. In the Sources panel, click the *Plus* button and select **Display Capture** if you're lazy or **Window Capture** and highlight it on your web browser.
5. Create another source with the *Plus* button again and select **Window Capture**, this time selecting LiveSplit.
6. Draw your windows around in OBS so they fit on your screen.
