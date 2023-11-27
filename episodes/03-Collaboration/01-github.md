---
title: "Collaborating via GitHub"
teaching: 20
exercises: 15
questions:
- "How do I authenticate with GitHub?"
- "How do I put my project on GitHub?"
- "How do I &quot;_push_&quot; my latest changes to GitHub?"

objectives:
- "Authenticate with GitHub."
- "Connecting your project to GitHub."
- "Make changes locally and push them to GitHub."

keypoints:
- Setting up R Studio to authenticate with GitHub using a Personal Authentication Token (PAT).
- Setting the Git repository _Origin_ in your R Studio project enables _pushing_ and _pulling_ from your local copy of the repository to the repository on GitHub.
---

> ## Synchronizing Your Project With Your Repository

In Episode [Getting your project set up with Version Control in RStudio](../03-setup-versioning), we learned about using version control as you write your publication.  In this part of the workshop, we'll set up Rstudio to authenticate with GitHub, which is necessary to _push_ your changes to GitHub.

Terminology:  Git _Push_ and _Pull_

Definition: The process of synchronizing your local git repository with your git repository on GitHub (or other Git server).

GitHub used to allow simple Username & Password authentication, but now GitHub requires a more secure method of authentication.  For this workshop, we'll be using the Personal Access Token method.  The Personal Access Token (PAT) must be created for your account on GitHub.  You'll use the PAT to authenticate instead of your GitHub account password.

1. Login to your GitHub account with your web browser. [https://GitHub.com](https://GitHub.com)
1. On GitHub.com go to your account setting -> Developer Settings -> Personal access tokens or this link: [https://GitHub.com/settings/tokens](https://GitHub.com/settings/tokens)
1. Any tokens you have created in the past will be listed there, and you can click "Generate new token" button.  Set an expiration date for your new token and a scope.  For this workshop, the scope of "Repo" should be sufficient.  Then, Generate your new Token with the button at the bottom of the page.

![PAT options on GitHub](../../fig/10-GitHub-new-PAT-options.png)
* On the next screen GitHub shows you the new token.  **Be sure to copy it** as you only get one chance to see the token text.

> ## Note: 
>
> If you cloned the repository already the next 2 steps are not necessary, as the "origin" is set as part of the cloning process. 
{: .callout}


## Getting your Repository's URL from GitHub

You can get your repository's address from GitHub by navigating to your repository on GitHub.com and clicking the green "Code" button.  

![Copy Repo URL from GitHub](../../fig/10-GitHub-clone.png)

With that address, you can complete setting the origin URL in the next step. 

## Checking and Setting the "Origin" for the local copy of your repository.

If you forked and cloned the demonstration publication for this workshop, as covered in an earlier episode, then your copy of the repository should already have the "origin" set.  Once the "origin" is set properly, you should be able to push and pull your changes to and from GitHub.  When you clone a repository from GitHub, your local copy of the repository should have GitHub set as the "origin".  

You can check this in Rstudio --> Tools --> Project Options --> Git/SVN

If the "Origin" field is blank, then you'll need to add it from the terminal with a couple of terminal commands like this:
```
git remote add origin <paste your repository address here>
git fetch --set-upstream origin main
```

Be sure **your** GitHub username is part of the URL.

After you've updated the Origin URL from the command line, go back to R Studio --> Tools --> Project Options --> Git/SVN to verify you have the "Origin" field filled in.  It should look like this.

![RSTudio Project Options Git/SVN](../../fig/10-rstudio-project-options-git-with-https-origin.png) 


## Push your local changes up to your repository GitHub.
With authentication set up and your local copy of your repository pointing to GitHub as the "Origin" you should be able to make changes locally and _push_ them up to GitHub.  

When prompted, enter your GitHub username and paste into your Personal Access Token (PAT) when prompted for your GitHub password.

![RStudio PAT Password Prompt](../../fig/10-git-mac-password-prompt.png)

 Let's try it and see if it works.

> ## Challenge 2: Push to GitHub
> 
> 1. Make a change to one of the files in your project or add a new file.
> 2. In R Studio's Git panel, check the box to Stage the changed file.
> 3. Commit the change to your Git repository.
> 4. Click the green up arrow to _Push_ your repository changes up to GitHub.
> 5. Look on [GitHub.com](https://GitHub.com) to verify your changes are there.
> 
{: .challenge}

With the ability to synchronize your changes between GitHub and your local, the next step is to explore options for publishing your research paper.


{% include links.md %}
