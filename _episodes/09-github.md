---
title: "Collaborating via Github"
teaching: 15
exercises: 10
questions:
- "How do I authenticate with Github?"
- "How do I put my project on Github?"
- "How do I &quot;_push_&quot; my latest changes to Github ?"

objectives:
- "Authenticate with Github."
- "Connecting your project to Github."
- "Make changes locally and push them to Github."

keypoints:
- Setting up R Studio to authenticate with Github using SSH Keys.
- Setting the Git repository _Origin_ in your R Studio project enables _pushing_ and _pulling_ from your local copy of the repository to the repository on Github.
---

In [episode 5](../05-setup-versioning/) we learned about using version control as you write your publication.  In this part of the workshop we'll setup Rstudio to authenticate with Github which is necessary to _push_ your changes to Github.

Terminology:  Git _Push_ and _Pull_

Definition: The process of syncronizing your local git repository with your git repository on Github (or other Git server).

Github used to allow simple Username & Password authentication but now Github requires a more secure method of authentication.  For this workshop we'll be using the SSH Key method.  If you've used SSH authentication before with some other program or service you can likely use your existing keys.  If you do not yet have a pair of SSH keys you can create them using RStudio.



1. Check for your local SSH keys.  Tools --> Global Options --> Git/SVN.  
1. If your "SSH RSA key" field is blank then you do not yet have SSH Keys and you should generate keys by clicking the "create RSA key" button. ![](../fig/09-rstudio-global-options-git-no-ssh-keys.png)  ![](../fig/09-rstudio-create-rsa-key-button.png)
Set your passphrase and don't forget it.  Store your passphrase in your password manager. 
![](../fig/09-rstudio-create-rsa-key-set-passphrase.png) 
![](../fig/09-rstudio-create-rsa-key-result.png)

Click "View Public Key" in RStudio --> Tools --> Global Options --> Git/SVN and copy the public key cypher text.
![](../fig/09-rstudio-global-options-git-with-ssh-keys.png)

![](../fig/09-rstudio-public-key-display.png)

Now that you have a public key you need to add it to your account on Github.

1. Login to your Github account with your web browser. [https://github.com](https://github.com)
1. If you have not yet added your Public SSH key to your Github account in "[Setting --> SSH and GPG keys](https://github.com/settings/keys)" do so.  <br><br>

Click the "New SSH Key" button in Github 
![](../fig/09-github-add-new-ssh-key-button.png)
then paste it into the form.
![](../fig/09-github-add-new-ssh-key.png)

Now you can authenticate with Github using your SSH keys. Test this in the terminal with:

```
ssh -T git@github.com
```
## Getting your repository's URL from Github
You can get the address of your repository from Github by navigating to your repository on Github.com and clicking the green "Code" button.  Make sure to copy the SSH form of the URL.

![](../fig/09-github-clone.png)

With that address you can complete setting the origin URL in the next step. 

## Checking and Setting the "Origin" for the local copy of yoiur repository.

If you forked and cloned the demonstration publication for this workshop as covered in an earlier episode then your copy of the repository should already have the "origin" set.  Once the "origin" is set properly you should be able to push and pull your changes to and from Github.  When you clone a repository from Github your local copy of the repository should have Github set as the "origin".  When you're using SSH to authenticate with Github you'll need to use the SSH form of your repository's URL as your "Origin"

You can check this in Rstudio --> Tools --> Project Options --> Git/SVN

![](../fig/09-rstudio-project-options-git-with-https-origin.png) 

If the "Origin" field has the HTTPS form of your repository's URL then you'll need to update it from the terminal with command like:

![](../fig/09-git-remote-set-url.png)

```
git remote set-url origin <paste your repository address here>
```

Be sure to put **your** Github username in the URL.

After you've updated the Origin URL from the command line go back to R Studio --> Tools --> Project Options --> Git/SVN to verify you have the SSH form of the URL in your "Origin" field.  It should look something like this.

![](../fig/09-rstudio-project-options-git-with-ssh-origin.png) 



----

If the "Origin" field is blank then you'll need to add it from the terminal with a couple of terminal commands like this:
```
git remote add origin <paste your repository address here>
git fetch --set-upstream origin main
```

## Push your local changes up to your repository Github.
With authentication set up and your local copy of your repository pointing to Github as the "Origin" you should be able to make changes and _push_ them up to Github.  Let's try it and see if it works.

> ## Challenge: Push to Github
> 
> 1. Make a change to one of the files in your project or add a new file.
> 2. In R Studio's Git panel check the box to Stage the changed file.
> 3. Commit the change to your Git repository.
> 4. Click the green up arrow to _Push_ you repository changes up to Github.
> 5. Look on [Github.com](https://github.com) to verify your changes are there.
> 
{: .challenge}

With the ability to synchronize your changes between Github and your local the next step is explore options for publishing your research paper.


{% include links.md %}
