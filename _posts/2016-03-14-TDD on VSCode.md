---
layout: post
title: "TDD on Visual Studio Code"
description: ""
category:
tags: []
---
#### VS Code,TDD,GulpJS and more buzzwords,

Dot Net Core is finally in release candidate, the .Net community have been waiting for ages for this to come out! Cross platform is something everyone is excited about and its been a lot of confusion when it comes to the latest version of .net. We went from vNext to .Net 5 to .Net Core

And for this new cross platform world, we have a new IDE! [VS Code](https://goo.gl/Th9qSO) while this new IDE is much more light weight than the Visual Studio we are used to on Windows, it takes a bit to get used to.

I wont go into much detail to why VS code is different than Visual Studio and why Microsoft have launched it. There are plenty of articles out there which do it far more justice than I ever could.

From here on in I am going to assume you have VS code installed on your machine

Unfortunately for those of you (including myself) who are new to using VS Code you will find a few subtle changes, for example you cant just build your solution with a shortcut like you do on Windows.

Another thing is it doesn't have a built it test runner yet.

the aim of this blog post is to walk you through doing TDD on it.

For anyone doing TDD, [NCrunch](http://www.ncrunch.net/) is a must, the ability to save your files and have all your tests run automatically changes the way you code completely, the immediate feedback is immense!

So to start off with we need a working environment, for this tutorial we will be using a Mac.

First make sure you have VS Code and .Net core installed on your machine, you can follow this [guide](http://docs.asp.net/en/latest/getting-started/installing-on-mac.html)


Next we check out my sample code using the below command

```
git clone https://github.com/samelamin/VSCodeTDDTutorial
```

This checks out the code which contains a **CoreConsoleApp** and **CoreConsoleApp.Tests** projects

Now we need to install [gulp](http://gulpjs.com/) which we will use as a task runner.

To do that we open up the terminal and navigate to the root folder of the repo and install gulp and gulp-shell using the below command

```
npm install gulp
npm install gulp-shell
```

This will install all gulp locally but chances are you might want to run gulp from the terminal so you will have to install it again globally using the below command

```
npm install gulp -g
npm install gulp-shell -g
```

Next we will set up a build task, if you press ctrl+shift+B VS Code will complain and say no task runner is configured, click on "Configure Now". This will create a **tasks.json** file. Here is where we will define what tasks to run. Replace the contents of the file with the JSON below

``` javascript
{
    "version": "0.1.0",
    "command": "gulp",
    "isShellCommand": true,
    "tasks": [
        {
            "taskName": "default",
            "isBuildCommand": true,
            "showOutput": "always",
            "isWatching": true
        }
    ]
}
```
