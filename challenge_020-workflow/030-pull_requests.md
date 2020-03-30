# Introduction

Remember: in previous challenge-010 one exercise was about branches based on GitFlow. Let's dive deeper into Gitflow:

- develop branch represents the next release
- feature branches represents all features that should go into the next release
- finished feature branches are merged back in to the develop branch
- one all features are done the develop branch is release (tagging develop branch with a release tag)

One important rule is: other team member needs to review your work. Once your team has approved your work, you may merged your feature into develop branch!

This is the idea of pull requests!

# Exercise: pull request feature XYZ

- search on GitHub help and read all about pull requests
- go to pull request on sandboy repo
- create a new pull request (=PR) for the first feature branch of your first exercise in challenge-010
  - create on the right for 'Reviewers' and select on team member
  - let the other team member review, comment your request
    - other team member should make comments on one or more files in different lines
    - make suggestion what should be changed
    - you reply on the comment of the other
    - you make the changes
    - the other should later see the comments and make other comments
    - the other then should approve your PR
- once approved merge your feature back to develop using fetch/rebase
  - do this on bash
  - do not do that on GitHub (there is a merge button in the PR)
- remove your feature branch locally and remotely
  - Note: feature branches that are not used anymore should be cleaned up!
- repeat that and create PRs for all your feature branches

# Exercise: review bootcamp

Open source project has the goal being used by others (developers). Like this bootcamp project you are using and taking benefits of learning new skills. As a good developer you may contribute back: provide feedback (e.g. creating issues when you find a bug), make suggestions (e.g. fixing a bug).

In the beginning of challenge 1, you got an issue for creating a feature branch on the bootcamp repo.

Now it is time for you to contribute back:
- create a PR the feature branch 'feature/review_YourName'
  - add everybody in the team as reviewers
  - everybody should review and make comments
  - you should comment and make changes on your feature branch based on the feedback of your team
  - once everybody has approved it you can merge your feature branch back to develop
  - delete your feature branch

