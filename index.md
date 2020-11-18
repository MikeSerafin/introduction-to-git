# Library 501 - Introduction to Git

## Workshop description
With this introduction to Git, we will go over the basics on Git and GitHub.  We will go over setting up a GitHub account, explaining basic commands like clone, add, and commit, setting up a repository on GitHub, and how to recover old versions of files.

You will not be an expert by the end of the class. You will probably not even feel very comfortable using Git. This is okay. We want to make a start but, as with any skill, using Git takes practice.

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
You may want to change the default editor to something more familiar by using the `core.editor` config. Any text editor can be made default by adding the correct file path and command line options (see [GitHub help](https://help.github.com/articles/associating-text-editors-with-git/)).  However, the simplest `core.editor` values are `"notepad"` on Windows, `"nano -w"` on Mac, and `"nano -w"` on Linux.  For example:
```bash
$ git config --global core.editor "notepad"
```
You will NOT get an immediate error message if you specify an incorrect or non-existent text editor command here. Therefore, you may first wish to test that the text editor you specify can be invoked, with (for the above example of `"notepad"` on Windows):
```bash
$ touch deleteme.txt
$ notepad deleteme.txt
```
Finally, to check that your configuration changes have been made, use:
```bash
$ git config --list
```

## Getting started with git

### Using Git
One of the main barriers to getting started with git is the language. Although some of the language used in git is fairly self-explanatory, other terms are not so clear. The best way to get to learn the language - which consists of a number of verbs such as `add`, `commit` and `push` (preceded by the word ‘git’) - is by using it, which is what we will be doing during this lesson. These commands will be explained as we proceed from setting up a new version-controlled project to publishing our own website.

### Creating a repository
A Git **repository** is a data structure used to track changes to a set of project files over time. Repositories are stored within the same directory as these project files, in a hidden directory called `.git`. We can create a new git repository either by using GitHub’s web interface, or via the command line. Let’s use the command line to create a git repository for the experiments that we’re going to do today.

First, we will create a new directory for our project and enter that directory.

```bash
$ mkdir hello-world
$ cd hello-world
```
We will now create an empty git reposityro to track changes to our project.  To do this we will use the git **init** command, which is simply short for *initialize*.


