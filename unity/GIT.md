# Git Best Practices

-----

[Back to homepage](..)

-----

## How to use git

Instead of writing an entirely new guide, I reccomend you check out [git without deep shit](https://rogerdudler.github.io/git-guide/) as a good starting point to understanding what **git** is, which is how we control different versions of our code, assets, and other files.

By the end of the guide, it is expected that you understand at a basic level what the following are:

* Commits
* Pulling and Pushing Changes
* Branches

If you followed the [guide to setup Unity](.) then you'll know that you don't need any commands, all of these features are available to you in GitHub Desktop. But one more thing - if you are developing a new feature or part of the game that could break other parts of the game, instead of pushing directly, you'll need to make a pull request.

### Pull Requests

A pull request is basically the idea that rather than pushing the button that says "merge branches," which could break a lot of things, you'll go to the project website and click on the **Pull requests** tab and file a new pull request, selecting the branch you're working on and the `master` branch so someone else can make sure everything is working. Always helps to have a second set of eyes!

### The .gitignore

There exists a file in your project directory known as `.gitignore` which lists all the files that are to be ignored when pushing code up to the internet. You'll want to make sure random files you generate, like logs, passwords, and such are in this file so it doesn't get pushed to the internet.

## Best Practices

* Write clean commits and your commit comment should say what the code does (in case we need to revert the change)
* Commit often, so you don't lose your work
* Don't delete past commits, we have basically unlimited storage
* Don't commit files you generated! (see the section about gitignores)
* **Use pull requests!**
