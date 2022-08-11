---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "How To Fix Hugo Website Error - from config failed to resolve output format headers from site config"
subtitle: ""
summary: ""
authors: []
tags: []
categories: []
date: 2022-08-11T20:53:53+05:30
lastmod: 2022-08-11T20:53:53+05:30
featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
## Introduction

Sometimes you might encounter the following error on typing <span style="color:DimGray;background-color: #F0FFFF">hugo server</span> from your local website directory.

```shell
Error: from config: failed to resolve output format "headers" from site config
```

To resolve the error, head over to <span style="color:DimGray;background-color: #F0FFFF">config/_default/config.yaml</span> and temporily rewrite the following line as follows:

```shell
outputs:
  home: [RSS, JSON, WebAppManifest]
```

Open terminal and from the home directory of the website type the following commands:

```shell
hugo mod clean
hugo mod get -u ./...
hugo mod tidy
```

When the update is complete head over to <span style="color:DimGray;background-color: #F0FFFF">config/_default/config.yaml</span> and restore the items that were rewritten.

```shell
outputs:
  home: [HTML, RSS, JSON, WebAppManifest, headers, redirects]
```

Now type <span style="color:DimGray;background-color: #F0FFFF">hugo server</span> from the website home directory and it should successfully start a server.


```python

```
