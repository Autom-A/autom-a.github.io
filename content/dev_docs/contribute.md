---
title: "Contribute"
date: 2023-11-10T10:03:04+01:00
draft: false
author: Mijux, Filweyd
---

## Purpose

The purpose of this document is to propose a procedure to follow when developing on the [AutomA](https://github.com/Autom-A) project. This procedure applies whether you are internal or external to the project.

## Procedure

### A - ISSUE

Whatever github repository you want to work on, you need to create an issue by putting the necessary elements in it. The issue must **imperatively** be written in English.
Let's take the following example: if you want to create a new ANSSI recommendation, such as R30, you need to fill in the following fields:

| Field | Content |
| :---: | ----- |
|Title |[Make-Rule] R30 - Disable unused user accounts|
|Comment|**Todo** : questions.yml + playbook.yml <br> **From** : ANSSI <br> **Rule** : 30 <br> **Level** : Minimal|

In addition, if you are in the project, you must add :
| Field | Content |
| :---: | ----- |
|Assignees|the person(s) working on it|
|Labels|[TODO]+[enhancement]|
|Project|Kanban (remember to put the project into TODO as soon as you create it)|

### B - BRANCH

#### Case: You're working on the project's source repository

From the issue page, you can create a development branch associated with it. Simply click on "Create branch" to display a pop-up window requesting several items of information. You don't need to change the default information.

![CreateBranch1](/images/contribute/img1.png)

![CreateBranch2](/images/contribute/img2.png)

You now have a branch to develop! Don't forget to change branch (on vscode, click bottom left). Here are the commands you need to issue in your terminal:

```bash
# To retrieve changes to the repository, including the new branch
git fetch --all
# Change development branch
git checkout <your_branch_name>
# Check
git branch --show-current
```
#### Case: You're working on a project fork

You need to fork the project on your account, which will give you the rights to modify the code. Once on your repository, you can either develop directly on your *main* branch or create auxiliary branches as we do on the official repository.

### C - MERGING

#### Updating your code

##### Case: You're working on the project's source repository

Before requesting to push your modifications onto the main branch, you need to make sure that you won't overwrite the work of other contributors. To do this, you must first update your branch to the same level as the main branch.

From your development branch, perform the following commands (in order):
```bash
git checkout <your_branch_name>
git fetch
git merge origin/main
# Conflict management on your branch
# (on the command line or via your IDE)
git push
```

#### Case: You're working on a project fork

You must add the official repository as an additional remote.
```bash
git remote add source <repo_url>
```

Update your branch :

```bash
git pull source <your_branch_name>
```
You need to manage any conflicts that may arise, while taking care not to break any existing code. Now that your local repository is up to date, it's time to update your remote repository:

```bash
git push 
```

#### Merge request

From the github web interface, you can perform a pull-request to merge your branch with the main branch. Once the minimum number of reviewers has been reached, you can validate the merge.
