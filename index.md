# Library 501 - Introduction to Git

## Workshop description
With this introduction to Git, we will go over the basics on Git and GitHub.  We will go over setting up a GitHub account, explaining basic commands like clone, add, and commit, setting up a repository on GitHub, and how to recover old versions of files.

**Note**: This lesson is derived from the [Library Carpentries Introduction to Git](https://librarycarpentry.org/lc-git/) under the Creative Commons ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/))

## Setup
1. Create a free [GitHub](https://github.com/join) account and confirm your email.
2. Download and install Git for your operating system: https://git-scm.com/downloads (Note: Git for Windows comes bundled with the Git BASH terminal that allows you to use UNIX-style commands on Windows)
3. Configure Git by opening a terminal and entering the following commands:
```bash
$ git config --global user.name "Your Name"
$ git config --global user.email "your@email"
```
This user name and email will be recorded with each commit in the history of your repositories. The email address should be the same one you used when setting up your GitHub account.
You may want to change the default editor to something more familiar by using the `core.editor` config.

