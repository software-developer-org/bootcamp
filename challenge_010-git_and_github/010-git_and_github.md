# Getting Started

- Sign up for a [GitHub account](https://github.com/join).
- Create a new issue [here](https://github.com/software-developer-org/assignments/issues) with title 'new core team' and a comment. Example:

```
title:
new core team

comment:
please add me to your organization at https://github.com/software-developer-org
Thanks, Tai
```

- next: wait :). You'll get an email notification when you are in
- once you are in you should find yourself [here](https://github.com/orgs/software-developer-org/people)
- in the People tab there is a dropdown. you may change your membership from private to public!

Why do you want your membership being public? Here at software-developer we want everything to be transparent. Besides (and in general) each team member should take responsibility.

Most importantly: your work counts more than any CV and represents your 'business card'.

# Exercise: new feature

What you learn:
- track your work with a ticket (= issue) on GitHub
- get a local copy (=clone) from a GitHub repository
- working locally using git
- working on a new branch
- push and check your result on GitHub under your new created branch

## git: create a new branch with one file

Now you need to learn git - or prove you can use it :).

- create a [new issue](https://github.com/software-developer-org/sandbox/issues) in the sandbox repo. Enter the following:
  - Title: challenge010: new feature
  - Comment: my first feature
  - Assignees: click on 'assign yourself'
- **remember your issue number**! All commits you will do in the sandbox should start like '#MyIssueNumber added new file'
- open the tutorial [git-started](https://github.com/software-developer-org/git-started) and follow the steps in the README file:
  - install git, vi or vim, and bash (Windows user: bash comes as 'git-bash' when installing git!)
  - do your first steps using git

A note on challenges:
- The **first step** is always creating an issue with this convention:
  - Syntax: "challenge XYZ: exercise title"
  - Example: "challenge 010: new feature"
- always start every commit message with '#YourIssueNumber: ...'
- the next challenges expect you doing this without mentioning it anymore

Next test your git skills using the sandbox repo on GitHub.

### Clone GitHub repo on your local computer

Open bash (or git-bash on Windows) and do the following:

```
$ cd my_workspace # choose a folder/workspace where you want to work
$ git clone https://github.com/software-developer-org/sandbox
Cloning into 'sandbox'...
remote: Enumerating objects: 32, done.
remote: Counting objects: 100% (32/32), done.
remote: Compressing objects: 100% (20/20), done.
remote: Total 32 (delta 2), reused 26 (delta 1), pack-reused 0
Unpacking objects: 100% (32/32), done.

$ cd sandbox
$ git branch # this shows all local branches
* develop
$ git branch --all # this shows all local and remote branches
* develop
  master
  remotes/origin/HEAD -$ origin/master
  remotes/origin/develop
  remotes/origin/master
```

NOTE:
For better learning in bash: use **only** your keyboard. Do NOT use the mouse or touchpad :)!

### Create a new branch (= feature)

Now you have cloned the sandbox on your local computer. Next you'll create your own branch. Create a new branch 'feature/YourIssueNumber_git-started'. For example if your issue number is 4 then open your bash:

```
$ git checkout -b feature/4-new_feature
Switched to a new branch 'feature/4-new_feature'
$ git branch
  develop
* feature/4-new_feature
```

Another note challenges:
- the **second step** is always creating a new branch with this convention:
  - Syntax: "feature/YourIssueNumber-Exercise_Title"
  - Example: "feature/4-new_feture"
- always commit your challenge under this branch
- the next challenges expect you doing this without mentioning it anymore

### Create and save (=commit) your first work

Now you have created **and** switched to your new branch. Next create a new, empty file 'YourIssueNumber-Exercise_Title.md' in folder challenge-010:

```
$ cd challenge-010 # cd: change to directory
$ touch 00004-new_feature.md # NOTE: issue should have *FIVE* digits. If your issue is 20, then file is 00020-new_feature.md
$ ls -al
total 4
drwxr-xr-x 1 maita 197609 0 Mar 25 20:57 ./
drwxr-xr-x 1 maita 197609 0 Mar 25 20:27 ../
-rw-r--r-- 1 maita 197609 0 Mar 25 20:57 00006-new_feature.md
-rw-r--r-- 1 maita 197609 0 Mar 25 20:27 dummy
$ tail 00004-new_feature.md # print the content of a file
$ tail ../README.md # print the content of a file from parent directory
# Sandbox

This is the sandbox

```

Use vi in bash, edit your file 00004-new_feature.md, and save it. In vi enter a line with some text like this:
```
hello world
```

NOTE: Again - for better learning in bash and especially using the vi editor: **use only your keyboard**. Do NOT use the mouse or touchpad :)!

Stage and commit your changes with git. Your commit message will be '#YourIssueNumber completed!'

```
$ git status # shows your file as unstage
On branch feature/4-new_feature
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	00004-new_feature.md

nothing added to commit but untracked files present (use "git add" to track)
$ git add . # git add all files in current folder ('.' = current folder)
$ git status # shows your file being staged
On branch feature/4-new_feature
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   00004-new_feature.md

$ git commit -m '#4 completed!'
[feature/4-new_feature e30a3ef] #4 completed!
 1 file changed, 1 insertion(+)
 create mode 100644 challenge-010/00004-new_feature.md
$ git status # shows your working folder is in sync with git (=clean)
On branch feature/4-new_feature
nothing to commit, working tree clean
$ git log -2 # show the last two commits/logs
commit 48389eefb13d3eff819bc0c681b9e0e6879a6894 (HEAD -> feature/6-new_feature)
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Wed Mar 25 21:01:41 2020 +0100

    #4 completed!

commit 2a8bbf568acf4429261271ae516b76e4efae3239 (origin/master, origin/develop, origin/HEAD, develop)
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Wed Mar 25 20:20:16 2020 +0100

    setup challenges
```

## GitHub

### Pushing your (local) git changes to the (remote) GitHub repo

Look what branches you have on your computer (=local), and what it is on GitHub (=remote):

```
$ git branch --all
  develop
* feature/4-new_feature
  master
  remotes/origin/HEAD -$ origin/master
  remotes/origin/develop
  remotes/origin/master
```

All remote branches starts with remotes/origin/. Ignore the line HEAD. You can se there are 3 branches on GitHub.

All others are local branches. You can see the remote branches exist also locally. And there your new branch that exists only locally.

Now you can push your changes (=commits) to GitHub and 'link' your local branch with the remote branch (= set upstream):

```
$ git push -u origin feature/4-new_feature
Username for 'https://github.com': taitruong
Password for 'https://taitruong@github.com': 
Counting objects: 4, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 403 bytes | 403.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0)
remote: 
remote: Create a pull request for 'feature/4-new_feature' on GitHub by visiting:
remote:      https://github.com/software-developer-org/sandbox/pull/new/feature/4-new_feature
remote: 
To https://github.com/software-developer-org/sandbox
 * [new branch]      feature/4-new_feature -$ feature/4-new_feature
Branch 'feature/4-new_feature' set up to track remote branch 'feature/4-new_feature' from 'origin'.
$ git status
On branch feature/4-new_feature
Your branch is up to date with 'origin/feature/4-new_feature'.

nothing to commit, working tree clean
```

Look closer at 'git status' before and after pushing to GitHub:

```
$ git status # before push...
On branch feature/4-new_feature
nothing to commit, working tree clean

$ git push ... # push...

$ git status # after push
On branch feature/4-new_feature
Your branch is up to date with 'origin/feature/4-new_feature'.

nothing to commit, working tree clean
```

You can see that after the 'git push -u ...' the git status provides additional info about the status of your local and remote branch.

### Verify results on GitHub

#### Branches

Open your Browser:
- have a look at the [sandbox repo](https://github.com/software-developer-org/sandbox)
- open the drop down named: 'Branch: develop'
  - you should see your branch
  - select your branch in the drop down
  - now navigate to folder 'challenge-010'
  - you should many files, **including** your file '00004-new_feature.md'
- open the branch drop down again
  - select branch develop
  - you see many files, **except/without** your file '00004-new_feature.md'

#### Issues

Have a look at all [issues](https://github.com/software-developer-org/sandbox/issues):
- you see all open issues, including your issue
- click on/navigate to your issue. What do you see?
  - your commit is shown as "YourUser added a commit that referenced this issue ...'
  - below there is your commit message '#YourIssueNumber completed!'
  - on the right you see your commit with some SHA (hash code) like 'e30a3ef'
- click on the commit SHA
  - you see your file content that comes with that commit
- click above on the tab 'Code'
  - make your you select your branch 'feature/4-new_feature' in the drop down menu
  - navigate to folder challenge-010
  - select your file 00004-new_feature.md. You see:
    - on top your commit message (shows always the latest commit on this file) 
    - you see your file including the content
    - you see on the right the latest commit with SHA code 'e30a3ef'

# Exercise: feature update

## update file, commit, and push to GitHub
  - create a new issue
    - title: git started: feature update
    - write: updating file related to #4
    - Assignees: assign this issue to yourself
    - remember issue number (e.g. 5)
  - open bash
  - make sure calling these git commands in your bash:
    - git pull # sync your working folder with remote folder
    - git checkout feature/4-new_feature # switch to your previous(!) branch
    - git checkout -b feature/5-update_feature # create a new branch based on current branch (=feature/4-update_feature)
  - change dir to challenge-010
  - edit and save file 00004-new_feature.md with more lines for text
  - stage and commit with message '#5 file updated'
  - what does git status say?
    - what does say about your local branch compared to remote branch (origin)?
  - push your file (using 'git push -u origin ...')
  - what does git status now say?

## GitHub: verify and close issue

Now check your result on GitHub
 - Go to issue (e.g. 5)
   - what do you read in the comment?
     - is it linked with the previous issue (#4)?
     - click in the comment on the previous issue #4
     - you should see a note that issue #4 is mentioned by issue #5
   - go back to issue #5
   - click and check on commit (SHA code on the right)
   - go back and close your issue!
   - go to issue #4
     - you see that issue #5 is closed
 - navigate in the code and have a look at your file
   - to which commit is the message refereing?
   - click on the commit (SHA code on the right)

# Next
Go back to the [challenge folder](./) and continue with the next exercises. For each exercise you need to follow this [guideline](../challenge_020-workflow/020-workflow.md#software-developerorg-workflow-guidelines).

Most importantly guideline, rule 1: **every exercise starts with creating a new issue and a new branch**.

Just to point this out again: every exercise starts with creating a new issue!

Every time you commit your exercise you need to put your issue number at the begnning of your commit message. Example for a commit message: '#YourIssueNumber: title of exercise XYZ'.
