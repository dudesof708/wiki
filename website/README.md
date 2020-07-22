# Website Contribution Guide

-----

[Back to homepage](..)

-----

First, make sure you have [git set up](../software/git).

## Table of Contents

* [Downloading the source code](#downloading-the-source-code)
* [Making contributions](#making-contributions)
* [Uploading contributions](#uploading-contributions)

## Downloading the Source Code

You can follow the [git setup guide](../software/git), and clone [this repository](https://github.com/dudesof708/7o8.tech). If you are using command-line, the command is:

```bash
git clone https://github.com/dudesof708/7o8.tech.git
```

## Making Contributions

To load the website code, after finding your repository, head to [GitHub Desktop](#github-desktop) if you are using GitHub Desktop and [Command Line](#command-line) if you are using git.

We use **HTML, Javascript, and CSS** to host a static page of our website. It is deployed with [Jekyll](https://jekyllrb.com/), but you don't need to know or worry about how this works. Simply edit the website in your preferred text editor and push your changes as described in [Uploading Contributions](#uploading-contributions).

### GitHub Desktop

If you are using GitHub Desktop, you need to switch from the **`master`** branch to the **`gh-pages`** branch, so select **Current Branch** on the top of the window and select `gh-pages` to switch to it. You should immediately see all the website files show up in the project folder.

### Command Line

If you are using git, simply run the following command to switch branches:

```bash
git checkout gh-pages
```

## Uploading Contributions

Find the subheading that describes you and following the instructions for adding your changes to the website.

### Dudes of 708 Member

As a member, we use a 100% trust system and do not verify your changes, as a static site can easily be rolled back if you make a mistake. Follow the following steps to upload your changes:

If you are using GitHub Desktop:

1. Type a description of your changes in the **Summary** box in the bottom left corner.
2. Click the blue **Commit to gh-pages** button in the bottom left corner.
3. On the top bar, *Fetch origin* will change to **Push changes**. Click it. Your changes are now uploaded.

If you are using Git, it's as simple as:

```bash
git commit -m <summary of your changes>
git push
```

### Friends of 708

You'll have to fork the repository and make a pull request. Your pull request will recieve immediate attention as a friend of 708. Additionally, you could also help us fill out this section with detailed instructions!

### Everyone Else

As with the friends of 708, you'll have to fork the repository and make a pull request. We can't wait to see what you come up with!
