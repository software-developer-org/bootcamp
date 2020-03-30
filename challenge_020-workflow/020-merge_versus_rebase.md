# Being a student means: self-study!

Like in life: others may help you, but you have to study yourself! From now on all challenges won't provide you detailed problems and step-by-step instructions. Instead topics are introduced where self-study is required. You have to research on your own on the wep for papers and in-depth sources. Also there will be no unique solution, but your solution that you will present and commit in your branches.

This is what all software projects and customers expect from you and your team: provide your knowledge and development skills that you own now or are willing to adopt yourself by selfstudying. This often happens not before but during you are doing a project. You have to learn new tools, languages, APIs, etc.

# Merge conflicts

Have a look at this (and try it yourself!):

```
$ mkdir merge-example
$ cd merge-example/
$ git init
Initialized empty Git repository in D:/workspace/merge-example/.git/
$ echo Hello, world! > README.md
$ git add .
$ git commit -m 'initial commit'
[master (root-commit) 1f24ead] initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 README.md
$ git log
commit 1f24ead0f0483f71c35a3b262a1a94389f2c1aca (HEAD -> master)
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 20:05:49 2020 +0200

    initial commit
$ git status
On branch master
nothing to commit, working tree clean
$ git checkout -b temporary-branch
Switched to a new branch 'temporary-branch'
$ echo another line >> README.md
$ git checkout master
Switched to branch 'master'
$ echo Hello, me >> README.md
$ git commit -am 'hello, me'
[master f101d10] hello, me
 1 file changed, 1 insertion(+)
```

Now let's merge it with temporary branch:
```
$ git merge temporary-branch
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.
$ git status # shows all files with conflicts
On branch master
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Use vi to fix it.
Before:
```
Hello, world!
<<<<<<< HEAD
Hello, me
=======
another line
>>>>>>> temporary-branch
```

After:
```
Hello, world!
Hello, me
another line
```

Back in bash:
```
$ git add . # staging files tells git conflicts are resolved
$ git status
On branch master
All conflicts fixed but you are still merging.
  (use "git commit" to conclude merge)

Changes to be committed:

        modified:   README.md
$ git commit
[master f7df061] Merge branch 'temporary-branch'
$ git log
commit f7df0616dc8c879e34ffcc974059eaae93603c1e (HEAD -> master)
Merge: f101d10 d30038d
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 20:17:06 2020 +0200

    Merge branch 'temporary-branch'

commit f101d10303eaa0db276794e9833effcf6784d090
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 20:12:36 2020 +0200

    hello, me

commit d30038d447301a0308f66c46f3caa44a861bdf60 (temporary-branch)
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 20:11:18 2020 +0200

    updated

commit 1f24ead0f0483f71c35a3b262a1a94389f2c1aca
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 20:05:49 2020 +0200

    initial commit
```

# Exercise: merge commit

Document above example in a new feature-branch. Look at the current/latest commit:
```
$ git show
commit f7df0616dc8c879e34ffcc974059eaae93603c1e (HEAD -> master)
Merge: f101d10 d30038d
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 20:17:06 2020 +0200

    Merge branch 'temporary-branch'

diff --cc README.md
index 759ff41,e7dd6a5..f0e2b8f
--- a/README.md
+++ b/README.md
@@@ -1,2 -1,2 +1,3 @@@
  Hello, world!
 +Hello, me
+ another line
```

Have a close look at the 2nd output:
> Merge: f101d10 d30038d
SHA code 'f101d10' was the last commit from master branch and SHA code 'd30038d' was the last commit from the temporary branch.

Research (e.g. from the Pro Git book and gitready.com) and explain what the concept of merge commits is!
# Exercise: rebase

Back to bash and let's revert the last merge commit, and do a rebase of the temporary branch instead:
```
$ git reset --hard HEAD~1
HEAD is now at f101d10 hello, me

maita@LAPTOP-P4D7LDG2 MINGW64 /d/workspace/merge-example (master)
$ git rebase temporary-branch
First, rewinding head to replay your work on top of it...
Applying: hello, me
Using index info to reconstruct a base tree...
M       README.md
Falling back to patching base and 3-way merge...
Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
error: Failed to merge in the changes.
hint: Use 'git am --show-current-patch' to see the failed patch
Patch failed at 0001 hello, me
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit: run "git rebase --skip".
To abort and get back to the state before "git rebase", run "git rebase --abort".
$ git status # shows all conflicts
rebase in progress; onto d30038d
You are currently rebasing branch 'master' on 'd30038d'.
  (fix conflicts and then run "git rebase --continue")
  (use "git rebase --skip" to skip this patch)
  (use "git rebase --abort" to check out the original branch)

Unmerged paths:
  (use "git reset HEAD <file>..." to unstage)
  (use "git add <file>..." to mark resolution)

        both modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

Now fix the file (like you did above) and commit it:
```
$ vi README.md

maita@LAPTOP-P4D7LDG2 MINGW64 /d/workspace/merge-example (master|REBASE 1/1)
$ git add README.md

maita@LAPTOP-P4D7LDG2 MINGW64 /d/workspace/merge-example (master|REBASE 1/1)
$ git status
rebase in progress; onto d30038d
You are currently rebasing branch 'master' on 'd30038d'.
  (all conflicts fixed: run "git rebase --continue")

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

        modified:   README.md


maita@LAPTOP-P4D7LDG2 MINGW64 /d/workspace/merge-example (master|REBASE 1/1)
$ git rebase --continue
Applying: hello, me
```

Let's look at the log:
```
$ git log
commit 2ceb571ffd18ba6b415bdcd4dbb4e2790cad49dc (HEAD -> master)
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 20:12:36 2020 +0200

    hello, me

commit d30038d447301a0308f66c46f3caa44a861bdf60 (temporary-branch)
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 20:11:18 2020 +0200

    updated

commit 1f24ead0f0483f71c35a3b262a1a94389f2c1aca
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 20:05:49 2020 +0200

    initial commit
```

Compared to merge (having 4 commits), rebase has only 3 commits. If you look close to the latest commit, you see this was your last commit on master. But the SHA code has changed! This is what rebase does.

Research (e.g. from the Pro Git book and gitready.com) and explain what the concept of rebase is!

# Exercise: fetch and rebase remote branches

In the real world your main branch is 'develop'. Several developers work on different features. Once a feature is done it needs to be moved back to the develop branch.

Let's emulate that on the sandbox:
- switch to develop branch
- go 2 commits back
- checkout a new feature branch
```
$ cd sandbox/ # go to sandbox repo
$ git branch
  develop
  feature/6-new_feature
* feature/7-update_feature

maita@LAPTOP-P4D7LDG2 MINGW64 /d/workspace/sandbox (feature/7-update_feature)
$ git checkout develop
Switched to branch 'develop'
Your branch is up to date with 'origin/develop'.
$ git reset --hard HEAD~2
HEAD is now at 2d2bc37 Initial commit
$ git reset --hard HEAD~2
HEAD is now at 2d2bc37 Initial commit
$ git checkout -b feature/merge-rebase-remote-branch
Switched to a new branch 'feature/merge-rebase-remote-branch'
```

Next:
- do something and commit to the new branch
- switch to develop branch
- pull and update develop branch back to latest commits
```
$ echo hello, world! > myfile.md
$ git add myfile.md
$ git commit -am 'new feature...'
[feature/merge-rebase-remote-branch 5e24591] new feature...
 1 file changed, 1 insertion(+)
 create mode 100644 myfile.md
$ git checkout develop
Switched to branch 'develop'
Your branch is behind 'origin/develop' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)
$ git pull
remote: Enumerating objects: 10, done.
remote: Counting objects: 100% (10/10), done.
remote: Compressing objects: 100% (6/6), done.
remote: Total 8 (delta 2), reused 7 (delta 1), pack-reused 0
Unpacking objects: 100% (8/8), done.
From https://github.com/software-developer-org/sandbox
 * [new branch]      feature/8-new_feature -> origin/feature/8-new_feature
 * [new branch]      feature/9-update_feature -> origin/feature/9-update_feature
Updating 2d2bc37..2a8bbf5
Fast-forward
 README.md           | 4 ++++
 challenge-010/dummy | 0
 challenge-020/dummy | 0
 challenge-030/dummy | 0
 challenge-040/dummy | 0
 challenge-050/dummy | 0
 challenge-060/dummy | 0
 challenge-070/dummy | 0
 challenge-080/dummy | 0
 challenge-090/dummy | 0
 10 files changed, 4 insertions(+)
 create mode 100644 README.md
 create mode 100644 challenge-010/dummy
 create mode 100644 challenge-020/dummy
 create mode 100644 challenge-030/dummy
 create mode 100644 challenge-040/dummy
 create mode 100644 challenge-050/dummy
 create mode 100644 challenge-060/dummy
 create mode 100644 challenge-070/dummy
 create mode 100644 challenge-080/dummy
 create mode 100644 challenge-090/dummy
$ git status
On branch develop
Your branch is up to date with 'origin/develop'.

nothing to commit, working tree clean
```
Now try the following:
- merge with feature branch
  - how many commits do you see?
  - analyze the merge commit
- hard revert the last commit (removes the merge commit)
- rebase with feature branch
  - how many commits do you see?
  - which commits' SHA code has changed (look on GitHub and compare to it)?

Document the steps you have done in a markdown file.

What you see is that with rebase you are not only moving your commits from the feature branch, but you are also changing commits/SHA codes on the develop branch. This means you are changing other developers work. **This is what you do not want to do**!

# Exercise: rebase on feature branch

Let's undo the changes on develop and switch to your feature branch:
```
$ git reset HEAD~3 --hard
HEAD is now at 2d2bc37 Initial commit
$ git status
On branch develop
Your branch is behind 'origin/develop' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean
$ git pull
```

Now on local develop branch let's go back 2 commits. In the real world this is like you once pul from remote branch. In the mean while somebody did some changes and pushed it on remote develop branch (which is 2 commits ahead of your local develop branch):

```
$ git reset HEAD~2 --hard
HEAD is now at 2d2bc37 Initial commit
$ git status
On branch develop
Your branch is behind 'origin/develop' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

nothing to commit, working tree clean
```

Now switch to your feature branch, fetch remote branch, and rebase from remote branch:

```
$ git checkout feature/merge-rebase-remote-branch
Switched to branch 'feature/merge-rebase-remote-branch'
$ git fetch origin master
From https://github.com/software-developer-org/sandbox
 * branch            master     -> FETCH_HEAD
$ git rebase origin/master
First, rewinding head to replay your work on top of it...
Applying: new feature...
$ git log
commit bbe4c9adb749baa292c86844561dfccdb3c93a88 (HEAD -> feature/merge-rebase-remote-branch)
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Mon Mar 30 21:13:05 2020 +0200

    new feature...

commit 2a8bbf568acf4429261271ae516b76e4efae3239 (origin/master, origin/develop, origin/HEAD)
Author: Tai 'Mr. T' Truong <tai.truong@software-developer.org>
Date:   Wed Mar 25 20:20:16 2020 +0100

    setup challenges
```

What you see in the git log is that your feature branch is up-to-date with remote develop branch. In addition to that your commit is top, but with a changes SHA-code!

What does that mean? Imagine there has been more changes on develop branch. Using fetch and rebase on remote branch allows you to keep all you commits on top of it. This is useful because all your work stays together - instead of being hidden in one merge commit!

Now you can switch back to develop branch and merge it back:

```
$ git checkout develop
Switched to branch 'develop'
Your branch is behind 'origin/develop' by 2 commits, and can be fast-forwarded.
  (use "git pull" to update your local branch)

maita@LAPTOP-P4D7LDG2 MINGW64 /d/workspace/sandbox (develop)
$ git merge feature/merge-rebase-remote-branch
Updating 2d2bc37..bbe4c9a
Fast-forward
...
$ git status
On branch develop
Your branch is ahead of 'origin/develop' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
$ git push
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 312 bytes | 156.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To https://github.com/software-developer-org/sandbox
   2a8bbf5..bbe4c9a  develop -> develop
```

What happened? You merged your feature branch, git status tells you your local branch is in sync with your remote branch, plus you are ahead of one commit! Now you can push all work back to GitHub.

Document all the steps above, commit and finish your work!

# Exercise: interactive rebase

Here at software-developer.org you should **only** use fetch, rebase on feature branch and merge it back to remote branch.

Please keep in mind that you are the one and only owner of your feature branch. This means rebasing on that and chaning your commit's SHA code doesn't hurt since it is yours. Never do that on branches that belongs to others (like develop branch).

Avoid using merge and creating merge commits. Why? Imagine you have tons of commits in your feature branch. Then you merge it into your develop branch. Then later other people make changes on develop branch. So new commits comes in.

Here are some pseudo commits how it may look like:
- commit 1
- commit 2
- feature commits (either one big merge commit, or X commits due to rebase)
- later commit 3 from a developer
- later commit 4 from another developer

Then you realize your feature is totally broken. You and your team decides to undo your feature changes. So you want to achieve this:
- commit 1
- commit 2
- commit 3
- commit 4

In case of a merge branch it may happen that your have one big merge commit to undo. 

With rebase you have can do reorder your commits:
- commit 1
- commit 2
- later commit 3 from a developer
- later commit 4 from another developer
- feature commits (either one big merge commit, or X commits due to rebase)

Basicall you put your feature commits at the end (on top). This is what you can do with 'rebase -i'.
Finally you can remove/reset your last commit. Result is that you have undone your work.

Try the steps above and document it in a markdown file!

