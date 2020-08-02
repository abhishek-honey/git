# Pragmatic Guide to Git

* [1. Getting Started](#1.-Getting-Started)
	* [Task 1. Installing Git](#Task-1.-Installing-Git)
	* [Task 2. Configuring Git](#Task-2.-Configuring-Git)
	* [Task 3. Creating a New Repository](#Task-3.-Creating-a-New-Repository)
	* [Task 4. Creating a Local Copy of an Existing Repository](#Task-4.-Creating-a-Local-Copy-of-an-Existing-Repository)


* [2. Working with Git](#2.-Working-with-Git)
	* [Task 5. Seeing What Has Changed](#Task-5.-Seeing-What-Has-Changed)
	* [Task 6. Staging Changes to Commit](#Task-6.-Staging-Changes-to-Commit)
	* [Task 7. Committing Changes](#Task-7.-Committing-Changes)
	* [Task 8. Ignoring Files](#Task-8.-Ignoring-Files)
	* [Task 9. Undoing Uncommitted Changes](#Task-9.-Undoing-Uncommitted-Changes)
	* [Task 10. Moving Files in Git](#Task-10.-Moving-Files-in-Git)
	* [Task 11. Deleting Files in Git](#Task-11.-Deleting-Files-in-Git)
	* [Task 12. Sharing Changes](#Task-12.-Sharing-Changes)


* [3. Organizing Your Repository with Branches and Tags](#3.-Organizing-Your-Repository-with-Branches-and-Tags)
	* [Task 13. Creating and Switching Branches](#Task-13.-Creating-and-Switching-Branches)
	* [Task 14. Viewing Branches](#Task-14.-Viewing-Branches)
	* [Task 15. Merging Commits Between Branches](#Task-15.-Merging-Commits-Between-Branches)
	* [Task 16. Rewriting History by Rebasing](#Task-16.-Rewriting-History-by-Rebasing)
	* [Task 17. Deleting Branches](#Task-17.-Deleting-Branches)
	* [Task 18. Tagging Milestones](#)


* [4. Working with a Team](#4.-Working-with-a-Team)
	* [Task 19. Adding and Removing Remotes](#Task-19.-Adding-and-Removing-Remotes)
	* [Task 20. Retrieving Remote Changes](#Task-20.-Retrieving-Remote-Changes)
	* [Task 21. Retrieving Remote Changes, Part II](#Task-21.-Retrieving-Remote-Changes,-Part-II)
	* [Task 22. Sending Changes to Remotes](#Task-22.-Sending-Changes-to-Remotes)
	* [Task 23. Handling Remote Tags and Branches](#Task-23.-Handling-Remote-Tags-and-Branches)


* [5. Branches and Merging Revisited](#5.-Branches-and-Merging-Revisited)
	* [Task 24. Handling Conflicts](#Task-24.-Handling-Conflicts)
	* [Task 25. Handling Conflicts with a GUI](#Task-25.-Handling-Conflicts-with-a-GUI)
	* [Task 26. Temporarily Hiding Changes](#Task-26.-Temporarily-Hiding-Changes)
	* [Task 27. Cherry-Picking Commits](#Task-27.-Cherry-Picking-Commits)
	* [Task 28. Controlling How You Replay Commits](#Task-28.-Controlling-How-You-Replay-Commits)
	* [Task 29. Moving Branches](#Task-29.-Moving-Branches)


* [6. Working with the Repository’s History](#6.-Working-with-the-Repository’s-History)
	* [Task 30. Viewing the Log](#Task-30.-Viewing-the-Log)
	* [Task 31. Filtering the Log Output](#Task-31.-Filtering-the-Log-Output)
	* [Task 32. Comparing Differences](#Task-32.-Comparing-Differences)
	* [Task 33. Generating Statistics About Changes](#Task-33.-Generating-Statistics-About-Changes)
	* [Task 34. Assigning Blame](#Task-34.-Assigning-Blame)


* [7. Fixing Things](#7.-Fixing-Things)
	* [Task 35. Fixing Commits](#Task-35.-Fixing-Commits)
	* [Task 36. Reverting Commits](#Task-36.-Reverting-Commits)
	* [Task 37. Resetting Staged Changes and Commits](#Task-37.-Resetting-Staged-Changes-and-Commits)
	* [Task 38. Erasing Commits](#Task-38.-Erasing-Commits)
	* [Task 39. Finding Bugs with bisect](#Task-39.-Finding-Bugs-with-bisect)
	* [Task 40. Retrieving “Lost” Commits](#Task-40.-Retrieving-“Lost”-Commits)


* [8. Moving Beyond the Basics](#8.-Moving-Beyond-the-Basics)
	* [Task 41. Exporting Your Repository](#Task-41.-Exporting-Your-Repository)
	* [Task 42. Doing Some Git Housekeeping](#Task-42.-Doing-Some-Git-Housekeeping)
	* [Task 43. Syncing with Subversion](#Task-43.-Syncing-with-Subversion)
	* [Task 44. Initializing Bare Repositories](#Task-44.-Initializing-Bare-Repositories)


* [9. Glossary](#9.-Glossary)

* [System design topics: start here](#system-design-topics-start-here)

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

Finally, once I have those commits ready, I share those commits by push- ing them (push is the term for sending commits to another repository) back upstream to my public repository so the rest of the team can view them and integrate them with their repositories.

#### Repository Layouts
* One method is the fully distributed model. In this, each developer has their own public repository that the developer uses to publish their changes to. All the other developers on the team then pull changes from everyone else’s repositories to keep current.
* In practice, most teams have a lead developer who is responsible for making sure all the changes are integrated. This limits the number of repositories you and your team have to pull changes from to one, but it increases the workload on the person who has to integrate everyone’s changes.
* Another method is the shared repository model, where all developers can push to a shared repository. This resembles the standard centralized model and is often adopted by teams when they first start using Git—it requires the least amount of mental overhead when it comes to thinking about where a change is shared.
* You can mix both of these as well to create a hybrid solution. Use a shared repository for all of the code that’s ready for production, and each developer maintains their own public repository for sharing code that’s still a work in progress.

### Task 1. Installing Git

* __Mac__
	*	Download the latest Git for Mac installer.

	Follow the prompts to install Git.

	Open a terminal and verify the installation was successful by typing git --version:

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
* [Task 4. Creating a Local Copy of an Existing Repository](#Task-4.-Creating-a-Local-Copy-of-an-Existing-Repository)
* [Task 7. Committing Changes](#Task-7.-Committing-Changes)
* [Task 12. Sharing Changes](#Task-12.-Sharing-Changes)
* [Task 44. Initializing Bare Repositories](#Task-44.-Initializing-Bare-Repositories)

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
* [Task 3. Creating a New Repository](#Task-3.-Creating-a-New-Repository)
* [Task 12. Sharing Changes](#Task-12.-Sharing-Changes)
* [Task 19. Adding and Removing Remotes](#Task-19.-Adding-and-Removing-Remotes)

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
* [Task 3. Creating a New Repository](#Task-3.-Creating-a-New-Repository)
* [Task 6. Staging Changes to Commit](#Task-6.-Staging-Changes-to-Commit)
* [Task 7. Committing Changes](#Task-7.-Committing-Changes)

### Task 6. Staging Changes to Commit
Git uses a two-step process to get changes into the repository. The first step is staging changes through git add. Staging a change adds it to the index, or staging area. This sits between the working tree—your view of the repository—and the actual repository.

Through the staging area, you can control what is staged from the most coarse-grained—adding everything within the repository—down to editing the changes, line by line.

It uses standard shell-style wildcards, so wildcards work: base.* matches base.rb and base.py.

You can control which parts of a file you commit using the -p parameter. Running this, you’re presented with each section of the file that has changed, and you’re given the opportunity to add or skip it. You can stage the change by pressing y or skip a change with n. s lets you break the change into smaller pieces. This and a few other options aren’t always available. You can press ? inside patch mode to get a list of all the commands and what they do.

Taking the control a step further, you can directly edit the changes that are being staged by using the -e parameter.

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
 * __In Chapter 1__, we’re going to cover Version Control Systems (VCSs) and Git basics — no technical stuff, just what Git is, why it came about in a land full of VCSs, what sets it apart, and why so many people are using it. Then, we’ll explain how to download Git and set it up for the first time if you don’t already have it on your system.
 * __In Chapter 2__, we will go over basic Git usage — how to use Git in the 80% of cases you’ll encounter most often. After reading this chapter, you should be able to clone a repository, see what has happened in the history of the project, modify files, and contribute changes. If the book spontaneously combusts at this point, you should already be pretty useful wielding Git in the time it takes you to go pick up another copy.
 * __Chapter 3__ is about the branching model in Git, often described as Git’s killer feature. Here you’ll learn what truly sets Git apart from the pack. When you’re done, you may feel the need to spend a quiet moment pondering how you lived before Git branching was part of your life.
Stage this hunk [y,n,q,a,d,K,g,/,e,?]? y
```

Related Tasks
* [Task 5. Seeing What Has Changed](#Task-5.-Seeing-What-Has-Changed)
* [Task 7. Committing Changes](#Task-7.-Committing-Changes)



### Task 7. Committing Changes




### Task 8. Ignoring Files





### Task 9. Undoing Uncommitted Changes





### Task 10. Moving Files in Git





### Task 11. Deleting Files in Git






### Task 12. Sharing Changes

## 3. Organizing Your Repository with Branches and Tags
### Task 13. Creating and Switching Branches





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

## System design topics: start here
