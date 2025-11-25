---
title: Pre-workshop Setup
---

## PART I: Install Git and create a GitHub Account

We will need the following accounts and software for this workshop:

- Create GitHub account (use existing or create a new account)
- Install Git
- Install R & RStudio (Two separate installations: if you are on a Windows device, you may need [Rtools](https://cran.r-project.org/bin/windows/Rtools/).

For the most up-to-date instructions for creating your GitHub account and installing Git, please follow the steps described in [Software Carpentry's Version Control with Git lesson](https://swcarpentry.github.io/git-novice/#installing-git).

### Git
Git is a version control system that lets you track who made changes to what, when, and has options for easily updating a shared or public version of your code on GitHub.

### Additional GitHub information
Through the [Github education program](https://docs.github.com/en/education/explore-the-benefits-of-teaching-and-learning-with-github-education/use-github-for-your-schoolwork/about-github-education-for-students), students get additional free services beyond the basic free account.

If you are concerned about what personal information (specifically contact information) is revealed through GitHub you may review these [instructions for keeping your email address private](https://help.github.com/articles/keeping-your-email-address-private/) provided by GitHub.

## PART II: Install R/Rstudio and Quarto

### R
R is a powerful programming language for data exploration, visualization, and statistical analysis. To interact with R, we use RStudio.

Follow the [installation instructions provided here](https://carpentries.github.io/workshop-template/install_instructions/#r-1) to install R and RStudio.


### Quarto

Quarto is a scientific and technical publishing system built on Pandoc that we will use in RStudio.
Quarto has been bundled with RStudio in recent versions. If you have the most up-to-date RStudio version, you shouldn't to install Quarto.


:::::::::::::::::::::::::::::::::::::::  keypoints

## Version clarifications on Quarto and R/Rstudio

If you already have RStudio and R installed, please check if you have the most recent RStudio version and at least R version **4.3**, along with Quarto version **1.3.45** at least. The quarto document will not render without the most up-to-date versions. **The Quarto Package is not the CLI**.


You can check if you have the correct Quarto version by typing the following in the RStudio terminal:

```source
quarto --version
```

Your output should be:

```output
quarto --version
1.4
```

::::::::::::::::::::::::::::::::::::::::::::::::::

### R Packages

Install the following packages in RStudio: `rmarkdown`, `tidyverse`,`BayesFactor`, `patchwork`.
We will be covering the purpose of using packages and recap different ways to install and manage them in RStudio. Nonetheless, pre-installing the packages we will use for this workshop will save us some precious time, since installation time may vary among learners. Here are the steps for two possible approaches you may follow for completing this process:

::::::::::::::::::::::::::::::::::::::::: tab

### Using Menus and Tabs

1) Open RStudio

2) Select from the upper menu `Tools > Install packages...` or click on the `Packages` tab in the bottom-right section and then click on install. Either action will prompt a box dialog.

3) In the `Install Packages` dialog box, copy this text `rmarkdown, tidyverse, BayesFactor, patchwork` under the Packages field, make sure the option `install dependencies` is selected, keep other information unchanged, and then click `install`.

4) Don't be alarmed by the stop sign that will blink (and do not click on it, otherwise you will cancel the process) or the red text messages. Once the process completes, the cursor will be preceded by a greater-than sign `>`.

### Using the Console

Copy and paste each of the following functions to the console and wait for the process to complete:

```R
 install.packages("rmarkdown")
 install.packages("tidyverse") 
 install.packages("BayesFactor") 
 install.packages("patchwork")
```

or instead

```R
 install.packages(c("rmarkdown", "tidyverse", "BayesFactor", "patchwork"))
```

:::::::::::::::::::::::::::::::::::::::::
