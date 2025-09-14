author: Tony Beaumont
summary: Using GIT to track my work
id: git-01
categories: version-control
environments: Web
status: Published
feedback link: mailto:a.j.beaumont@aston.ac.uk

# Using GIT: How to complete and submit tasks

## Introduction

We are going to use GIT to keep track of versions of our work and submit completed exercises as a **Pull Request**.

### What you should already know

You should have done the prep in the [Onboarding module, Sprint 1](https://programming.codeyourfuture.io/onboarding/sprints/1/prep/)

### What you'll learn

- **fork** a repository
- **clone** a repository
- **basic git commands** such as `git add`, `git commit`, `git push`

### What you'll need

You need a laptop with `git` installed ([Download Git](https://git-scm.com/downloads)). You will also need VS Code installed ([Download VS Code](https://code.visualstudio.com/download)).

### What you'll do

You will fork and clone a git repository. Then do some work to complete an exercise. Finally you will submit your work in a Pull Request.

## What is a Git repository?

The [GitHub Docs](https://docs.github.com/en/repositories/creating-and-managing-repositories/about-repositories) says the following about repositories:

> aside positive
> A repository is the most basic element of GitHub. It's a place where you can store your code, your files, and each file's revision history. Repositories can have multiple collaborators and can be either public or private.

This is the repository we are going to use today: [https://github.com/beaumoaj/git_practice](https://github.com/beaumoaj/git_practice). When you follow the link, this is what you will see.

![The Repository in a web browser](./images/TheRepository.png)

To work on a repository you need to create a copy of the whole repository down to your local computer This is referred to as creating a `clone` of the repository. However this repository does not belong to you and so if you `clone` it you will not be able to save your changes back to the repository. To allow your changes to be saved, you must first `fork` the repository to your own GitGub account.

To complete your CYF work, you will usually be starting from a [CYF repository](https://github.com/codeyourfuture). The usual process will be to:

1. `fork` the original repository so you have a copy of it in **your own GitHub account**.
2. `clone` your copy of the repository back to **your computer**. Once the files are on your computer, you can edit them.
3. Do some work in which you make changes to the files in the copy on your computer.
4. Inform `git` which files you have changed using the `git add` command.
5. Save a local snapshot of your updated files by using the `git commit` command.
6. Upload your changes to the copy of the repository in your GitHub account using the `git push` command.
7. Repeat steps 3 to 6 until you have finished met the success criteria for the work.
8. Submit your work by submitting a **pull request**. A pull request will notify the owner of the **original repository** (which you forked) that you are sending them some changes to look at. CYF uses pull requests to keep track of work submitted by trainees. Volunteers will look at your pull requests and either approve (ie. you completed it correctly) or reject them (ie. you didn't meet the success criteria).

> aside positive
>
> # Terminology
>
> **fork** copy a repository from some else's GitGub account to your own GitHub account.<br/>
>
> **clone** copy a repository down to your own computer.

Now we will step through the process and see who it works.

## Forking a repository

> aside positive
> Forking a repository means take an original repository from someone else's github account and make a new copy in your own github account.

Open the repository [https://github.com/beaumoaj/git_practice](https://github.com/beaumoaj/git_practice) in your web browser.

Click on the **Fork** button and choose **Create new fork** as shown on the right hand side of this image:
![Creating a fork](./images/CreateFork.png)

You will be shown the following form:
![Form to specify the name of the copy](./images/ForkForm.png)

1. You should ensure that the **Owner** field is set to your username.<br/>
1. You can keep the suggested **Repository name** which will be used as the name of the repository in your github account.<br/>
1. The **Description** field may already contain some suitable text, but if not you could write your own or edit the original. For example, you could write:
   ```console
   This repository is part of Onboarding sprint 1
   ```
1. Finally, click the **Create fork** button.

When Github has finished making a copy of the repository, you will be shown the new copy in your account. You can tell the difference between the two repositories by checking the URL in the address bar of your browser. For example, if the URL https://**github.com**/**CodeYourFuture**/**js-exercises** (reading from right to left) tells me that this is a repository called **js-exercises** owned by a user called **CodeYourFuture** on **github.com**. If I fork it to my account, the new copy will have the URL https://github.com/**beaumoaj**/js-exercises. The difference is that the owner is now **beaumoaj**, which is my github user name. When you fork a repository, you should always check that you are working with **your** copy.

## Cloning a repository

> aside positive
> Cloning a repository means to select a github repository (usually) in your account and copy all the files down to your local computer.

First, you need to have a **directory** (another name for **folder**) into which you can copy the repository. To keep track of all of your work for ITP, create a new **directory** called (for example) `CYF-ITP`. **Inside** that directory, create new sub-directory for each sprint. Your sub-directory could be called (for example) `Onboarding-Sprint1`.

Now open the new folder in a terminal window. In a Linux computer press the **Ctrl** and **ALT** keys together (I will write this as `CTRL-ALT`) and then press the `t` key and a new terminal will open in your home folder. Now you need to change into your new directory using the `cd` command (you can remember `cd` as standing for Change Directory).

```bash
cd ~/CYF-ITP/Onboarding-Sprint1
```

Here is an example from my computer:
![Changing directory](./images/TerminalCD.png)

Notice that the prompt to the left of the cursor will tell you which is the current directory.

You can use the `ls` command to LiSt the files in the current directory. If you do that in your new directory you won't see any files. It should look like this:
![Listing files](./images/listFiles.png)

Now lets `clone` the repository.

If it is not already open, open your copy of the repository on GitHub in your web browser. Make sure you are starting from **your copy of the repository** (look for **your username** in the URL in your web browser). Click the green **Code** button and you will see the **Clone** options.

![Code button on GitHub](./images/cloneRepository.png)

You need to select either **HTTPS**, or **SSH**, or **GitHub CLI** and the copy the URL from the box.

> aside positive
>
> To use the **SSH** option, you must have set up `SSH` access (see [https://docs.github.com/en/authentication/connecting-to-github-with-ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)) before you can use that way of cloning a repository.
>
> To use the **GitHub CLI** you need to install the GitHub Command Line tools on your computer (see [https://cli.github.com/](https://cli.github.com/))

We will use the **HTTPS** option. Select the `HTTPS` tab and copy the URL from the box. Now go to you terminal window and use the `git clone` command to clone the repository. The command is a version of the command shown below but the text **YOUR_USERNAME** should be replaced with whatever your username is on GitHub (you can anyway paste the URL after copying it from you repository)

```console
git clone https://github.com/YOUR_USERNAME/git_practice.git
```

When you enter your version of the above command, you will get some messages printed to your terminal as the repository is copied down to your computer. If you use the `ls` command again, you should now see a new folder with the same name as the repository. On my computer it looks like this. The new folder is called `git_practice`:
![After cloning a repository](./images/afterClone.png)

## Project brief

Follow the instructions below to style the bio. Try looking up the CSS features you'll need in the [MDN CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference).

### Box styles

1. Give the `&lt;body&gt;` element a padding of `20px` on all sides and a width of `500px`.
1. Give the `&lt;body&gt;` element a background color of `#efefef` (a light-gray &lt;hex-color&gt; value).
1. Center the `&lt;body&gt;` element inside the viewport by setting top- and bottom-margins of `0`, and left- and right-margins of `auto`.
1. Give the `&lt;ul&gt;` used for the contact details a background color of white, and a `5px` solid purple border on all sides. Give the `&lt;ul&gt;` padding of `30px` on all sides to push the content away from the border.
1. Give the `&lt;ul&gt;` a border radius of `20px`.

### Text styles

1. Make the level one heading dark gray, using the CSS color keyword `darkslategray`, and give the heading a `10px` dotted bottom border, which uses the CSS color keyword `purple`.
1. Make the level two heading italic.
1. Give the level one heading a font size of `2rem` and the level two heading a font size of `1.5rem`.
   Select the `&lt;div&gt;` using a class selector, and give it a color of `darkslategray` and a `bold` font weight.
1. Make the links `green`.
1. Make the links `darkgreen` while hovered over with the mouse pointer or focused via the keyboard (you'll need to use a couple of pseudo-classes for this).
1. Make the links lose their underline while hovered or focused.

### Hints and tips

1. Use the [W3C CSS Validator](https://jigsaw.w3.org/css-validator/) to catch unintended mistakes in your CSS — mistakes you might have otherwise missed — so that you can fix them.
2. Try looking up some more advanced CSS features (again, the [MDN CSS reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference) will be useful here) and add some more styles to your solution. Get adventurous!
3. Remember that there is no wrong answer here — at this stage in your learning you can afford to have a bit of fun.

### Example

Your finished example should end up looking something like this:

![Example Solution](./images/SolutionExample.png)
