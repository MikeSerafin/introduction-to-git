# Library 501 - Introduction to Git

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
