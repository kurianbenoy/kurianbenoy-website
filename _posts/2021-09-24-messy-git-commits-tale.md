---
title: Messy git commit relation with master and develop branches
type: post
tags: [git, github]
---

In github, there are usually dev and main branches. Usually developers advocate protecting branch features, 
to avoid any of user to not merge directly without commiting.

The reason we are getting merge conflicts when merging from develop to master is simple.
When merging PRs we are having a new commit named `Merge pull request #no` in master branch.
According to my understanding branches are like a straight line, if there is a new curve
cause by merging using git with the new commit). That curve should be in dev branch as well. 

If we are not adding that merge commit(the curve), and continuing development in the dev branch.
The things are not in sync, and we are playing by
messing history 😐. You are allowed to mess with history by rebasing, and messing
history in protected branches is not approved.

This is why git is raising a merge conflict when pushing latest changes from dev branch to master
branch. That's why we are needing to fix history in dev branch always with a new PR to have the
commit called `Merge pull request #no` also be included in our history.

~ Mera Thoughts
