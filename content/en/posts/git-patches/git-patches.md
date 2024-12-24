---
title: "Git patches"
summary: "How to use git patches to store changes and share them."
categories: ["git"]
tags: ["technical"]
#externalUrl: ""
#showSummary: true
date: 2024-11-02
draft: false
---

## What are Git patches?

Patches are files that contain code and metadata in a format that Git can interpret and reapply. These files can be generated from your current changes or from a specific commit.

Patches are useful in the following situations:

- You’ve explained something to someone while screen-sharing, and you want to share the code without rewriting everything in another environment.
- You have changes that another developer needs to continue working on a task, but you need to finish something before opening a new pull request. Sharing these changes allows your coworker to use your code without delay.
- A coworker has been assigned to a project you previously worked on, so you want to share some code to help them get started.
- You want to save some code for future reference but don’t want to lose it in your long stash list.

## Creating a patch

Creating a patch is really easy.

### From changes in your working directory

You can create a patch by using the output of the `git diff` command:

`git diff > some_changes_i_want_to_share.patch`

You can also add specific files from your working directory to a patch:

`git diff file1.js > some_changes.patch`

`git diff file1.js file2.js > some_changes.patch`

### From changes in a commit

You can save the changes from a commit using `git format-patch`:

`git format-patch [commit_hash]`

## The .patch file

You can open the `.patch` file in your code editor or IDE like any other file to view the code and metadata stored in it. This allows you to verify if you’re saving what you intended.

## Applying the patch

To apply the patch, simply use the command:

`git apply my_patch_file.patch`

When you run `git apply`, the changes will be applied to your working directory. Applying a patch doesn’t create a new commit.

## Conclusion

Patches are easy to understand and use, and they’re highly useful when collaborating with other developers or saving code for future reference. Try to make the most of them to improve your workflow.
