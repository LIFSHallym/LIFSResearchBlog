---
layout: post
title: "Few github commands enough to excel in your team"
icon: star-o
author: Onche Anthony
tags: [github, git, version control, Digital forensics]
---
 ### SUMMARY
 
Git is different from github and that is a good start to help you understand this post. Git is an open-source version control system that was started by Linus Torvalds the man who created Linux OS. Version control systems are a category of software tools that help a software team manage changes to source code over time. There are other version control systems only that git is the prefered VCS out there.

So what is Git?

Git is a command-line tool, so what is github? 

Github is..

Simply a hub where developers store their projects and network with like minded people using git. To learn more see github pages [here] (https://git-scm.com/book/en/v2)

Having clearly stated this differences, let me show you a few commands to get you started with using github.
 
Like some other computer programs git takes a lot of time to master, not enough time before members of your team begin to hasten you to push the latest code and soon after you are on your way to causing everyone pain. Let's talk about how to avoid this scenario which actually was a personal experience.
 
### WHAT YOU NEED TO KNOW
 ```bash 
$ git clone
$ git checkout
$ git push
    $ git add 
    $ git commit
pull request
$ git pull
```
 You will be working with me as your team mate on a [hello-world project] (https://github.com/jokeapart/hello-world.git) in a github repository as an example to illustrate how to use the above commands.
  

 ### PROCEDURE
 Before we proceed, kindly make sure you download and install git on your computer. If you have not done so already, click [here] https://gist.github.com/derhuerst/1b15ff4652a867391f03 to do so. 
 
 Once you are done with the installation you also need to create your own account on GitHub.com. Let's go!!

1. git clone:

When ever you want to start a new project you need to clone (copy) the entire project folder from github to your local machine. To do so use the command below:

```bash
$ git clone < project github url >
```
Using our sample github repository your command will be: git clone https://github.com/jokeapart/hello-world.git

2. git checkout

We now have the same repository on github and on our local machine. It means you and I as members of a team are working on thesame codebase at thesame time. But we are currently on the master branch. To be safe, each of us should at least have a separate branch each from the master branch.

Why do we need to create separate branch from master? 

A branch is like a folder online to keep your version of changes made to the project so that as a team we can check for conflicts between our code (if our changes would break the last working version of the code in master), before we can merge our code to the master branch. The main branch is refered to as master branch.

Now create a branch using the command

```bash
$ git checkout -b [name_of_your_new_branch]
```
3. Git Push

Great job, you have created a branch and that means any changes you make on the code will be saved to your branch and not directly to the master branch (a very important safety measure).

Now go ahead and make changes to the code. Let's say add contents to README.md file located in the hello-world folder.

This newly added content is only on your local machine. In other for members of the team to get the new changes you have to push your code to github.

This has 3 sub steps in the following order

i. You have to add you changes to the repository

```bash
$ git add README.md
```
[Git Add](/img/news/gitadd.png)
ii. You have to commit your changes

```bash
$ git commit -m "Enter a description for the changes you just made"
```
iii. Now you can push to your branch

```bash
$ git push origin [name_of_your_new_branch]
```
[Git push](/img/news/gitpush.png)

4. Git Pull Request

If you visit the github url for the repo in our case https://github.com/jokeapart/hello-world , you will see your branch is now on the repo with changes specifically made by you alone. To merge your code with the master branch you will have to create a pull request. click on the button that says pull request to do so.

[Git pull request](/img/news/pullrequest.png)

5. Git pull

Let's assume your changes has been merged to master by the team member incharge of accepting pull request and you closed the day's work and went home. 

To continue your work whenever you return you have to make a git pull

What is git pull?

Remember while you started you cloned the master branch right? Then you created your branch and it has been merged back to master. Assumming while you were away other branches from your team mates were also merged to master, if you continue working on your branch and then push to be merged, you can guess that your code will surely not have alot of what is currently at the master branch and will be rejected from merging.

You should use git pull every time you want to continue working on an existing project so that you get the current codebase from the master branch into your local branch and you and your team members are always on thesame page. Git pull is like the first time when you had to clone the whole project but this time you just have to pull it.

```bash
$ git pull origin master
```

This will update your local branch with the most recent code base in the master branch. After that you can add your new changes to the code base and when you are done for working simply repeat step 3. 4.

To excel in your team revolves around repeating steps 5, 3 and 4 in that order. That is git pull, git push, git pull request. 

### GOOD PRACTICES
1. Always create a new branch for every new feature you are adding to the project. You can delete the branch after merging it to master
2. Always check the branch you are on before pushing your code. 
```bash
$ git status
```
You can change from one branch to another when neccesarry by 

```bash
$ git checkout [branch-name]
```
