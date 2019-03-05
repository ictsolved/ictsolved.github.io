---
layout: post
title: "Getting Started with Git"
description: Git is a distributed Version Control System (VCS) which is used for tracking the source code during software development. It allows collaboration between the contributors and targets to maintain integrity, and support for distributed, non-linear workflows.
date: 2019-03-02 13:44:46
author: sarad
categories:
- blog
- Git
tags: Git tutorial for beginners, git clone, git remote, git setup
generes: Git
img: 2019-03-02-getting-started-with-git.png
imagealt: git tutorial
thumb: 2019-03-02-getting-started-with-git.png
redirect_from:
  - /blog/git/getting-started-with-git
---

Git is a distributed Version Control System (VCS) which is used for tracking the source code during software development. It allows collaboration between the contributors and targets to maintain integrity, and support for distributed, non-linear workflows. <!--more--> Let's get started.

>**Contents**
1. [Create your first repository, then add and commit files](#create-add-commit)
2. [Clone a repository](#clone-repository)
3. [Sharing code](#share-code)
4. [Setting your user name and email](#configure-user)
5. [Setting up the upstream remote](#setting-up-remote)
6. [Learning about a command](#help-command)
7. [Set up SSH for Git](#setup-ssh)
8. [Git Installation](#installation)
  * [Installing from Source](#installing-from-source)
  * [Installing on Mac](#installing-on-mac)
  * [Installing on Linux](#installing-on-linux)
  * [Installing on Windows](#installing-on-windows)

### <a class="anchor" name="create-add-commit"></a>Create your first repository, then add and commit files

At the command line, first verify that you have Git installed:

On all operating systems:

```
git --version
```
On UNIX-like operating systems:
```
which git
```
If nothing is returned, or the command is not recognized, you may have to install Git on your system. Jump to [Git Installation](#installation) section for instructions.

After installing Git, configure your username and email address. Do this *before* making a commit. Jump to [Setting your user name and email](#configure-user) section for instructions.

Once Git is installed and configured, navigate to the directory you want to place under version control and create an empty Git repository:

```
git init
```
This creates a hidden folder, *.git*, which contains the plumbing needed for Git to work.

Next, check what files Git will add to your new repository; this step is worth special care:

```
git status
```
Review the resulting list of files; you can tell Git which of the files to place into version control (avoid adding files with confidential information such as passwords, or files that just clutter the repo):

```
git add <file/directory name #1> <file/directory name #2> < ... >
```
If all files in the list should be shared with everyone who has access to the repository, a single command will add everything in your current directory and its subdirectories:

```
git add .
```
This will "stage" all files to be added to version control, preparing them to be committed in your first commit.

For files that you want never under version control, create and populate a file named .gitignore before running the add command.

Commit all the files that have been added, along with a commit message:

```
git commit -m "Initial commit"
```
This creates a new commit with the given message. A commit is like a save or snapshot of your entire project. You can now push, or upload, it to a remote repository, and later you can jump back to it if necessary. If you omit the -m parameter, your default editor will open and you can edit and save the commit message there.

**<u>Adding a remote</u>**

To add a new remote, use the **git remote add** command on the terminal, in the directory your repository is stored at.

The **git remote add** command takes two arguments:

1. A remote name, for example, origin
2. A remote URL, for example, https:**//<**your-git-service-address**>/**user**/**repo.git

```
git remote add origin https://<your-git-service-address>/owner/repository.git
```

NOTE: Before adding the remote you have to create the required repository in your git service, You'll be able to push/pull commits after adding your remote.

### <a class="anchor" name="clone-repository"></a>Clone a repository

The **git clone** command is used to copy an existing Git repository from a server to the local machine.

For example, to clone a GitHub project:

```
cd <path where you would like the clone to create a directory>
git clone https://github.com/username/projectname.git
```
To clone a BitBucket project:

```
cd <path where you would like the clone to create a directory>
git clone https://yourusername@bitbucket.org/username/projectname.git
```
This creates a directory called projectname on the local machine, containing all the files in the remote Git repository. This includes source files for the project, as well as a .git sub-directory which contains the entire history and configuration for the project.

To specify a different name of the directory, e.g. MyFolder:

```
git clone https://github.com/username/projectname.git MyFolder
```
Or to clone in the current directory:

```
git clone https://github.com/username/projectname.git .
```
Note:

1. When cloning to a specified directory, the directory must be empty or non-existent.
2. You can also use the **ssh** version of the command:

```
git clone git@github.com:username/projectname.git
```
The https version and the **ssh** version are equivalent. However, some hosting services such as GitHub [recommend](https://help.github.com/articles/set-up-git/#next-steps-authenticating-with-github-from-git){:target="_blank"} that you use https rather than **ssh**.

### <a class="anchor" name="share-code"></a>Sharing code

To share your code you create a repository on a remote server to which you will copy your local repository.

To minimize the use of space on the remote server you create a bare repository: one which has only the *.git* objects and doesn't create a working copy in the filesystem. As a bonus you set this remote as an upstream server to easily share updates with other programmers.

On the remote server:

```
git init --bare /path/to/repo.git
```
On the local machine:

```
git remote add origin ssh://username@server:/path/to/repo.git
```
(Note that *ssh:* is just one possible way of accessing the remote repository.)

Now copy your local repository to the remote:

```
git push --set-upstream origin master
```
Adding *--set-upstream* (or -u) created an upstream (tracking) reference which is used by argument-less Git commands, e.g. **git pull**.

### <a class="anchor" name="configure-user"></a>Setting your user name and email

You need to set who you are before creating any commit. That will allow commits to have the right author name and email associated to them.

It has nothing to do with authentication when pushing to a remote repository (e.g. when pushing to a remote repository using your GitHub, BitBucket, or GitLab account).

To declare that identity for all repositories, use **git config *-*-global**

This will store the setting in your user's *.gitconfig* file: e.g. $HOME**/**.gitconfig or for Windows, **%**USERPROFILE**%**\.gitconfig.

```
git config --global user.name "Your Name"
git config --global user.email mail@example.com
```
To declare an identity for a single repository, use **git config** inside a repo. This will store the setting inside the individual repository, in the file $GIT_DIR**/**config. e.g. **/**path**/**to**/**your**/**repo**/**.git**/**config.

```
cd /path/to/my/repo
git config user.name "Your Login At Work"
git config user.email mail_at_work@example.com
```
Settings stored in a repository's config file will take precedence over the global config when you use that repository.

Tips: if you have different identities (one for open-source project, one at work, one for private repos, ...), and you don't want to forget to set the right one for each different repos you are working on:

**<u>Remove a global identity</u>**
```
git config --global --remove-section user.name
git config --global --remove-section user.email
```
*Version ≥ 2.8*

To force git to look for your identity only within a repository's settings, not in the global config:

```
git config --global user.useConfigOnly true
```
That way, if you forget to set your user.name and user.email for a given repository and try to make a commit, you will see:


```
no name was given and auto-detection is disabled
no email was given and auto-detection is disabled
```
### <a class="anchor" name="setting-up-remote"></a>Setting up the upstream remote

If you have cloned a fork (e.g. an open source project on Github) you may not have push access to the upstream repository, so you need both your fork but be able to fetch the upstream repository.

First check the remote names:

```
$ git remote -v
origin https://github.com/myusername/repo.git (fetch)
origin https://github.com/myusername/repo.git (push)
upstream # this line may or may not be here
```
If upstream is there already (it is on _some_ Git versions) you need to set the URL (currently it's empty):

```
$ git remote set-url upstream https://github.com/projectusername/repo.git
```
If the upstream is not there, or if you also want to add a friend/colleague's fork (currently they do not exist):

```
$ git remote add upstream https://github.com/projectusername/repo.git
$ git remote add dave https://github.com/dave/repo.git
```
### <a class="anchor" name="help-command"></a>Learning about a command

To get more information about any git command – i.e. details about what the command does, available options and other documentation – use the *-*-help option or the **help** command.

For example, to get all available information about the **git diff** command, use:

```
git diff --help
git help diff
```
Similarly, to get all available information about the status command, use:

```
git status --help
git help status
```
If you only want a quick help showing you the meaning of the most used command line flags, use -h:

```
git checkout -h
```
### <a class="anchor" name="setup-ssh"></a>Set up SSH for Git

If you are using *Windows* open [Git Bash](https://git-for-windows.github.io/){:target="_blank"}. If you are using *Mac* or *Linux* open your Terminal.

Before you generate an SSH key, you can check to see if you have any existing SSH keys.

List the contents of your ~**/**.ssh directory:

```
$ ls -al ~/.ssh
# Lists all the files in your ~/.ssh directory
```

Check the directory listing to see if you already have a public SSH key. By default the filenames of the public keys are one of the following:

```
id_dsa.pub
id_ecdsa.pub
id_ed25519.pub
id_rsa.pub
```
If you see an existing public and private key pair listed that you would like to use on your Bitbucket, GitHub (or similar) account you can copy the contents of the id_*.pub file.

If not, you can create a new public and private key pair with the following command:

```
$ ssh-keygen
```
Press the Enter or Return key to accept the default location. Enter and re-enter a passphrase when prompted, or leave it empty.

Ensure your SSH key is added to the ssh-agent. Start the ssh-agent in the background if it's not already running:

```
$ eval "$(ssh-agent -s)"
```
Add you SSH key to the ssh-agent. Notice that you'll need te replace id_rsa in the command with the name of your

*private key file*:

```
$ ssh-add ~/.ssh/id_rsa
```
If you want to change the upstream of an existing repository from HTTPS to SSH you can run the following command:

```
$ git remote set-url origin ssh://git@bitbucket.server.com:7999/projects/your_project.git
```
In order to clone a new repository over SSH you can run the following command:

```
$ git clone ssh://git@bitbucket.server.com:7999/projects/your_project.git
```
### <a class="anchor" name="installation"></a>Git Installation

Let’s get into using some Git. First things first—you have to install it. You can get it a number of ways; the two major ones are to install it from source or to install an existing package for your platform.

**<u><a class="anchor" name="installing-from-source"></a>Installing from Source</u>**

If you can, it’s generally useful to install Git from source, because you’ll get the most recent version. Each version of Git tends to include useful UI enhancements, so getting the latest version is often the best route if you feel comfortable compiling software from source. It is also the case that many Linux distributions contain very old packages; so unless you’re on a very up-to-date distro or are using backports, installing from source may be the best bet.

To install Git, you need to have the following libraries that Git depends on: curl, zlib, openssl, expat, and libiconv. For example, if you’re on a system that has yum (such as Fedora) or apt-get (such as a Debian based system), you can use one of these commands to install all of the dependencies:

```
$ yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel
```
```
$ apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev
```
When you have all the necessary dependencies, you can go ahead and grab the latest snapshot from the Git web site:

[http://git-scm.com/download](http://git-scm.com/download){:target="_blank"} Then, compile and install:

```
$ tar -zxf git-1.7.2.2.tar.gz
$ cd git-1.7.2.2
$ make prefix=/usr/local all
$ sudo make prefix=/usr/local install
```
After this is done, you can also get Git via Git itself for updates:

```
$ git clone git://git.kernel.org/pub/scm/git/git.git
```
**<u><a class="anchor" name="installing-on-linux"></a>Installing on Linux</u>**

If you want to install Git on Linux via a binary installer, you can generally do so through the basic package-management tool that comes with your distribution. If you’re on Fedora, you can use yum:

```
$ yum install git
```
Or if you’re on a Debian-based distribution like Ubuntu, try apt-get:

```
$ apt install git
```
**<u><a class="anchor" name="installing-on-mac"></a>Installing on Mac</u>**

There are three easy ways to install Git on a Mac. The easiest is to use the graphical Git installer, which you can download from the SourceForge page. [http://sourceforge.net/projects/git-osx-installer/](http://sourceforge.net/projects/git-osx-installer/){:target="_blank"}

Figure 1-7. Git OS X installer. The other major way is to install Git via MacPorts [http://www.macports.org](http://www.macports.org){:target="_blank"}. If you have MacPorts installed, install Git via

```
$ sudo port install git +svn +doc +bash_completion +gitweb
```
You don’t have to add all the extras, but you’ll probably want to include +svn in case you ever have to use Git with Subversion repositories (see Chapter 8).

Homebrew [http://brew.sh/](http://brew.sh/){:target="_blank"} is another alternative to install Git. If you have Homebrew installed, install Git via

```
$ brew install git
```
**<u><a class="anchor" name="installing-on-windows"></a>Installing on Windows</u>**

Installing Git on Windows is very easy. The msysGit project has one of the easier installation procedures. Simply download the installer exe file from the GitHub page, and run it: [http://msysgit.github.io](http://msysgit.github.io){:target="_blank"}


After it’s installed, you have both a command-line version (including an SSH client that will come in handy later) and the standard GUI.

*Note on Windows usage:* you should use Git with the provided msysGit shell (Unix style), it allows to use the complex lines of command given in this book. If you need, for some reason, to use the native Windows shell / command line console, you have to use double quotes instead of single quotes (for parameters with spaces in them) and you must quote the parameters ending with the circumflex accent (^) if they are last on the line, as it is a continuation symbol in Windows.

>*This article is compiled from the original Stack Overflow Documentation released under [CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/){:target="_blank"} and created by these contributors: [Ala Eddine JEBALI](https://stackoverflow.com/users/1343790/){:target="_blank"}, [Allan Burleson](https://stackoverflow.com/users/5703771/){:target="_blank"}, [Craig Brett](https://stackoverflow.com/users/718940/){:target="_blank"}, [Dan Hulme](https://stackoverflow.com/users/967945/){:target="_blank"}, [eykanal](https://stackoverflow.com/users/168775/){:target="_blank"}, [Henrique Barcelos](https://stackoverflow.com/users/1798341/){:target="_blank"}, [Jonathan Lam](https://stackoverflow.com/users/2397327/){:target="_blank"}, [Kageetai](https://stackoverflow.com/users/1159510/){:target="_blank"}, [maccard](https://stackoverflow.com/users/723918/){:target="_blank"}, [ob1](https://stackoverflow.com/users/8168719/){:target="_blank"}, [Roald Nefs](https://stackoverflow.com/users/4779556/){:target="_blank"}, [ronnyfm](https://stackoverflow.com/users/204968/){:target="_blank"}, [Sazzad Hissain Khan](https://stackoverflow.com/users/1084174/){:target="_blank"}, [Tyler Zika](https://stackoverflow.com/users/1086315/){:target="_blank"}, [tymspy](https://stackoverflow.com/users/3029163/){:target="_blank"}. This website is not affiliated with [Stack Overflow](https://stackoverflow.com/){:target="_blank"}. For corrections or feedback comment below or email to <a href="mailto:ictsimplified@gmail.com?Subject=Feedback on Getting Started with Github" target="_top">ictsimplified@gmail.com</a>*

