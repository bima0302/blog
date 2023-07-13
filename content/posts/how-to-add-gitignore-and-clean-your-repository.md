---
title: "How to Add Gitignore and Clean Your Repository"
date: 2022-03-23
tags: ["dev"]
---

Git is a tool that helps you manage your code. Sometimes, you have files that you don’t want Git to track or share. For example, files that are temporary, not related to your project, or contain sensitive information.

If you are using Git as your version control system, you may have encountered some unwanted files or folders in your repository that you don’t want to track or share. These can be temporary files, logs, configuration files, dependencies, or any other files that are not relevant to your project. To avoid cluttering your repository with these files, you can use a special file called `.gitignore` that tells Git which files or patterns to ignore. In this blog post, I will show you how to create and use a `.gitignore` file, and how to clean your repository from the files that you have already committed but want to ignore.

## How to clone your private repository?

To add a `.gitignore` file, you can use one of the following methods:

- Create a .gitignore file manually in the root of your local Git repository and edit it with a text editor. You can use patterns to specify which files or folders to ignore. For example, to ignore all .log files and everything in any directory named temp, you can write:
  ```
  # ignore ALL .log files
  *.log
  # ignore ALL files in ANY directory named temp
  temp/
  ```
- Use Visual Studio to create a `.gitignore` file for you. In Visual Studio, click Git > Settings. This opens the Options window. Navigate to Source Control > Git Repository Settings. In the Git files section, click Add (next to Ignore file). It will add the `.gitignore` file to the repository root directory.

## How to clean repository with .gitignore?

To clean your repository with `.gitignore`, you need to remove the files that you want to ignore from the Git index and then commit the changes. There are different ways to do this, depending on whether you want to remove the files only from the latest commit or from the entire history.

- If you want to remove the files only from the latest commit, you can use the following commands:
  ```
  # remove all files from the index
  git rm -r --cached .
  # add back the files as per new .gitignore
  git add .
  # commit the changes
  git commit -m "Cleaned repository with .gitignore"
  ```
- If you want to remove the files from the entire history, you can use a script that iterates over all the files that should have been ignored and filters them out from all the commits. For example:
  ```
  #!/bin/bash
  # backup your repository first!
  for f in `git ls-files --exclude-standard --others --directory --ignored`
  do
  git filter-branch --force --index-filter "git rm --cached --ignore-unmatch '$f'" --prune-empty --tag-name-filter cat -- --all
  done
  ```
