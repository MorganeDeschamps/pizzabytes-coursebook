<!-- ![](https://i.imgur.com/1QgrNNw.png)

# SG | Git Intro -->

After this lesson you will be able to:

- explain what a version control system is,
- understand why we should use Git,
- create a new repository,
- check the status of a repository,
- add files to a commit (staging area),
- commit files,
- understand the git log,
- create an account in GitHub and
- create a repo, clone repo, add files, commit files, push files to the remote repo on GitHub.

## What is git?

During the web application development cycle, many changes occur - new features, bugs management, re-factorization of the code... Sometimes you might want to take a snapshot of the current state of the app, and it would be super useful if you could restore it to in case you made some unwanted changes you wish to remove. This all is possible - and thanks to Git.  
At the same time, web development projects usually require the effort of more than one programmer. Teams collaborate on the same projects, and not all the time, all changes synced together give the most amazing results.
How to go about this and similar challenges, you might ask? Again we have to thank to the Git. It helps us to have new releases, code that has to be organized and accessible for everyone. Git tracks changes and has a smooth and practical way of putting new code together without breaking what is already there.

:::info
**Git** is a free and open-source distributed version control system.

A **version control system** is software that helps developers to track changes and distribute their code.
:::

## Git advantages or why we should use Git?

- **Distributed architecture**

Git is an example of a [DVCS (Distributed Version Control System)](https://en.wikipedia.org/wiki/Distributed_version_control). This means that rather than have one single place for the full version history of the software, every developer gets to have his own working copy of the code. This copy is also a repository with the complete history of all changes ever done to that version of the code.

In case you are curious and want to learn about other options, not just about DVCS, check this [article](https://en.wikipedia.org/wiki/Distributed_version_control#Distributed_vs._centralized) from Wikipedia.

- **Flexibility**

Git allows us to have various development workflows, so it adapts to any project size. It also provides compatibility with a lot of existing systems and protocols.

- **Everyone knows Git**

Git has come to be the expected version control system for new projects. It has the functionality, performance, security, and flexibility that most teams and individual developers need, that's why everyone uses it. Also, many developers already have Git experience, so it is a de-facto standard.

- **Git is an open-source**

Git is an open-source project with more than ten years of evolution. The project maintainers have shown balanced judgment and a mature approach to meeting the long term needs of its users with regular releases that improve usability and functionality.

You can check the [Git source code on GitHub](https://github.com/git/git). Check the number of commits and collaborators! It is impressive! This also means the Git community is enormous, and a lot of good quality documentation is available on the Internet, through books, tutorials, and dedicated websites.

Let's make our hands a bit dirty. Next is to practice how to work with Git.

## Creating a Repository

Git manages different projects with different repositories. We generally call them `repos` for short. :smile:

To make your project a `git` repository, open your terminal and go inside **your project folder**. Right in this folder, at the top of your project, type:

```shell
$ git init
Initialized empty Git repository in [your .git directory path]
```

:::info
:warning: You don't need to type the `$` symbol. It is provided by your terminal to let you know where you should type your commands.
:::

This command creates a **hidden directory - `.git`** in your project's folder. This hidden directory is where Git operates and stores its data. Since we just initialized our project as Git repository, we didn't make any changes so far, so `.git` repository is still empty.

Type `ls -la` in your terminal to see the new folder.

## Checking the status

Let's type the `git status` command to see what is the current state of our project:

```
$ git status
# On branch master
#
# No commits yet
#
nothing to commit (create/copy files and use "git add" to track)
```

:::success
:bulb: It's healthy to run `git status` often. Sometimes you might by accident make some unwanted changes, and you didn't even notice that.
:::

## Adding and committing changes

Create two files: `index.html` and `about.html`.

```
$ touch index.html about.html
```

Run the `git status` command again to see how the repository status has changed:

```shell
$ git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)

         about.html
            index.html

nothing added to commit but untracked files present (use "git add" to track)
```

As you can see, Git is now detecting changes - in this case, two new files. Also, it recognizes that these new files are not being tracked, and Git suggests how to add them in the next commit.

What does it mean - _the new files are not being tracked_, is the logical question here. It refers to the fact that some change has been made in the project (which is correct, we created two news files), but Git is not aware of this change yet. In case we want to come back to this state of our app at some point later, Git wouldn't be able to help us since this change wasn't recorded in the `.git` repository. To make a record of it, the change needs to be **committed**.

:::info
A Git commit works a lot like _taking a picture_. It takes a [snapshot](<https://en.wikipedia.org/wiki/Snapshot_(computer_storage)>) of the files added to the commit.
:::

This is a fundamental concept to understand. Imagine it's your brother's birthday, and you are the unofficial photographer. You get to choose which family members are going to be included in each picture. You select some of them, ask them to stay still somewhere in the house, and then you take a picture. With Git, family members are your project files. The moment of asking your relatives to stand somewhere in the house so you can take a photo of them is represented with adding files that will be committed. When you take the picture, you're committing the changes.

:::info
:warning: You are not making copies of the files you're tracking. You are just creating a snapshot of the files you added.
:::

However, before we are able to commit file/s, we have to make sure we pick the ones we want to commit. We can decide to _add all the files_ that have some changes in them, or _just some of them_.

### Adding the file - staging

Now, let's add `index.html` to the tracked group.

```shell
$ Git add index.html
$ git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)

           new file:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)

    about.html
```

Let's review:

- with `git add index.html`, we added `index.html` to staging area;
- we run `git status` so we make sure we added only what we needed, which is just `index.html`. We can see that `index.html` is listed on _changes to be committed_, that is what we wanted;
- also, we can see that `about.html` is listed as _Untracked files_, which is again what we wanted since we added only `index.html` to be committed.

We saw that combining `git + <file name>` we can add files one by one. If you want to add all the files that have had some changes in them, you can type:

```shell
$ git add .
```

**Dot (`.`) means - add all files.**

### Removing the file - unstaging

As you can see in your Git status output, you can also remove files from the tracking group. This is known as **unstaging the changes**. When we add the files, we are staging them for commit. We know this is a lot of new expressions for you to understand. However, these terms will soon become part of your everyday vocabulary.
Let's explain the concept of unstaging a bit more. In case you added some files and then realized you don't want to do that now, you can always unstage them (remove them from staging area) using:

```shell
$ git rm --cached <file-name-1> <file-name-2>...
```

The `<>` around the _file-name-1_ and _file-name-2_ just points where you should add the name of the file you want to unstage, so don't have to use these signs actually.

Check the example below: let's say that you, by accident, added both files (_index.html_ and _about.html_), and you wanted to add just _index.html_. What you can do is to remove `about.html` with the following command:

```shell
# example of how to remove a file that is staged by mistake
$ git rm --cached about.html
```

After this, if you would run `git status`, you would see that `about.html` is marked as an untracked file again. Simple and perfect!

### Committing the files

Now when you have all your changes added to the staging area, it is time to commit them to `.git` so there's a _snapshot_ (a record) of the current state of the app.

To commit your changes simply type:

```shell
$ git commit -m "add index.html file"
[master (root-commit) d100e63] Add the index.html file
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 index.html
```

Try to be as descriptive as possible with your commit message. Once you see it, it has to tell you why you made it. Examples of good commit messages are:

- _bugfix - create callback to make sure the data is available before rendering file_ or
- _clean code - remove redundant variables_.

After you committed changes, the record of them has created in the `.git` repository and you can always go back to this state of the app if needed. Even if that is not needed, you can always check the history to see how your app development progressed and what are all the things that you had to do to get your app to the current state.

In case you want to make sure you added just what you needed/wanted, you can run once again `git status`. You can run this command whenever you want.

## Git log

We briefly mentioned you could go to history and check all the commit messages and the order in which you made them. You have access to much more details - who made commit, when was made, what commit message was attached to it and also you get the unique number that represents that very commit, which is the number under which was recorded the state of the app in that moment.

You can think of Git's log as a journal that remembers all the changes we have committed so far, in the order we committed them. You can run now:

```
$ git log
```

The output will be something like this:

```shell
commit 389345d4e7652ea595c1ba234a970c4cd6ba5d31 (HEAD -> master)
Author: sandrabosk <sandraboskovic@hotmail.com>
Date:   Thu Jan 16 15:35:54 2020 -0500

    add index.html file
```

The log file will open in your terminal with the [less](<https://en.wikipedia.org/wiki/Less_(Unix)>) program and to exit simply type **`q`**.

## Remote repositories

To collaborate on any Git project, you need to know how to manage remote repositories.

**Remote repositories** are versions of your project that are hosted on the Internet or network somewhere. Collaborating with others involves managing these remote repositories and pushing and pulling data to and from them when you need to share work.

## GitHub

:::success
[GitHub](https://github.com/) is a code-hosting platform. It lets you and others work together on projects from anywhere.
:::

:warning: Before anything else, if you haven't done it yet, you should go now to [github.com](https://github.com/) and create an account.

:::success
:eyeglasses: **GitHub** is NOT **Git**.

- Git is a version control software that creates a registry of different states of your app in the `.git` repository.
- GitHub is a hosting platform that understands Git.

Git runs on your local machine, while GitHub runs on the Internet. Keep in mind some people consider GitHub as a social network for code sharing.
:::

## Clone a GitHub repository

To clone a GitHub repository is to copy the entire project to your local computer. It is a combination of:

- `git init` (create the local repository)
- `git remote add` (add the URL to that repository)
- `git fetch` (fetch all branches from that URL to your local repository)
- `git checkout` (create all the files of the main branch in your working tree)

For now, forget about the fetching and the checkout. We will learn about branches in another lesson.

But you should know that `git clone` already initializes your local repository and adds the URL of the remote repository, so the system knows where to put the changes and from where get the changes while you work.

### Clone a repo from your GitHub profile to your local machine

Before being able to clone the repo, you have to create it on your GitHub profile.

1. **Create a repo on your GitHub profile**

   Go to your profile on GitHub. You have to log in. There are multiple ways to create a new repository on GitHub:

   - you can follow this [link](https://github.com/new)
   - you can click on the **+** sign next to your image in the upper right corner:

   ![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_4f1d41dbc7da7dee984b7dc0f8425555.png)

   - follow the steps:
     - give your repo a name (ex. `clone-test`),
     - (optional) Give it some description (check the image below if you need some inspiration),
     - make it public,
     - (optional) you can, but don't have to click on `Initialize this repository with a README`.

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_33550afd38f7d8105d9791b67e24fd85.png)

2. **Cloning the repository**

   After you have created a new repository (`clone-test`), you should see a page like this:
   ![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_43fab2186e9ee398e6e7a3119230e1b4.png)


    2.1 Now copy the link that is marked in red on the image - it should be in this format: `https://github.com/your-gh-username/clone-test.git`

    2.2 Go to your terminal and navigate where you would like to clone the folder (example: navigate to your Ironhack repository and if you have subfolders like ex.week1 and whichever day (ex.day3)) and then type following (in the terminal):

```shell
# make sure you don't copy the following,
# you have to use the link that points to your own GitHub repo

$ git clone https://github.com/<your-gh-username>/clone-test.git
```

What you should see in your terminal should look similar to this:

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_838e0ae6dd959041058f62a4c79f5b5f.png)

BOOM! :rocket:
Have you just cloned the repo? Yes, you have! Amazing!

## Push to a GitHub repository

As the message in terminal said, you cloned an empty repository. Let's add a file in it and push it to the GitHub. First, let's navigate to the newly cloned repository:

```shell
$ cd clone-test
$ touch index.js
$ code .
```

You can add just a comment in the `index.js` file:

```javascript
// This is just a test.
// We want to make sure this will be pushed to GitHub.
```

Now run **`git status`** to see the changes which you are about to commit:

```shell
$ git status

# On branch master
# No commits yet
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)

#     index.js

# nothing added to commit but untracked files present (use "git add" to track)
```

We are ready to follow the steps we already practiced:
-stage files (with `git add`),

- commit files (with `git commit`) and
  -we will have one more command that will allow us to push `index.html` (and any other files we might have) to GitHub, and that is `git push origin master`:

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_401b1eeff303b30e848b406847b10d24.png)

Now, go to your GitHub profile and refresh the page where is your `clone-test` and you should be able to see `index.js` and comments we added in it:

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_038bd6625db9fdecb9fffa6ad8a66f99.png)

This worked like a charm! Amazing job.

### Clone a repo from someone's GitHub profile to your local machine

Let's clone a repository from the Ironhack labs account. To do this, navigate to the directory where you want to have this folder cloned and copy the following command (without the `$`):

```
$ git clone https://github.com/ironhack-labs/lab-learn-cloning.git
```

After hitting enter, you will see the following:

```shell
Cloning into 'lab-learn-cloning'...
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 5 (delta 0), reused 5 (delta 0), pack-reused 0
Unpacking objects: 100% (5/5), done.
```

This is just an extremely simplified example of a project that you have just cloned, but it doesn't really matter how big the project is, the process will be the same.

:::warning
Keep in mind - **you can't make changes in remote repositories that don't belong to you**.

You can make changes locally, but if you would like to push those changes, you would get an error that says _"Permission denied <your-GitHub-username>"_.

In order to be able to push to the repository that doesn't belong to you (doesn't point to your GitHub page), you have to be added as a _collaborator_. More about this topic later.
:::

:::success
To check where any cloned repository is pointing (the URL address), you can type:

```shell
$ git remote -v
```

If the URLs that are returned as a response don't point to your GitHub profile, you won't be able to push to them.
:::

When inside `clone-test`, make some small changes to any of the files. Let's say you made some updates in the `index.html`. Save the changes, check the URLs this repo is pointing to and then try to push to the remote repository:

```shell
$ git remote -v
# origin  https://github.com/ironhack-labs/lab-learn-cloning.git (fetch)
# origin  https://github.com/ironhack-labs/lab-learn-cloning.git (push)
```

As we can see, this lab doesn't point to your GitHub profile. It points to the `ironhack-labs`. We won't be able to push but let's try:

```
$ git add .
$ git commit -m"add updates in index.html - fix grammar"
# [master b7a38b2] add updates in index.html - fix grammar
#  1 file changed, 1 insertion(+), 1 deletion(-)
```

And finally, the push:

```shell
$ git push origin master

# remote: Permission to lab-learn-cloning.git denied to sandrabosk.
# fatal: unable to access 'https://github.com/ironhack-labs/lab-learn-cloning.git': The requested URL returned error: 403
```

:::info
Still, there is a way you can contribute to the repositories that are not yours. One of the ways is to **fork** them first and then clone them, but we will talk about this later.
:::

## Fun fact

![](https://i.imgur.com/iDbve7w.png =400x)

The **octocat** is GitHub's mascot and logo. It was designed by [Simon Oxley](https://pando.com/2013/07/08/original-github-octocat-designer-simon-oxley-on-his-famous-creation-i-dont-remember-drawing-it/), who created the Twitter bird too.

It is an octopus with the head of a cat, and GitHub users have been creating versions of the octocat since GitHub was born. If you want to take a look at all the versions, go to the [OctoDex](https://octodex.github.com/).

## Practice time

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_4c348de3a59169168c150d8744057cc4.png)

Now it's your turn to practice some more git in [Learn Git Branching](https://learngitbranching.js.org/) site!

## Summary

In this lesson, you have learned what Git and GitHub are, how to initialize repositories, stage and unstage existing files, commit changes, and read the log. Also, you have your GitHub account already created, and you cloned a real project repository on your (local) computer.

## Extra Resources

- [Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf) - This cheat sheet features the most important and commonly used git commands for easy reference.
- [Commit message guidelines](https://gist.github.com/robertpainsi/b632364184e70900af4ab688decf6f53)
- [Semantic Commit Messages when pushing to GitHub](https://seesparkbox.com/foundry/semantic_commit_messages)
