# Workflow

So far you have learned the following tools: git, bash, vi, GitHub

As long as your work alone you may not need considering (but should) about **how** you work. But working in a team you **must** organize your work with others. You must define some common understanding about your team's workflow.

Why?
- software consists of:
  - features (the things/functions a user can do on your software)
  - bugs (these tedious errors that always exist on software, whether you like or not)
  - releases (= versions)
    - your current version (= current release) the user is working on (e.g. Windows 10, git v2.25.2)
    - your next version (= release candidate = rc) you are working on (e.g. Windows 11, git v2.26.0-rc2)

Each team has their own workflow. Here are the most common most teams agrree on. Here at software-developer.org these workflows are our guidelines.

## software-developer.org Workflow Guidelines

> 1. A new task starts with a new issue ('no commit without an issue!')
> 2. The master branch is the current customer release (= production release branch owned by release manager, 'developers never uses the master branch')
> 3. The develop branch is the next release
> 4. Developers works only on feature and hotfix (=bugs) branches
> 5. Before moving a feature or hotfix to a release (develop or master) it needs to be reviewed by another developer (= 'Pull Request on GitHub')
> 6. Once a review is accepted, a feature/hotfix branch is copiey (= merged) into a release branch (= 'Accepting a pull request')

You will learn these guidelines in the following exercises.

Please note: **all** exercises are done in the [sandbox repo](https://github.com/software-developer-org/sandbox)

# Exercise: semantic versioning

- create a new issue 'workflow: semver'
- read these resources:
  - [semver.org](https://semver.org)
  - [wikipedia](https://en.wikipedia.org/wiki/Software_versioning)
- summarize your readings in a semver_summary.md
  - use git
  - don't forget creating a new feature branch!
- the summary should contain these chapters:
  - What is Semantic Versioning?
    - Example: "Version 1.9.0"
    - "1" stands for ... (explain!)
    - "9" stands for ...
    - "0" stands for ...
  - Why Semantic Versioning?
    - explain why
    - Example. Your Software "my cool git extension" with version 1.9.0 uses git v1.8.4
      - there are new git versions: v1.8.5, v1.9.0, v1.15.0, v2.26.0
      - your are working on a new feature for version 1.10.0
        - which git version later than v1.8.4 can you use?
	- there is a new git version v.2.27.0-rc7. Would you recommend updgrading to this version? why?
      - you are working in parallel for version 2.0.0
        - which git version would you use? why?
  - versions
    - you started a developing another software. With which version should it start?
    - there is a bug in software xyz version 2.1.5
      - there is a bug to be fixed. which version should the bug go into?
      - there are two new features to be develop. which version should they go into?
      - there is an existing feature in 2.1.5 called "export as txt file". now you change it to "export as csv file". which version should this go to?
- commit and push your work
  - don't forget using your issue number in the commit message!
- close your issue!

# Exercise: branches


