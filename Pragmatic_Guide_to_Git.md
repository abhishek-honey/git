# Pragmatic Guide to Git

* [1. Getting Started](#1-getting-started)
	* [Task 1. Installing Git](#task-1-installing-git)
	* [Task 2. Configuring Git](#task-2-configuring-git)
	* [Task 3. Creating a New Repository](#task-3-creating-a-new-repository)
	* [Task 4. Creating a Local Copy of an Existing Repository](#task-4-creating-a-local-copy-of-an-existing-repository)


* [2. Working with Git](#2-working-with-git)
	* [Task 5. Seeing What Has Changed](#task-5-seeing-what-has-changed)
	* [Task 6. Staging Changes to Commit](#task-6-staging-changes-to-commit)
	* [Task 7. Committing Changes](#task-7-committing-changes)
	* [Task 8. Ignoring Files](#task-8-ignoring-files)
	* [Task 9. Undoing Uncommitted Changes](#task-9-undoing-uncommitted-changes)
	* [Task 10. Moving Files in Git](#task-10-moving-files-in-git)
	* [Task 11. Deleting Files in Git](#task-11-deleting-files-in-git)
	* [Task 12. Sharing Changes](#task-12-sharing-changes)


* [3. Organizing Your Repository with Branches and Tags](#3-organizing-your-repository-with-branches-and-tags)
	* [Task 13. Creating and Switching Branches](#task-13-creating-and-switching-branches)
	* [Task 14. Viewing Branches](#task-14-viewing-branches)
	* [Task 15. Merging Commits Between Branches](#task-15-merging-commits-between-branches)
	* [Task 16. Rewriting History by Rebasing](#task-16-rewriting-history-by-rebasing)
	* [Task 17. Deleting Branches](#task-17-deleting-branches)
	* [Task 18. Tagging Milestones](#task-18-tagging-milestones)


* [4. Working with a Team](#4-working-with-a-team)
	* [Task 19. Adding and Removing Remotes](#task-19-adding-and-removing-remotes)
	* [Task 20. Retrieving Remote Changes](#task-20-retrieving-remote-changes)
	* [Task 21. Retrieving Remote Changes, Part II](#task-21-retrieving-remote-changes-part-II)
	* [Task 22. Sending Changes to Remotes](#task-22-sending-changes-to-remotes)
	* [Task 23. Handling Remote Tags and Branches](#task-23-handling-remote-tags-and-branches)


* [5. Branches and Merging Revisited](#5-branches-and-merging-revisited)
	* [Task 24. Handling Conflicts](#task-24-handling-conflicts)
	* [Task 25. Handling Conflicts with a GUI](#task-25-handling-conflicts-with-a-gui)
	* [Task 26. Temporarily Hiding Changes](#task-26-temporarily-hiding-changes)
	* [Task 27. Cherry-Picking Commits](#task-27-cherry-picking-commits)
	* [Task 28. Controlling How You Replay Commits](#task-28-controlling-how-you-replay-commits)
	* [Task 29. Moving Branches](#task-29-moving-branches)


* [6. Working with the Repository’s History](#6-working-with-the-repositorys-history)
	* [Task 30. Viewing the Log](#task-30-viewing-the-log)
	* [Task 31. Filtering the Log Output](#task-31-filtering-the-log-output)
	* [Task 32. Comparing Differences](#task-32-comparing-differences)
	* [Task 33. Generating Statistics About Changes](#task-33-generating-statistics-about-changes)
	* [Task 34. Assigning Blame](#task-34-assigning-blame)


* [7. Fixing Things](#7-fixing-things)
	* [Task 35. Fixing Commits](#ask-35-fixing-commits)
	* [Task 36. Reverting Commits](#task-36-reverting-commits)
	* [Task 37. Resetting Staged Changes and Commits](#task-37-resetting-staged-changes-and-commits)
	* [Task 38. Erasing Commits](#task-38-erasing-commits)
	* [Task 39. Finding Bugs with bisect](#task-39-finding-bugs-with-bisect)
	* [Task 40. Retrieving “Lost” Commits](#task-40-retrieving-lost-commits)


* [8. Moving Beyond the Basics](#8-moving-beyond-the-basics)
	* [Task 41 Exporting Your Repository](#task-41-exporting-your-repository)
	* [Task 42 Doing Some Git Housekeeping](#task-42-doing-some-git-housekeeping)
	* [Task 43 Syncing with Subversion](#task-43-syncing-with-subversion)
	* [Task 44 Initializing Bare Repositories](#task-44-initializing-bare-repositories)


* [9. Glossary](#glossary)

## 1. Getting Started

The Git Workflow
Working by yourself on a project with no version control, you hack a little, test it out and see whether it does what you want, tweak a few more lines of code, and repeat. Adding version control into the mix, you start committing those tweaks to keep a record of them.

1.	Fetch Changes from the Team (Start your day here:sunrise:)
2.	Share Changes with the Team:couple:
3.	Make Changes & Commit Them (repeat until done :repeat:)
4.	Review Commits

I fetch all the changes from the other developers on my team to make sure I’m working with the latest code, and then I start working on the user stories I have for the day. As I make changes, I create a handful of commits—a separate commit for each change that I make.

Occasionally, I end up with several separate changes that all need to be com- mitted. I’ll break out Git’s patch mode, stage, and finally commit each set of changes separately.

Once I have the feature complete, I give the commits I’ve created a quick review to make sure all the changes are necessary. At this point I look for commits that can be combined and make sure they are in the most logical order.

Finally, once I have those commits ready, I share those commits by pushing them (push is the term for sending commits to another repository) back upstream to my public repository so the rest of the team can view them and integrate them with their repositories.

#### Repository Layouts
* One method is the fully distributed model. In this, each developer has their own public repository that the developer uses to publish their changes to. All the other developers on the team then pull changes from everyone else’s repositories to keep current.
* In practice, most teams have a lead developer who is responsible for making sure all the changes are integrated. This limits the number of repositories you and your team have to pull changes from to one, but it increases the workload on the person who has to integrate everyone’s changes.
* Another method is the shared repository model, where all developers can push to a shared repository. This resembles the standard centralized model and is often adopted by teams when they first start using Git—it requires the least amount of mental overhead when it comes to thinking about where a change is shared.
* You can mix both of these as well to create a hybrid solution. Use a shared repository for all of the code that’s ready for production, and each developer maintains their own public repository for sharing code that’s still a work in progress.

### Task 1. Installing Git

* __Mac__
	*	Download the latest Git for Mac installer.

	Follow the prompts to install Git.

	Open a terminal and verify the installation was successful by typing ```git --version```:

	```bash
	(base) Honeys-Air:git apple$ git version
	git version 2.21.0
	```

	*	Install Git with Homebrew
	```bash
	(base) Honeys-Air:git apple$ brew install git

	# After installation
	(base) Honeys-Air:git apple$ git version
	git version 2.21.0
	```

* __Windows__

	*	Download the latest Git for Windows installer.

	When you've successfully started the installer, you should see the Git Setup wizard screen. Follow the Next and Finish prompts to complete the installation. The default options are pretty sensible for most users.

	Open a Command Prompt (or Git Bash if during installation you elected not to use Git from the Windows Command Prompt).
	```Bash
	$ git --version
  git version 2.9.2
	```
* __Linux__

	*	__Debian / Ubuntu (apt-get)__

		From your shell, install Git using apt-get:
		```bash
		$ sudo apt-get update
		$ sudo apt-get install git

		# After installation
		$ git --version
		git version 2.9.2
		```
	* __Fedora (dnf/yum)__

		From your shell, install Git using dnf (or yum, on older versions of Fedora):
		```Bash
		$ sudo dnf install git
		or
		$ sudo yum install git

		# After installation
		$ git --version
		git version 2.9.2
		```

If you face any problem while installation or you are using some other operating system, please google, most probably somebody has already answered 😂 , the earth is quite big!😉

If you have successfully installed git, its __50％__ done, so now you deserve to rest🥱, after doing the configuration and making a github account with a repository its __95%__ done.🥳
### Task 2. Configuring Git
Create a github account by Signing up to github, it is just like signing up for some other websites.
*	Remember user name
* Remember email id

Git requires some configuration to work. You must tell Git your name and your email address since there is no central repository to keep track of that information.

Git uses both to calculate the commit ID—an SHA-111 hash—that identifies each commit.

```Bash

(base) Honeys-Air:git apple$ git config --global user.name "github_user_name"
(base) Honeys-Air:git apple$ git config --global user.email "github_email_id"

# Git user for specific repository

(base) Honeys-Air:git apple$ cd /path/to/repository
(base) Honeys-Air:repository apple$ git config user.name "github_user_name"
(base) Honeys-Air:repository apple$ git config user.email "github_email_id"

# Colors whenever possible

(base) Honeys-Air:git apple$ git config --global color.ui auto
```

There are many other useful configuration, do google some🔎

Some links
* [Git config file example](https://gist.github.com/pksunkara/988716).
* [Official git config.](https://git-scm.com/docs/git-config)

### Task 3. Creating a New Repository

Create a new directory ```git``` on your local machine.

Create a new project named ```git``` on github with default options, using your new github account.

After creating a new github account, github will give some default commands that we can simply copy paste on terminal.

```Bash
(base) Honeys-Air:git apple$ mkdir git
(base) Honeys-Air:git apple$ cd git

# Copy paste the commands that github provided.
(base) Honeys-Air:git apple$ echo "# git" >> README.md
(base) Honeys-Air:git apple$ git init
(base) Honeys-Air:git apple$ git add README.md
(base) Honeys-Air:git apple$ git commit -m "first commit"
(base) Honeys-Air:git apple$ git remote add origin https://github.com/abhishek-honey/git.git
(base) Honeys-Air:git apple$ git push -u origin master
```

To create a repository inside an existing directory called /work/existing-widget, use this: ```Same as above with a little twist```

```Bash
(base) Honeys-Air:some-other--dir apple$ cd /work/existing-widget
(base) Honeys-Air:existing-widget apple$ git init
Initialized empty Git repository in /work/existing-widget/.git/
(base) Honeys-Air:existing-widget apple$ git add .
(base) Honeys-Air:existing-widget apple$ git commit -m "initial commit"
[master (root-commit) 6e477fa] initial commit
101 files changed, 4083 insertions(+), 0 deletions(-) create mode 100644 AUTHORS
... and 100 more files ...
```

After that same make a github repository with the same name and push it to the ```origin master```

Hurray... __90%__ done. Now 1 more thing to __95%__


Related Tasks
* [Task 4. Creating a Local Copy of an Existing Repository](#task-4-creating-a-local-copy-of-an-existing-repository)
* [Task 7. Committing Changes](#task-7-committing-changes)
* [Task 12. Sharing Changes](#task-12-sharing-changes)
* [Task 44 Initializing Bare Repositories](#task-44-initializing-bare-repositories)

### Task 4. Creating a Local Copy of an Existing Repository

The ```git clone``` command initializes a new repository on your computer and fetches the entire history—all the changes that have been tracked during the life of that repository.

```Bash
(base) Honeys-Air:tmp apple$ git clone https://github.com/abhishek-honey/git
Cloning into 'git'...
remote: Enumerating objects: 14, done.
remote: Counting objects: 100% (14/14), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 14 (delta 3), reused 13 (delta 2), pack-reused 0
Unpacking objects: 100% (14/14), done.
```
Sometimes you don’t need the entire history of the repository. You don’t always need the last ten years of changes—the last year’s might suffice. You can use the ```--depth``` parameter to limit how many revisions you fetch. This is called a ```shallow repository```.

There are a few limitations to this type of repository clone. *For example, you can’t create another clone from it.*

```Bash
(base) Honeys-Air:tmp apple$ git clone --depth 50 https://github.com/abhishek-honey/git
Cloning into 'git'...
remote: Enumerating objects: 14, done.
remote: Counting objects: 100% (14/14), done.
remote: Compressing objects: 100% (8/8), done.
remote: Total 14 (delta 3), reused 13 (delta 2), pack-reused 0
Unpacking objects: 100% (14/14), done.
```

Related Tasks
* [Task 3. Creating a New Repository](#task-3-creating-a-new-repository)
* [Task 12. Sharing Changes](#task-12-sharing-changes)
* [Task 19. Adding and Removing Remotes](#task-19-adding-and-removing-remotes)

__95%__ done, so now you have got super power of creating your own repository on github, and you can also clone other's repository.

😎🥳😎

## 2. Working with Git

Now that you have Git and your repository set up, it’s time to start learning how to interact with Git. A handful of commands are all you need to get you through most tasks. Once you finish the tasks in this part, you’ll know them all. __99.9%__

The workflow goes like this. First, create your repositor, either create a new repository or clone an existing one. Then make some changes, test that they do what you want, commit those changes, make some more changes, and so on. Finally, you share those changes when they’re ready.

Lots of small, discrete changes that touch very specific portions of the code are better than a few monolithic changes. Make sure you don’t sit on a whole bunch of changes until they’re perfect. First, they’ll never be perfect. There’s always something else to refactor and abstract away. Second, the bigger the change becomes, the harder it becomes to fully understand, review, and test.

### Task 5. Seeing What Has Changed

The ```git status``` has several different outputs, depending on what’s in your working tree.

It contains all three types of outputs: staged changes, changes to known files, and untracked files.

```Bash
(base) Honeys-Air:git apple$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	modified:   Pragmatic_Guide_to_Git.md

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   Pragmatic_Guide_to_Git.md

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	images/
	project/
```
So, to understand this imagine that in some multiverse there is a group of 5 friends.
1.	Amit
2.	Honey
3.	Raj
4.	Angel
5.	Payal

So, they all decided to take a group photo, on the stage, by a camera-man.

So, this is the current  ```status```. They all are ```Untracked files:```

```Bash
(base) Honeys-Air:git apple$ git status
On branch master
Your branch is up to date with 'origin/master'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	project/amit
	project/angel
	project/honey
	project/payal
	project/raj

nothing added to commit but untracked files present (use "git add" to track)
```
Now, that it is decided that they will take a photo, so camera-man told ok, lets move to the staging area, for that we do ```git add *```
```Bash
(base) Honeys-Air:git apple$ git add *
(base) Honeys-Air:git apple$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   project/amit
	new file:   project/angel
	new file:   project/honey
	new file:   project/payal
	new file:   project/raj

(base) Honeys-Air:git apple$
```
Now see the status, all of them are in ```Changes to be committed:```

Now, Angel forgot her fancy glasses, so she asks honey to bring her the glasses, and yes he will bring the glasses as angel has asked.
😄😂😄

Here you can write ```bringing the glasses in``` honey

Lets see the ```status```

```Bash
(base) Honeys-Air:git apple$ echo "bringing the glasses" >> project/honey
(base) Honeys-Air:git apple$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   project/amit
	new file:   project/angel
	new file:   project/honey
	new file:   project/payal
	new file:   project/raj

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   project/honey
```

Here we can see honey is present in two places, and it is not because honey has some super power, it is because in this multiverse this is a universal law, that if a camera-man has already asked someone to be in staging area and if they move out of the the staging area i.e something has changed, in that case the person will be present in 2 places.
1.	Changes to be committed:
2.	Changes not staged for commit:

Now one of Angel's friend also came Riya. i.e one file got added.

Lets see the status.
```Bash
(base) Honeys-Air:echo "Riya" > project/riya
(base) Honeys-Air:git apple$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   project/amit
	new file:   project/angel
	new file:   project/honey
	new file:   project/payal
	new file:   project/raj

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   project/honey

Untracked files:
  (use "git add <file>..." to include in what will be committed)

	project/riya
```
So now riya is ```Untracked files``` and honey is ```Changes not staged for commit``` and ```Changes to be committed:```. and others are ```Changes to be committed```
as they are already in staging area, so now lets add riya and honey in the staging area and see the status.

```Bash
(base) Honeys-Air:git apple$ git add *
(base) Honeys-Air:git apple$ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   project/amit
	new file:   project/angel
	new file:   project/honey
	new file:   project/payal
	new file:   project/raj
	new file:   project/riya
```
Now for taking the photo we use ```git commit -m "Take a photo"```

Hope you remember this story of ```git multiverse```, whenever you work with git.


Related Tasks
* [Task 3. Creating a New Repository](#task-3-creating-a-new-repository)
* [Task 6. Staging Changes to Commit](#task-6-staging-changes-to-commit)
* [Task 7. Committing Changes](#task-7-committing-changes)

### Task 6. Staging Changes to Commit
Git uses a two-step process to get changes into the repository. The first step is staging changes through git add. Staging a change adds it to the index, or staging area. This sits between the working tree—your view of the repository—and the actual repository.

Through the staging area, you can control what is staged from the most coarse-grained—adding everything within the repository—down to editing the changes, line by line.

It uses standard shell-style wildcards, so wildcards work: base.* matches base.rb and base.py.

You can control which parts of a file you commit using the ```-p ```parameter. Running this, you’re presented with each section of the file that has changed, and you’re given the opportunity to add or skip it. You can stage the change by pressing y or skip a change with n. s lets you break the change into smaller pieces. This and a few other options aren’t always available. You can press ? inside patch mode to get a list of all the commands and what they do.

Taking the control a step further, you can directly edit the changes that are being staged by using the ```-e``` parameter.

```Bash
#Add all files in the current repository.
(base) Honeys-Air:git apple$ git add -A
(base) Honeys-Air:git apple$ git add *

# Add all tracked files that have been changed.
(base) Honeys-Air:git apple$ git add -u

# -p option
git add -p
diff --git a/README.md b/README.md
index 96546e3..737df2f 100644
--- a/README.md
+++ b/README.md
@@ -3,6 +3,7 @@
 * Pro Git

 # Pragmatic Guide to Git
+[Notes](Pragmatic_Guide_to_Git.md)
 ## 1. Getting Started
 * Task 1. Installing Git
 * Task 2. Configuring Git
Stage this hunk [y,n,q,a,d,j,J,g,/,e,?]? y
@@ -64,6 +65,7 @@
 * Task 44. Initializing Bare Repositories

 # Pro Git
+[Notes](Pro_git.md)
 * __In Chapter 1__, we’re going to cover Version Control Systems (VCSs) and Git basics — no technical stuff, just what Git is, why it came about in a land full of VCSs, what sets it apart, and why so many people are using it. Then, we’ll explain how to download Git and set it up for the first time you don’t already have it on your system.
 * __In Chapter 2__, we will go over basic Git usage — how to use Git in the 80% of cases you’ll encounter most often. After reading this chapter, you should be able to clone a repository, see what has happened in the history of the project, modify files, and contribute changes. If the book spontaneously combusts at this point, you should already be pretty useful wielding Git in the time it takes you to go pick up another copy.
 * __Chapter 3__ is about the branching model in Git, often described as Git’s killer feature. Here you’ll learn what truly sets Git apart from the pack. When you’re done, you may feel the need to spend a quiet moment pondering how you lived before Git branching was part of your life.
Stage this hunk [y,n,q,a,d,K,g,/,e,?]? y
```

Related Tasks
* [Task 5. Seeing What Has Changed](#task-5-seeing-what-has-changed)
* [Task 7. Committing Changes](#task-7-committing-changes)



### Task 7. Committing Changes
Git tracks changes to your repository through commits, which you make with the ```git commit``` command.

Prior to most commits, you need to stage the files you want to commit using the ```git add```.

Each commit requires a commit message. You can use ```-m``` and a string in quotation marks as your message or use Git’s editor to write a message.

You can avoid git add and commit every change in your working tree with the ```-a``` parameter. It commits everything you have staged and all the changes to your working tree.

```Bash
# Commit Changes
(base) Honeys-MacBook-Air:git apple$ git commit -m "Addded multiverse functionality"
[master 9733860] Addded multiverse functionality
 1 file changed, 12 insertions(+), 2 deletions(-)

# Commit all modified files.
(base) Honeys-MacBook-Air:git apple$ git commit -m "Addded multiverse functionality" -a
[master 896d69c] Addded multiverse functionality
 1 file changed, 12 insertions(+), 2 deletions(-)

# Commit and launch editor for commit message.
(base) Honeys-MacBook-Air:git apple$ git commit
```

Related Tasks
* [Task 5. Seeing What Has Changed](#task-5-seeing-what-has-changed)
* [Task 6. Staging Changes to Commit](#task-6-staging-changes-to-commit)
* [Task 12. Sharing Changes](#task-12-sharing-changes)
* [Task 35. Fixing Commits](#ask-35-fixing-commits)

### Task 8. Ignoring Files

Software projects generate a lot of cruft. We don’t need or want some files cluttering up our repository or showing up in git status. That’s where the .gitignore and friends comes in.

Each line of the ```.gitignore``` is scanned, and any matches it finds are ignored by Git. Your ```.gitignore``` file is inside your repository, so you can track it like any other file. You can put it at the top level of your repository, and in that case the rules cascade through all subdirectories. You can also use subdirectory-specific ```.gitignore```, and those rules will only apply to files and directories inside that subdirectory.

Sometimes you don’t want to commit your ```.gitignore``` file to your repository. Maybe you’re be contributing to an open source project—there’s no need to add your unwanted files to the project-wide ```.gitignore```. You have two options in this case: use the ```.git/info/excludes``` file or add the ignore cases to your global excludesfile.

The __.git/info/excludes__ is the same as a ```.gitignore``` file, except it’s not tracked by Git since it’s inside the .git directory. It’s useful for excluding files that are specific to a project without adding a ```.gitignore``` file to the repository.

[Official gitignore docs](https://git-scm.com/docs/gitignore)


### Task 9. Undoing Uncommitted Changes
Git’s two-step process for tracking a commit means you can have files that are staged for commit that you’re not ready to commit. You use git reset HEAD or ```git rm --cached``` depending on the circumstance.

* Scenario 1: __You staged a change to file and want to unstage it—use__ ```git reset HEAD```. This is the most common use. You’re telling Git, “Change the index—the staging area—to the latest version of this file.”

* Scenario 2: __You have a new file that’s been staged that you don’t want to commit now—use__ ```git rm --cached```. Normally, ```git rm``` is used to remove files from your repository, but adding the ```--cached``` option tells Git to leave your working tree alone.

* Another common problem is making changes that you want to __undo completely.__ You can use ```git checkout``` to do this, but be careful. __git checkout happily removes all untracked changes from a file or directory. You can’t get those changes back if they were never tracked by Git.__

Related Tasks

* [Task 36. Reverting Commits](#task-36-reverting-commits)
* [Task 37. Resetting Staged Changes and Commits](#task-37-resetting-staged-changes-and-commits)


### Task 10. Moving Files in Git

Performing tasks such as reorganizing files, changing file formats, and so on, requires that files and sometimes entire directories get moved. git mv handles this for you.

 The ```git mv``` won’t overwrite an existing file; it displays an error instead. You can override this behavior by providing ```--force (or -f)```. __Be careful, though, because this makes Git overwrite the existing file. That’s dangerous if the existing file you’re overwriting isn’t tracked by Git. You have no way of getting that file back.__

```Bash

(base) Honeys-MacBook-Air:git apple$ git mv project/honey project/mv/honey
(base) Honeys-MacBook-Air:git apple$ tree
.
├── Pragmatic_Guide_to_Git.md
├── Pro_git.md
├── README.md
├── images
│   ├── github_1.jpeg
│   └── github_2.jpeg
└── project
    ├── amit
    ├── angel
    ├── foo.txt
    ├── hello.txt
    ├── mv
    │   └── honey
    ├── payal
    ├── raj
    └── riya

3 directories, 13 files

# Second example

(base) Honeys-MacBook-Air:git apple$ git mv project/mv/honey project/mv/honeyDifferentMultiverse
(base) Honeys-MacBook-Air:git apple$ tree
.
├── Pragmatic_Guide_to_Git.md
├── Pro_git.md
├── README.md
├── images
│   ├── github_1.jpeg
│   └── github_2.jpeg
└── project
    ├── amit
    ├── angel
    ├── foo.txt
    ├── hello.txt
    ├── mv
    │   └── honeyDifferentMultiverse
    ├── payal
    ├── raj
    └── riya

3 directories, 13 files

```

### Task 11. Deleting Files in Git

Files and directories sometimes outlive their usefulness. You can remove them from your working tree and tell Git to quit tracking them using the ```git rm``` command.

__This doesn’t remove the file from your repository’s history__; it removes it only from your working tree going forward. You can always go back in the history of the repository and see the files or directories that have been removed.

You call ```git rm``` and provide it with a filename to tell Git to remove it. Regex also works

You must provide the ```-r``` option if you are deleting a directory and all the files under it. It tells Git to recursively delete all the files starting at the provided directory.

Like most other actions in Git, ```git rm``` requires git commit to finalize its action. git rm stages the removal, and git commit finalizes it.

```Bash
(base) Honeys-MacBook-Air:git apple$ git rm -- outdated.py
(base) Honeys-MacBook-Air:git apple$ git rm -r -- old/
(base) Honeys-MacBook-Air:git apple$ git commit -m "remove the old/ directory"


# Get a directory back after deleting it but before committing it.
# This example uses the previous example where old/ is deleted using git rm, but before the staged deletes are committed. There are two steps. First, reset the index:

(base) Honeys-MacBook-Air:git apple$ git reset HEAD -- old/ Unstaged changes after reset: M old/outdated.py
# Second, check out the files from the repository:
(base) Honeys-MacBook-Air:git apple$ git checkout -- old/

# Force a file to be removed.
(base) Honeys-MacBook-Air:git apple$ git rm -f -- outdated.py rm 'outdated.py'
```

Related Tasks

* [Task 9. Undoing Uncommitted Changes](#task-9-undoing-uncommitted-changes)
* [Task 10. Moving Files in Git](#task-10-moving-files-in-git)

### Task 12. Sharing Changes

Remember that Git is different from most traditional version control systems; committing a change and sharing that change are two distinct tasks. Committing changes is covered in detail in [Task 7. Committing Changes](#task-7-committing-changes)

Sending changes back to a remote repository to share is done via the git push command. Consider it the inverse of git pull; it sends your changes to the remote repository and merges those changes into the remote branch via a fast-forward merge, which is a merge where both branches share a common ancestor and only the branch being merged in has changes in it.

```Bash

(base) Honeys-MacBook-Air:git apple$ git push <remote name> <branch name>
```

* [Task 4. Creating a Local Copy of an Existing Repository](#task-4-creating-a-local-copy-of-an-existing-repository)
* [Task 7. Committing Changes](#task-7-committing-changes)
* [Task 19. Adding and Removing Remotes](#task-19-adding-and-removing-remotes)
* [Task 20. Retrieving Remote Changes](#task-20-retrieving-remote-changes)
* [Task 21. Retrieving Remote Changes, Part II](#task-21-retrieving-remote-changes-part-II)
* [Task 22. Sending Changes to Remotes](#task-22-sending-changes-to-remotes)

## 3. Organizing Your Repository with Branches and Tags
### Task 13. Creating and Switching Branches

Git’s convention is to treat the master branch as its main line of code. You can rename it to anything you want, but it’s a good idea to keep with the convention.

You can also create branches starting at points in the history of the repository. Provide git branch with the name of the new branch you want to create followed by the commit ID or branch or tag name to create a branch at that point.

Creating a new branch and checking it out immediately is common in Git. You can do both actions with one command: git checkout -b. Like git branch, it requires at least one parameter—the name of the new branch—and takes an optional second parameter specifying the point to create it from.

```bash
➜  git git:(master) git branch
* master

➜  git git:(master)
➜  git git:(master)
➜  git git:(master) git branch feature_learn_branches
➜  git git:(master)
➜  git git:(master)
➜  git git:(master) git checkout feature_learn_branches
Switched to branch 'feature_learn_branches'
➜  git git:(feature_learn_branches)
```


### Task 14. Viewing Branches







### Task 15. Merging Commits Between Branches






### Task 16. Rewriting History by Rebasing







### Task 17. Deleting Branches






### Task 18. Tagging Milestones

## 4. Working with a Team
### Task 19. Adding and Removing Remotes






### Task 20. Retrieving Remote Changes





### Task 21. Retrieving Remote Changes, Part II




### Task 22. Sending Changes to Remotes






### Task 23. Handling Remote Tags and Branches

## 5. Branches and Merging Revisited
### Task 24. Handling Conflicts








### Task 25. Handling Conflicts with a GUI








### Task 26. Temporarily Hiding Changes







### Task 27. Cherry Picking Commits










### Task 28. Controlling How You Replay Commits









### Task 29. Moving Branches

## 6. Working with the Repository’s History
### Task 30. Viewing the Log










### Task 31. Filtering the Log Output











### Task 32. Comparing Differences











### Task 33. Generating Statistics About Changes












### Task 34. Assigning Blame











## 7. Fixing Things
### Task 35. Fixing Commits







### Task 36. Reverting Commits










### Task 37. Resetting Staged Changes and Commits










### Task 38. Erasing Commits













### Task 39. Finding Bugs with bisect













### Task 40. Retrieving “Lost” Commits

## 8. Moving Beyond the Basics
### Task 41. Exporting Your Repository












### Task 42. Doing Some Git Housekeeping














### Task 43. Syncing with Subversion












### Task 44. Initializing Bare Repositories


### Glossary

* __^__: Adding a caret to any commit name (a commit ID, branch name, or tag) tells Git to use that commit, minus one. You can add multiple carets: HEAD^^ means HEAD minus two, and so on.
* __~#__: The tilde followed by a number is used with a commit name (a commit ID, branch name, or tag) to specify the commit located at that point minus the number__: HEAD~2 means two commits before HEAD, and so on.
* __amend__: Applies the commit that is being made to the previous commit to amend it.
* __bare repository__: A repository without a working tree. Generally used for repositories that are meant to be pushed and pulled to and from.
* __blame__:Anannotatedviewofafile(orportionofafile)thatshowswhat commit a change was made in, when that commit happened, and who made it.
* __branch__: A separate line of history within the repository stored as a pointer to a particular commit.
* __check out or checkout__: The act of taking a branch or files from the repository and checking it out into the working tree.
* __cherry-pick__: Taking one commit and applying it to the current branch.
* __commit__:Theindividualpointsintimethatyourrepositorytracks.Each commit in Git tracks who made it, when it was made, the changes that were made, and what commit (or commits) are its direct parents.
* __commitID__:TheIDforeachcommitisanSHA-1hashbasedonthedata that makes up a commit. Any change to the commit causes a different commit ID to be generated. Each commit provides its own integrity check through its ID.
* __commit message__: A plain-text message that is stored with the commit. It is used to convey what the commit did and why. By convention, Git
breaks commit messages into two parts. The first line is considered the subject, followed by an empty line, followed by the body of the commit message.
* __conflict__: See merge conflict.
* __diff__:Describesthedifferencesbetweentwo(ormore)versionsofafile
or files.
* __fast-forward merge__: A merge that moves the pointer of a branch to another point in the future without creating a merge commit.
* __fetch__: Retrieving commits from a remote repository and storing them in the local repository.
* __HEAD__: The latest point in your repository that your working tree cur- rently points to.
* __index__: See staging area.
* __interactiverebase__:Sameasrebase,exceptGitpausesbeforetherebase is started and allows you to modify the commits that are being applied, modify the order in which they are applied, and specify which commits should be stopped at so they can be edited.
* __log__: A reverse chronological output of all the commits that, by default, include the committer, commit date, commit ID, and commit message.
* __master__: Refers to the name of the default branch where the majority of development happens in Git.
* __merge__: Bringing the contents of two separate branches into sync by merging them together. This can happen by any number of merge strat- egies, the most common of which are a fast-forward merge and a recur- sive merge.
* __mergecommit__:Acommitwithmultipleparentsusedtosignifyamerg- ing of two or more branches. Merge commits are generally created by recursive merges.
* __merge conflict__: A conflict that happens when two commits attempt make changes that cannot be reconciled by automated means. This generally happens during a merge or while replaying commits during a rebase.
* __non-fast-forward merge__: See recursive merge.
* __ORIG_HEAD__: Refers to the location of HEAD before making any big changes to it such as running git rebase or git reset.
