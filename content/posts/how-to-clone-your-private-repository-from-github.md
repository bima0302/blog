---
title: "How to Clone Your Private Repository From Github"
date: 2023-06-01
tags : ["tutorial"]
social_image: 'images/1-github-repository.png'
---

## Background

In this blog post, I will show you how to clone a private repository from GitHub using different methods and tools. Whether you are using HTTPS or SSH, command line or GUI, Windows or Linux, you will find a solution that works for you.

If you want to clone a private repository from GitHub, you might encounter some challenges. Unlike public repositories, which are accessible to anyone, private repositories require authentication and permission to access. Let’s get started!

![GitHub Repository](images/1-github-repository.png)

## How to clone your private repository?

You can clone a private repository from your account and you can also clone a private repository from organization if you’re its owner or member.

```
git clone https://<pat>@github.com/<your account or organization>/<repo>.git
```
To clone a private repository from your account or organization, you need to generate a PAT(Personal Access Token) on your Github account, and add it to the command above. Organization doesn’t have PAT generator. PAT is Personal Access Token.

This is how you generate a PAT on your Github account:
1. Go to “Settings”.
    ![Settings](images/1-settings.png)

2. Scroll down then go to “Developer settings”.
    ![Developer Settings](images/1-developer-settings.png)

3. Press “Personal access tokens” then press “Generate new token”.
    ![Generate New Token](images/1-generate-new-token.png)

4. Fill “Note” then check “repo”. "repo" is not checked, you cannot clone a private repository.
    ![Repo](images/1-repo.png)

5. Scroll down then press “Generate token”.
    ![Generate Token](images/1-generate-token.png)

6. Finally, a PAT is generated.
    ![PAT](images/1-pat.png)

This is the command with the PAT generated above to clone your private repository:
```
git clone https://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@github.com/<your account or organization>/<repo>.git
```