---
title: Pre-workshop Setup
---**Requirements:**

<h2><b>PART I:Install Software and create GitHub Account</b></h2>

- Create Github account (use existing or create new account) 
- Install Git  
- Install R & RStudio (Two separate installations: if you are on a windows device, you may need <a href="https://cran.r-project.org/bin/windows/Rtools/">Rtools</a>)
- Install <a href="https://quarto.org/docs/get-started/">Quarto CLI (version 1.2)</a>


{% include install_instructions/github.html %}

{% include install_instructions/git.html %}


<br>


<h2><b>PART II: Install R/Rstudio and Quarto</b></h2>


{% include install_instructions/r.html %}

{% include links.md %}

<br>


## Quarto 

You will need to install Quarto from <a href="https://quarto.org/docs/get-started/">Quarto.org</a>. Open the Setup Wizard to begin the install.
Keep the defaults and select <b>Next</b> until the install Finishes.

> ## Version clarifications on Quarto and R/Rstudio
>
If you already have Rstudio and R installed, please check if you have the most updated <b>2022.07</b> Rstudio and at least R version <b>4.2</b>, along with Quarto version <b>1.2</b>. The quarto document will not render without the most updated versions. <b>The Quarto Package is not the CLI</b>
{: .keypoints} 


You can check if you have the correct Quarto version by typing the following in the Rstudio terminal:


~~~
quarto --version
~~~
{: .source}

Your output should be:

~~~
quarto --version
1.2.269
~~~
{: .output}

<br>

## R Packages

We will be using a feature called <a href="https://rstudio.github.io/renv/articles/renv.html">Renv</a>. Renv helps manage library paths and project specific states.
However, in case there are issues with the workflow, we will use the following packages in the workshop. 


Install the following packages in RStudio: `bookdown`, `tidyverse`, `rticles`,`BayesFactor`, `patchwork` , `rprojroot`. 
We will be covering the purpose of using packages and recap different ways to install and manage them in RStudio. Nonetheless, pre-installating the packages we will be using for this workshop will save us some precious time since installation time may vary among learners. Here are the steps for two possible approaches you may follow for completing this process: 

*Using Menus and Tabs*

1) Open R studio
2) Select from the upper menu `Tools > Install packages...` or click on the `Packages` tab in the bottom-right section and then click on install. Either action will prompt a box dialog. 
3) In the `Install Packages` dialog box, copy this command `bookdown, tidyverse, rticles, BayesFactor, patchwork, here` under the Packages field, make sure the option `install dependencies` is selected, keep other information unchanged, and then click `install`. 
4) Don't be alarmed by the stop sign that will blink (and do not click on it otherwise you will cancel the process) or the red text messages. Once the process completes the cursor will be preceeded by a greater-than sign `>`.

1) Copy and paste one of the following functions to the console and wait for the process to complete:
~~~

 install.packages("bookdown")
 install.packages("tidyverse") 
 install.packages("BayesFactor") 
 install.packages("patchwork")
 install.packages("here")

~~~
{: .source}
 
 or 

~~~
  
 install.packages(c("bookdown", "tidyverse", "BayesFactor", "patchwork", "here"))

~~~
{: .source}

2) Don't be alarmed by the stop sign that will blink (and do not click on it otherwise you will cancel the process) or the red text messages. Once the process completes the cursor will be preceeded by a greater-than sign `>`.

You may close Rstudio and all packages will remain installed when you reopen it. 
