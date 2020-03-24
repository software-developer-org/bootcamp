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

# Exercise: create a new branch with one file

What you learn:
- track your work with a ticket (= issue) on GitHub
- get a local copy (=clone) from a GitHub repository
- working locally using git
- working on a new branch
- push and check your result on GitHub under your new created branch

## git

Now you need to learn git - or prove you can use it :).

- create a [new issue](https://github.com/software-developer-org/sandbox/issues) in the sandbox repo. Enter the following:
  - Title: git started: new feature
  - Comment: my first feature
  - Assignees: click on 'assign yourself'
- **remember your issue number**! All commits you will do in the sandbox should start like '#MyIssueNumber added new file'
- open the tutorial [git-started](https://github.com/software-developer-org/git-started) and follow the steps in the README file:
  - install git, vi or vim, and bash (Windows user: bash comes as 'git-bash' when installing git!)
  - do your first steps using git

Next test your git skills using the sandbox repo on GitHub.

### Clone GitHub repo on your local computer

Open bash (or git-bash on Windows) and do the following:

```
> cd my_workspace # choose a folder/workspace where you want to work
> git clone https://github.com/software-developer-org/sandbox
Cloning into 'sandbox'...
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
> cd sandbox
> git branch # this shows all local branches
* develop
  master
> git branch --all # this shows all local and remote branches
* develop
  master
  remotes/origin/HEAD -> origin/master
  remotes/origin/develop
  remotes/origin/master
```

NOTE:
> For better learning in bash: use **only** your keyboard. Do NOT use the mouse or touchpad :)!

### Create a new branch (= feature)

Now you have cloned the sandbox on your local computer. Next you'll create your own branch. Create a new branch 'feature/YourIssueNumber_git-started'. For example if your issue number is 4 then open your bash:

```
> git checkout -b feature/4_git-started
Switched to a new branch 'feature/1_git-started'
> git branch
  develop
* feature/4_git-started
  master
```


NOTE:
> Again - for better learning in bash and especially using the vi editor: use **only** your keyboard. Do NOT use the mouse or touchpad :)!


### Create and save (=commit) your first work

Now you have created **and** switched to your new branch. Next create a new, empty file 'yourissue_first-steps.md' in folder 00100_git_started:

```
> cd 00100_git_started # cd: change to directory
> touch 00004_first-steps.md # NOTE: issue should have *FIVE* digits. If your issue is 20, then file is 00020_first-steps.md
> ls -al
drwxr-xr-x 2 tt tt 4096 Mär 21 21:16 .
drwxr-xr-x 4 tt tt 4096 Mär 21 21:00 ..
-rw-r--r-- 1 tt tt    0 Mär 21 21:16 00004_first-steps.md
> tail 00004_readme.md # print the content of the file
```

Use vi in bash, edit your file 00004_first-steps.md, and save it. In vi enter a line with some text like this:
```
hello world
```

Stage and commit your changes with git. Your commit message will be '#YourIssueNumber completed!'

```
> git status # shows your file as unstage
On branch feature/4_git_started
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	00004_first-steps.md

nothing added to commit but untracked files present (use "git add" to track)
> git add . # git add all files in current folder ('.' = current folder)
> git status # shows your file being staged
On branch feature/4_git_started
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   00004_first-steps.md

> git commit -m '#4 completed!'
[feature/4_git_started e30a3ef] #4 completed!
 1 file changed, 1 insertion(+)
 create mode 100644 00100_git_started/00004_first-steps.md
> git status # shows your working folder is in sync with git (=clean)
On branch feature/4_git_started
nothing to commit, working tree clean
> git log -2 # show the last two commits/logs
commit e30a3ef57bd9a6470bfc19c3a0dcfb105691c583 (HEAD -> feature/4_git_started)
Author: taitruong <me@mr-t.org>
Date:   Sat Mar 21 22:54:44 2020 +0100

    #4 completed!

commit 069d3748525b0ac59ef333c39b6b359d2bcf3b4b (origin/master, origin/HEAD, master)
Merge: eda28c2 b3c100e
Author: Tai 'Mr. T' Truong <maitai.truong@gmail.com>
Date:   Sat Mar 21 21:36:20 2020 +0100

    Merge pull request #3 from software-developer-org/develop
    
    Develop
```

## GitHub

### Pushing your (local) git changes to the (remote) GitHub repo

Look what branches you have on your computer (=local), and what it is on GitHub (=remote):

```
> git branch --all
  develop
  feature/1_git-started
* feature/4_git_started
  master
  remotes/origin/HEAD -> origin/master
  remotes/origin/develop
  remotes/origin/feature/1_git-started
  remotes/origin/master
```

All remote branches starts with remotes/origin/. Ignore the line HEAD. You can se there are 3 branches on GitHub.

All others are local branches. You can see the remote branches exist also locally. And there your new branch that exists only locally.

Now you can push your changes (=commits) to GitHub and 'link' your local branch with the remote branch (= set upstream):

```
> git push -u origin feature/4_git_started
Username for 'https://github.com': taitruong
Password for 'https://taitruong@github.com': 
Counting objects: 4, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (3/3), done.
Writing objects: 100% (4/4), 403 bytes | 403.00 KiB/s, done.
Total 4 (delta 0), reused 0 (delta 0)
remote: 
remote: Create a pull request for 'feature/4_git_started' on GitHub by visiting:
remote:      https://github.com/software-developer-org/sandbox/pull/new/feature/4_git_started
remote: 
To https://github.com/software-developer-org/sandbox
 * [new branch]      feature/4_git_started -> feature/4_git_started
Branch 'feature/4_git_started' set up to track remote branch 'feature/4_git_started' from 'origin'.
> git status
On branch feature/4_git_started
Your branch is up to date with 'origin/feature/4_git_started'.

nothing to commit, working tree clean
```

Look closer at 'git status' before and after pushing to GitHub:

```
> git status # before push...
On branch feature/4_git_started
nothing to commit, working tree clean

> git push ... # push...

> git status # after push
On branch feature/4_git_started
Your branch is up to date with 'origin/feature/4_git_started'.

nothing to commit, working tree clean
```

You can see that after the 'git push -u ...' the git status provides additional info about the status of your local and remote branch.

### Verify results on GitHub

#### Branches

Open your Browser:
- have a look at the [sandbox repo](https://github.com/software-developer-org/sandbox)
- open the drop down named: 'Branch: master'
  - you should see your branch
  - select your branch in the drop down
  - now navigate to folder '00100_git_started'
  - you should many files, **including** your file '00004_first-steps.md'
- open the branch drop down again
  - select branch develop
  - you see many files, **except/without** your file '00004_first-steps.md'

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
  - make your you select your branch 'feature/4_git_started' in the drop down menu
  - navigate to folder 00100_git_started
  - select your file 00004_first-steps.md. You see:
    - on top your commit message (shows always the latest commit on this file) 
    - you see your file including the content
    - you see on the right the latest commit with SHA code 'e30a3ef'

# Exercise: additional changes on your branch

## update file, commit, and push to GitHub
  - create a new issue
    - title: git started, feature update
    - write: updating file related to #4
    - Assignees: assign this issue to yourself
    - remember issue number (e.g. 5)
  - open bash
  - make sure
    - you are working on your branch (git status)
    - your working folder is in sync with your remote folder (git pull)
  - edit and save file with more lines for text
  - commit with message '#5 file updated'
  - what does git status say?
    - what does say about your local branch compared to remote branch (origin)?
  - push your file
  - what does git status now say?

## GitHub: verify and close issue

Now check your result on GitHub
 - Go to issue (e.g. 5)
   - what do you read?
   - is it linked with the previous issue (#4)?
   - click and check on commit (SHA code on the right)
   - go back and close your issue!
 - navigate in the code and have a look at your file
   - to which commit is the message refereing?
   - click on the commit (SHA code on the right)

# Next
Go back to the [challenge folder](./) and continue with the next exercises. For each exercise you need to follow this [guideline](../challenge_020-workflow/020-workflow.md#software-developerorg-workflow-guidelines).

Most importantly guideline, rule 1: **every exercise starts with creating a new issue**.

Just to point this out again: every exercise starts with creating a new issue!

Every time you commit your exercise you need to put your issue number at the begnning of your commit message. Example for a commit message: '#YourIssueNumber title of exercise XYZ'.
