---
# Documentation: https://wowchemy.com/docs/managing-content/

title: "How To Build An Academic Website Using Hugo And Github Pages"
subtitle: ""
summary: "Internet and social media are powerful tools to build your presence as an academic scholar, network with peers and promote your research. Besides social media, an essential online presence that one can have is a personal website. This post shows how to setup a personal website using the academic-theme by Hugo."
authors: []
tags: []
categories: []
date: 2022-08-03T09:13:17+05:30
lastmod: 2022-08-03T09:13:17+05:30
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

## 1. Introduction

Internet and social media are powerful tools to build your presence as an academic scholar, network with peers and promote your research. Besides social media, an essential online presence that one can have is a personal website.

This post describes how to set up a personal academic website using the static website generator [**Hugo**](https://gohugo.io/) and publish it using [**GitHub Pages**](https://pages.github.com/). The post is targeted toward students, scientists and faculty members who have a basic knowledge about how to use Git, command line tools and Github.

Our final goal is to have two Github repositories: a source repository called <span style="color:DimGray;background-color: #F0FFFF">username_website</span>, which contains the website's unprocessed resources and a host repository called <span style="color:DimGray;background-color: #F0FFFF">username.github.io</span> which hosts the website.

***

##  2. Create a Website

### 2.1 Prerequisites


As mentioned before, you need certain prerequisites to follow this post. The requirements are listed below.

* You must have a [**Github**](https://github.com) account.
* You must have [**Git**](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) installed.
* You must have [**Go**](https://go.dev/dl/) installed.
* You must have basic [**Command line**](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Understanding_client-side_tools/Command_line) knowledge.

### 2.2 Install Hugo

Download and install the hugo from [**gohugoio/hugo**](https://github.com/gohugoio/hugo/releases) into your computer.

<div class="alert alert-block alert-info">
    <b> Note: </b> Install the latest extended-version of hugo.
</div>

### 2.3 Download A Theme

Open the terminal and from your home directory, type the following commands.


```shell
git clone https://github.com/wowchemy/starter-hugo-academic.git username_website
cd username_website
git submodule update --init --recursive
```

<div class="alert alert-block alert-info">
    <b> Note: </b> You must replace 'username' with your GitHub username.
</div>

### 2.4 Launch The Website

Make sure you are in the <span style="color:DimGray;background-color: #F0FFFF">username_website</span> directory. From the terminal, type the following command


```shell
hugo server
```

<div class="alert alert-block alert-info">
    <b> Note: </b> This will launch a server on your terminal which will locally host your website. Copy the URL displayed on the terminal and paste it into the browser of your choice. You must be able to see the website now.


</div>

***

## 3. Basic Customisation

### 3.1 Open Files In Text Editor

To customise the website, we need a text editor. You can choose any of your favourite text editors to do the task. In case you are using [**atom**](https://atom.io), you can open the files as follows:

Make sure you are in <span style="color:DimGray;background-color: #F0FFFF">username_website</span> directory. Now type

```shell
atom .
```

This must open all the files in the directory on the atom text editor window. Now, if you edit and save any file, the changes should reflect on your local browser window.

### 3.2 Personal Details Customisation

Following are the essential files you need to modify to customise your website:


* <span style="color:tomato; background-color: LavenderBlush">config/_default/config.yaml</span> : Edit this file to modify general website information.
* <span style="color:tomato; background-color: LavenderBlush">config/_default/params.yaml</span> : Edit this file to customise your website.
* <span style="color:tomato; background-color: LavenderBlush">config/_default/menus.yaml</span>: Edit this file to customise the menu bar.
* <span style="color:tomato; background-color: LavenderBlush">content/authors/admin/_index.md</span>: Edit your personal information here.

### 3.3 Profile Picture Customisation

The profile picture and the website icon can be modified as follows:

* <span style="color:tomato; background-color: LavenderBlush">content/authors/admin/avatar.jpg</span>
* <span style="color:tomato; background-color: LavenderBlush">assets/media/icon.png</span>

Replace  <span style="color:tomato; background-color: LavenderBlush">avatar.jpg</span> and <span style="color:tomato; background-color: LavenderBlush">icon.png</span> with the pictures of your choice.

<div class="alert alert-block alert-info">
    <b> Note: </b> Do not change the filenames. Just replace the files and retain the same filenames.
</div>



### 3.4 Widgets Customisation

To modify the widgets on your homepage, change the files in the <span style="color:tomato; background-color: LavenderBlush">content/home/</span> folder. In case you want to delete a section, open the related file and set <span style="color:tomato; background-color: LavenderBlush"> active:false</span>. More details about customisation can be found on [**wowchemy**](https://wowchemy.com/docs/getting-started/customization/) website.

***

## 4. Modify .gitignore File

In .gitignore file delete the line saying <span style="color:SlateGray;background-color: #F0FFFF">public/</span>.

***

## 5. Delete public/ Folder

Completely delete <span style="color:SlateGray; background-color: #F0FFFF">public</span> folder if it exists.
***

## 6. Create A New Repository <span style="color:Gray;background-color: #F0FFFF">username_website</span> On GitHub

To create a new repo on GitHub, log in and go to the [**GitHub**](https://github.com) home page. You can find the “New repository” option under the “+” sign next to your profile picture in the top right corner of the navbar. After clicking the button, GitHub will ask you to name your repo and provide a brief description.

* Name the repo <span style="color:Gray;background-color: #F0FFFF">username_website</span>.
* Provide a brief description, for example, "Contents of my academic website".
* Click on <span style="color:Green">Create repository</span> button.

***

## 7. Modify .git/config file

**Currently .git/config file looks like shown below**

```shell
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
[remote "origin"]
	url = https://github.com/sourcethemes/academic-kickstart.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "main"]
	remote = origin
	merge = refs/heads/main
```

**Modify the url to look like this**

```shell
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
[remote "origin"]
	url = git@github.com:username/username_website.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "main"]
	remote = origin
	merge = refs/heads/main
```

***

## 8. Add Files To Staging Area And Create A Commit

After you have completed customising the website, add all the files to the staging area with the following command. Make sure you are in <span style="color:Gray; background-color: #F0FFFF ">username_website</span> directory.

```shell
git add .
```

Once all the modified files are added to the staging area, leave a short commit message which summarises your changes.

```shell
git commit -m "fully customised version of the website"
```

***

## 9. Point Your Directory <span style="color:Gray; background-color: #F0FFFF">username_website</span> To Your Newly Created  <span style="color:Gray; background-color: #F0FFFF">username_website</span> Repo On Github

From <span style="color:Gray; background-color: #F0FFFF">username_website</span> directory in the terminal type


```shell
git push -u origin --all
```

Now, login to your account in Github and make sure that all the contents of your website are uploaded to <span style="color:Gray; background-color: #F0FFFF">username_website</span> repository. This repository will hold all the contents of your website on Github. Now that we have a secure copy of all the contents, we can move on to create a new repository to host your website.

***

## 10. Create A New Repository <span style="color:Gray; background-color: #F0FFFF">username.github.io</span> On GitHub To Host Your Website

Create a new repo on GitHub named <span style="color:Gray; background-color: #F0FFFF">username.github.io</span>. Log in and go to the [**GitHub**](https://github.com) home page. You can find the “New repository” option under the “+” sign next to your profile picture in the top right corner of the navbar. After clicking the button, GitHub will ask you to name your repo and provide a brief description.

* Name the repo <span style="color:Gray; background-color: #F0FFFF">username.github.io</span>. The 'username' here must be same as your Github username.
* Provide a brief description, for example, "My academic website".
* Click on the Public option
* Initialise the repository with a README file and a licence.
* Now click on <span style="color:Green">Create repository</span> button.

***

<div class="alert alert-block alert-danger">
<b>Note:</b> Please make sure that these steps are strictly followed without any changes.
</div>



## 11. Update The Website URL

Update the website url in <span style="color:tomato; background-color: LavenderBlush">config/_default/config.yaml</span> file. The base url must look like

```shell
baseURL: 'https://username.github.io/' # Website URL
```
***

## 12. Clone  <span style="color:Gray; background-color: #F0FFFF">username.github.io</span> To public Directory

From the terminal, run the following commands:

```shell
cd username_website
git clone https://github.com/username/username.github.io.git public
```
***


<div class="alert alert-block alert-info">
<b>Note:</b> If you get: warning: You appear to have cloned an empty repository. – go back to the Github repo and create a README and licence file.
</div>


## 13. Make A Test File To See If The Website Works

Let us make a text file index.html to check if the website works as intended. From the <span style="color:Gray; background-color: #F0FFFF">username_website</span> directory, type the following commands

```shell
cd public
touch index.html
echo '<h1>Hello World - v0</h1>' >> index.html
```
Now push this change to the Github repository corresponding to the website. That is the repository named <span style="color:Gray; background-color: #F0FFFF">username.github.io</span> using the following command.

```shell
git add .
git commit -m "test webpage"
git push
```

**If everything goes well, towards the end of the terminal output, you must be able to see the following lines.**

```shell
To github.com:username/username.github.io.git
```

<div class="alert alert-block alert-success">
<b>Note:</b>  If you see the above line in the terminal window, skip the next step and move on to step 15.
</div>


**Else, you might encounter the following error**

```shell
remote: Permission to username/username.github.io.git denied to username.
fatal: unable to access 'https://github.com/username/username.github.io.git/': The requested URL returned error: 403
```

<div class="alert alert-block alert-danger">
<b>Note:</b> In case you encounter the above-mentioned error, go to the next step 14.
</div>

***

## 14. Clone The Repository <span style="color:Gray; background-color: #F0FFFF">username.github.io.git</span> Outside The <span style="color:Gray; background-color: #F0FFFF">username_website</span> Directory

Make sure you are outside <span style="color:Gray; background-color: #F0FFFF">username_website</span> directory. Then type the following commands to clone <span style="color:Gray; background-color: #F0FFFF">username.github.io.git</span> repository into your computer.

```shell
git clone git@github.com:username/username.github.io.git
cd username.github.io
echo '<h1>Hello World - v1</h1>' >> index.html
git add index.html
git commit -m "testing if the website works"
git push
```

After successfully completing the above procedure we move this repository into the <span style="color:Gray; background-color: #F0FFFF">username_website</span>. Run the following commands from outside the <span style="color:Gray; background-color: #F0FFFF">username_website</span> directory.

```shell
rm -rf username_website/public
mv username.github.io username_website/public
```

Now type the following commands,

```shell
cd username_website/public
echo '<h1>Hello World - v2</h1>' >> index.html
git commit -am "testing if the website works from within hugo project"
git push
```

Wait for a few minutes and go to the website **https://username.github.io**. You must be able to see the contents of the newly published index.html page.

***

## 15. Configure public As A Submodule

Add <span style="color:Gray; background-color: #F0FFFF">username.github.io.git</span> as a submodule using the following commands. Make sure you are in <span style="color:Gray; background-color: #F0FFFF">username_website</span> directory.

```shell
cd public
git submodule add -b master https://github.com/username/username.github.io.git public
```

Now open .gitmodules file and make sure the contents of the file look like shown below.

```shell

[submodule "public"]
	path = public
	url = https://github.com/username/username.github.io.git
	branch = master
```

***

## 16. Construct And Publish Your Website

Now construct your website using the following command. From <span style="color:Gray; background-color: #F0FFFF">username_website</span> directory run the following command.

```shell
hugo
```

The above command will construct the html, css and js files necessary to show your website online in the public folder. Now run the following commands to push your website online

```shell
cd public
git add .
git commit -m "first version of the website is now online"
git push
```
<div class="alert alert-block alert-info">
<b>Note:</b> Step 16 must be followed every time you make changes to the website.
</div>

Go back to  **https://username.github.io** and check out your newly published website!

***
