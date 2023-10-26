# Autom-A.github.io

This repository deploys a [website](https://autom-a.github.io) with all the documentation for users and developpers. The gohugo website is using the following module theme : [Relearn](https://mcshelby.github.io/hugo-theme-relearn/index.html)

# Requirements
## A - Complete Setup

You must install go and gohugo. this repo use go version 1.21.3 (see **go.mod** file). This allows you to use the following command:
```bash
hugo new <chapter>/<page_name>.md
```
And use also the following command:
```bash
hugo server
```
The command above builds and serves the website at http://localhost:1313 and render your markdown pages.

## B - No Setup

We don't encourage this method, but if you don't want to install hugo and go. You can just create a file in the right directory like:
```bash
echo "---
title: "<page_title>"
date: <YYYY-MM-DD>T<HH:MM:SS>+<time_shift>
draft: true
---" | tee ./content/<chapter>/<page_name>.md
```
The **time_shift** corresponds to you time shift from UTC time. If you are in UTC+1 region you must put **+01:00** but if you are in UTC-2 put **-02:00**. Here an example:
```bash
echo "---
title: "Tutorial"
date: 2023-10-22T14:04:00+02:00
draft: true
---" | tee ./content/dev_docs/tutorial.md
```

This method has many disadvantages, including that you won't be able to take advantage of all the features of the chosen theme.

# How to add a page ?
## Create a chapter

> In the following explanations, we will assume that you have the [complete setup](#a---complete-setup).

A chapter is simply a markdown page that is used also as a directory. You can nest chapters within chapters, like folders on your computer. To create a chapter, you have just to do the following command:
```bash
hugo new --kind chapter <chapter_name>/_index.md
```

It will create a **_index.md** with the following content:
```
+++
archetype = "chapter"
title = "Title of the Chapter"
weight = X
+++
```

You must change the value of "weight", this value is used to modify the order of chapter in the side bar by ascending order.

## Create a wiki page

> In the following explanations, we will assume that you have the [complete setup](#a---complete-setup).

You have just to use the following command:
```
hugo new <chapter_name>/<page_name>.md
```

```md
---
title: "Page Name"
date: 2023-10-25T16:31:13+02:00
draft: false
---
```
It will crate a markdown file with some metadata like "draft: true", you must set it to false to publish the page during the website compilation.

# Translation

The default language is english but there is also a french translation. To translate a chapter or a page, copy/paste this one and add the ISO Language code to it. Here an example:
- default language: **tutorial.md**
- french language: **tutorial.fr.md**
- spanish language: **tutorial.es.md**
- etc.

Then you need to translate the content !

# Want to contribute ?

If you want to add a new language translation or to improve the actual documentation do not hesitate to fork this project, modify it, and then ask for pull request.
For minor fix, you can just open an issue on this repository.