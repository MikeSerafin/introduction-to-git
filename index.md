# Library 501 - Introduction to Git

## Workshop description
With this introduction to Git, we will go over the basics on Git and GitHub.  We will go over setting up a GitHub account, explaining basic commands like clone, add, and commit, setting up a repository on GitHub, and how to recover old versions of files.

You will not be an expert by the end of the class. You will probably not even feel very comfortable using Git. This is okay. We want to make a start but, as with any skill, using Git takes practice.

**Note**: This lesson is derived from the [Library Carpentries Introduction to Git](https://librarycarpentry.org/lc-git/) under the Creative Commons ([CC BY 4.0](https://creativecommons.org/licenses/by/4.0/))

## Setup
1. Create a free [GitHub](https://github.com/join) account and confirm your email.
2. Download and install Git for your operating system: [https://git-scm.com/downloads](https://git-scm.com/downloads) (Note: Git for Windows comes bundled with the Git BASH terminal that allows you to use UNIX-style commands on Windows)
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

```bash
$ git init
```

```console
Initialized empty Git repository in <your file path>/hello-world/.git/
```
The `hello-world` directory is now a git repository.
If we run the `ls` command now (`ls` lists the content of the `hello-world` directory), the repository might seem empty; however adding the `-a` flag for all files via `ls -a` will show all hidden files, which in this case includes the new hidden directory `.git`. Flags can simply be thought of as command options that can be added to shell commands.
Note that whenever we use git via the command line, we need to preface each command (or verb) with `git`, so that the computer knows we are trying to get git to do something, rather than some other program.

### Displaying the current project's status
We can run the `git status` command to display the current state of a project. Let's do that now.

```bash
$ git status
```

```console
On branch master
No commits yet
nothing to commit (create/copy files and use "git add" to track)
```
*Note*: Some versions of Git have named the default branch as "main" and not "master".
The output tells us that we are on the master branch (more on this later) and that we have nothing to commit (no unsaved changes).

### Adding and committing
We will now create and save our firsst project file. This is a two-stage process. First, we **add** any files for which we want to save the changes to a staging area, then we **commit** those changes to the repository. This two-stage process gives us fine-grained control over what should and should not be included in a particular commit.
Let's create a new file using the `touch` command, which is a quick way to create an empty file.

```bash
$ touch index.md
```
The `.md` extension above signifies that we have chosen to use the Markdown format, a lightweight markup language with plain text formatting syntax. We will explore Markdown a bit later.
Let's check the status of our project again.

```bash
$ git status
```

```console
On branch master
No commits yet
Untracked files:
  (use "git add <file>..." to include in what will be committed)

    index.md

nothing added to commit but untracked files present (use "git add" to track)
```
This status is telling us that Git has noticed a new file in our directory that we are not yet tracking. With colourized output, the filename will appear in red. To change this, and to tell Git we want to track any changes we make to `index.md`, we use `git add`.

```bash
$ git add index.md
```
This adds our Markdown file to the **staging area** (the area where Git checks for file changes). To confirm this we want to use `git status` again.

```bash
$ git status
```
```console
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

    new file:   index.md
```
If we are using colourised output, we will see that the filename has changed colour (from red to green). Git also tells us that there is a new file to be committed but, before we do that, let’s add some text to the file.
We will open the file `index.md` with any text editor we have at hand (e.g. Notepad on Windows or TextEdit on Mac OSX) and enter `# Hello, world!`. The hash character is one way of writing a header with Markdown. Now, let’s save the file within the text editor and check if Git has spotted the changes.

```bash
$ git status
```
```console
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

	new file:   index.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   index.md
```
This lets us know that git has indeed spotted the changes to our file, but that it hasn't yet staged them, so let's add the new version of the file to the staging area.

```bash
$ git add index.md
```
Now we are ready to *commit* our first changes. Commit is similar to ‘saving’ a file to Git. However, compared to saving, a commit provides a lot more information about the changes we have made, and this information will remain visible to us later.

```bash
$ git commit -m 'Add index.md'
```
```console
[master (root-commit) e9e8fd3] Add index.md
 1 file changed, 1 insertion(+)
 create mode 100644 index.md
```
We can see that one file has changed and that we made one insertion, which was a line with the text '#Hello, world!'. We can also see the commit message 'Add index.md', which we added by using the `-m` flag after `git commit`. The commit message is used to record a short, descriptive, and specific summary of what we did to help us remember later on without having to look at the actual changes. If we just run `git commit` without the `-m` option, Git will launch nano (or whatever other editor we configured as `core.editor`) so that we can write a longer message.

Having made a commit, we now have a permanent record of what was changed, along with metadata about who made the commit and at what time.

### More on the Staging Area
If you think of Git as taking snapshots of changes over the life of a project, `git add` specifies *what* will go in a snapshot (putting things in the staging area), and git commit then actually takes the snapshot, and makes a permanent record of it (as a commit). If you don’t have anything staged when you type `git commit`, Git will prompt you to use `git commit -a` or `git commit --all`, which is kind of like gathering *everyone* for the picture! However, it’s almost always better to explicitly add things to the staging area, because you might commit changes you forgot you made. (Going back to snapshots, you might get the extra with incomplete makeup walking on the stage for the snapshot because you used `-a`!) Try to stage things manually, or you might find yourself searching for "git undo commit" more than you would like!

![Staging image](git-staging-area.svg)

At the moment, our changes are only recorded locally, on our computer. If we wanted to work collaboratively with someone else they would have no way of seeing what we’ve done. We will fix that in the next episode by using GitHub to share our work.

### Key points for this section
* Git repositories contain metadata about files under version control.
* This metadata enables us to track changes to files over time.
* Git uses a two-stage commit process.  Changes to files must first be added to the stating area, then committed to the repository.

## Sharing your work

### Create a repository on GitHub
When we have logged in to GitHub, we can create a new repository by clicking the **+** icon in the upper-right corner of any page, then selecting **New repository**.  Let's do this now.
* Create a new repository
* Give it the name `hello-world`
GitHub will ask if you want to add a `README.md`, license or a `.gitignore` file. Do not do any of that for now.

#### Choosing a license
Choosing a license is an important part of openly sharing your creative work online. For help in wading through the many types of open source licenses, please visit [https://choosealicense.com/](https://choosealicense.com).

### Connecting your local repository to the GitHub repository

In the previous episode we created a local repository on our own computer. Now we have also created a remote repository on GitHub. But at this point, the two are completely isolated from each other. We want to link them together to synchronize them and share our project with the world.

To do this, we need the GitHub repository URL, which should look something like this (with “some-librarian” replaced with your username):

![GitHub setup image](repository-url.png)

If the URL starts with `git@` rather than `https://`, please click the “HTTPS” button to change it.

> HTTPS vs SSH
> We use HTTPS here because it does not require additional configuration, which vary from operating system to operating system. If you start using Git regularly, you would like to set up SSH access, which is a bit more secure and convenient, by following one of the great tutorials from [GitHub](https://help.github.com/articles/generating-ssh-keys), [Atlassian/BitBucket](https://confluence.atlassian.com/bitbucket/set-up-an-ssh-key-728138079.html) and [GitLab](https://about.gitlab.com/2014/03/04/add-ssh-key-screencast/) (this one has a screencast).

Notice that GitHub is actually helpful enough to provide instructions for us so we don't have to remember these commands:

![GitHub help](githubhelp.png)




