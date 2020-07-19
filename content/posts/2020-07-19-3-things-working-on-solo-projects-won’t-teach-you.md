---
template: post
title: 3 Things Working on Solo Projects Won’t Teach You
slug: 3-Things-Working-on-Solo-Projects-Won’t-Teach-You
draft: false
date: 2020-07-14T16:15:48.055Z
description: Versioning, Testing, and Git
category: Software Engineering
tags:
  - Software Engineering
  - Side Projects
  - Versioning
  - Programming
---
![](/media/3thingsworkingonsolohero.jpeg "Photo by NESA by Makers on Unsplash")

While I have been programming and developing applications since I was 12, this week marks my official first year as a Software Engineer in the industry. Reflecting on my first year, I picked out a few concepts that I picked up.

## Versioning

Over the years, I have built several applications (for Hackathons, personal projects, or just trying to learn about some tools). Building these projects have helped me a lot in understanding the development workflow, and exposed me to countless tools and libraries. However, since these were just personal projects, most of them never made it to production. The ones that did were simple enough and did not need any support for versioning.

As you guys would have probably guessed, this is not the case with a Software Engineering job.

I learned about why versioning software is essential, and some best practices around it. In the section below, I give a birds-eye view of why versioning is necessary and some common strategies.

For this article, let’s talk about how versioning software works. Let’s imagine that we are working on a SAAS Application, and the application has a Client Application, which depends on a backend API. Our team is responsible for maintaining the backend API, and the Client-Side Application is developed and maintained by a different team.

> Since the client-side application has a hard dependency on the backend application, we have to make sure that the two pieces are compatible.

Essentially, we need a way to let the client app team know if the backend application has had a significant breaking change or a minor change, or just some bug fixes, as that will change the way the client app interacts with the backend API.

> This is where Semantic Versioning comes to play.

In Semantic Versioning, a version number might look like

![Semantic Versioning Format](/media/semver.png "Semantic Versioning Format")

According to the Semantic Version specification:

1. We update the Major Version when there are breaking changes (i.e., software dependent on this artifact will need to be updated as well)
2. We update the Minor version when we add functionality in a backward-compatible manner (i.e., there will be little to no changes required on a software that is dependent on this artifact).
3. We update the Patch version when we make backward-compatible bug fixes (i.e., there are no changes except bug fixing or refactoring).

### Where to track these numbers?

A common approach to track these numbers is to use git tags. Whenever we commit, and we want to increment the version number, we tag the repo at that point with the version number.

![Command to tag a repo](/media/versioningcommands.png "Command to tag a repo")

Note: Many third-party libraries will track the versions for your application and will also tag the git repos.

If you’re interested in reading more, you can read more on their [website](https://semver.org/).

## Testing, Testing, and More Testing

How many of you write tests for your side projects? None? Well, that’s at least how I did it. I never realized why testing is vital until I got the chance to see a pretty large codebase (> 60,000 loc).

> If you don’t like unit testing your product, most likely your customers won’t like to test it either.

When I previously worked on a side project, it was easy to figure out if there was a bug since the project was small with maybe just a few screens (if it was a web-app), or a few scripts. And usually, when I saw a bug, I knew exactly where the issue was.

Imagine a large codebase you just got introduced to, and don’t yet have all the knowledge to understand the entirety of the application and the different moving pieces. If you had to add a feature or make a change to an existing way, it would take ages to figure out if the feature broke any other part of the app, or had unwanted side effects in different parts of the application.

With a well-written test suite, once you make the changes required, all you need to do is run the tests to see if everything else is functioning correctly, saving you hours of frustration.Git

So, this is a little embarrassing. I had been working with version control systems for a while when I started my job and considered myself pretty comfortable with it.

Then I found out about **rebasing** and its caveats.

I came across rebasing very soon after starting, and a part of me was embarrassed as I was considered a git-master by some of my friends back at school. Although I had heard of rebasing, I had not ever used it since I never felt the need.

## Git Rebasing

Working solo, it did not matter if I used git rebase or git merge. On the contrary, when there are many developers `committing` and `merging`, the commit history can become confusing, and it might be a better idea to have developers work on separate branches and `rebasing`instead of `committing`.

Rebasing is very similar to merging (which was the method I always used). They both integrate changes from one branch into another, for example, combining changes from a feature branch with the master branch.

> The difference lies in how the changes are added to the destination branch.

To understand the difference lets first dig into how git merge works.

![Git Merge](/media/gitmerge.png "Git Merge")

When we merge a feature branch onto a base branch, git combines the commits of the feature branch and creates a merge commit. Then it adds this merge commit to the base branch.

On the other hand, rebasing will generate a linear git commit history. Git will append the commits to the base branch instead of creating a merge commit.

![Git Rebase](/media/gitrebase.png "Git Rebase")

So how does git do this?

Git takes the commits from the feature branch, and duplicate them; then it applies them to the head of the master branch.

> With the `rebase` command, you can take all the changes that were committed on one branch and replay them on a different branch.

There are some caveats around git rebasing and may not be the best choice in specific scenarios. [This article](https://www.atlassian.com/git/tutorials/merging-vs-rebasing#the-golden-rule-of-rebasing) explains how rebasing works, the typical developer workflow, and some of the caveats in depth.

These are some of the things that are not hard to learn; however, while working on solo projects, I never felt the urgency to research any of the tools mentioned above in depth.

I’d be interested to hear from other developers what you never had to touch until you worked on a project involving a larger team.

Until next time.

This article was published originally on [Medium in “Dev Genius”](https://medium.com/dev-genius/3-things-working-on-solo-projects-wont-teach-you-44d14f655fb0).