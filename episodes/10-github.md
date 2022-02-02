---
title: "Collaborating via Github"
teaching: 25
exercises: 10
questions:
- "How do I authenticate with Github?"
- "How do I put my project on Github?"
- "How do I &quot; _push_ &quot; my latest changes to Github ?"

objectives:
- "Authenticate with Github."
- "Connecting your project to Github."

keypoints:
- "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor `incididunt` ut labore (i.e. et dolore magna aliqua)."
- "Ut enim ad minim veniam, quis nostrud `*` exercitation `#` ullamco laboris nisi ut aliquip ex ea commodo consequat."
---

Continuing from [episode 4](../04-good-project/) ...

1. Check for your local SSH keys.  Tools --> Global Options --> Git/SVN.  
1. If your "SSH RSA key" field is blank ![](../fig/10-rstudio-global-options-git-no-ssh-keys.png) then you do not yet have SSH Keys and you should generate keys by clicking the "create RSA key" button.  ![](../fig/10-rstudio-create-rsa-key-button.png)
![](../fig/10-rstudio-create-rsa-key-set-passphrase.png) 
![](../fig/10-rstudio-create-rsa-key-result.png)
1. Login to your Github account with your web browser. [https://github.com](https://github.com)
1. If you have not yet added your Public SSH key to your Github account in "[Setting --> SSH and GPG keys](https://github.com/settings/keys)" do so.  <br><br>

Click "View Public Key" in RStudio --> Tools --> Global Options --> Git/SVN
![](../fig/10-rstudio-global-options-git-with-ssh-keys.png)

![](../fig/10-rstudio-public-key-display.png)

Click the "New SSH Key" button in Github 
![](../fig/10-github-add-new-ssh-key-button.png)
then paste it into the form.
![](../fig/10-github-add-new-ssh-key.png)


1. Create a bare repository on Github (maybe not needed if you already have a local repo ??? TEST THIS)

1. Add the new repository's Github URL to your local Git repo as a "remote" 

```
git remote add origin git@github.com:<username>/<repositoryName>.git
```

1. push your local repository up to git.


{% include links.md %}
