---
title: "Managing Dependencies in R/RStudio"
teaching: 15
exercises: 5

questions:

- "How can I avoid the dependency hell problem and make my code reproducible in the future?"
- "How can I document my computational environment?"
- "How can I manage package and software dependencies in RStudio?"

objectives:

- "Understand the relevance of documenting the computational environment used in your project."
- "Recognize the importance of managing dependencies for RStudio projects."
- "Understand how to setup Groundhog to support R code reproducibility."

keypoints:

- "Run the `sessionInfo()` function to take a snapshot of your computational environment."
- "Groundhog is a handy tool for capturing your project's package dependencies."
- "Make your R scripts reproducible by replacing `library(pkg)` with `groundhog.library(pkg,date)`."

---


## Documenting your Computational Environment

Just sharing your code, data, and workflow does not magically make your research reproducible if we don’t know what language the code is written in or if functions change or are deprecated in newer versions, breaking your code.

Therefore, you should ask yourself: \* What are the versions of the packages used for my project? \* Will my project be usable on other systems or in the future? \* How do you deal with projects requiring different versions of a package?

Reproducibility is a spectrum that encompasses several actions. A first step to help prevent this problem is to carefully document the hardware and versions of software used in your analyses so that others can recreate that computing environment if needed.

In R, you can accomplish that by running the `sessionInfo()` function. [see CRAN Docs](https://cran.r-project.org/web/packages/details/vignettes/sessioninfo.html) This will create a snapshot of your computational environment, including your OS, R session/version, packages, their versions, and where they were installed from (e.g., CRAN, GitHub, or local Libraries). This information should be integrated into your README and project documentation.

After using this function, you will print:


[add image]

Try it yourself and check which versions you are using for each of the packages you have installed for the workshop.  
You may save it as a .txt file and save it in your project folder using the following command: `sessionInfo() %>% capture.output(file="session_info.txt")`


## Avoiding the Dependency Hell

Assume you have followed all the recommended practices to create reproducible projects. You chose RStudio/R, a free and open-source software; you have used relative paths and produced clean and clear code; your project directory and data files follow name conventions and are well-organized and beautifully documented. You have also documented your computational environment, as advised above.

Is that all? Well, not quite. Imagine investing significant time and effort into completing sophisticated data analysis, only to face a frustrating situation. When R gets upgraded and new package versions are released, everything suddenly starts crashing down. How can you ensure that the packages you rely on for your project remain on the same version consistently, even in the future?

One common reproducibility issue in research relates to software dependencies. "Dependency hell" is a colloquial term used to describe a situation in software development where the complex web of dependencies between different software components becomes difficult to manage or resolve. It typically occurs when multiple software libraries or packages have conflicting or incompatible requirements regarding the versions of other libraries or packages they rely on.

If you can only install one version of the shared software or library, you may have to find newer or older versions of the other software packages. But doing so can create more problems because those new versions might not work with other software you have installed, causing problems for your code to break and your publications not to render things correctly.

Let's say you're working on a data analysis project and have two R packages you're using: "package X" and "package Y."

`"package X" version 1.0.0 depends on "package Z" version 2.0.0. "package Y" version 1.5.0 depends on "package Z" version 1.0.0.`

You start your project by installing the latest versions of both packages. At this point, everything works fine, and you can proceed with your analysis using both packages. However, a few months later, you must reproduce your analysis and reinstall the packages. Unknown to you, "package Z" has been updated since your last installation, and the new version is incompatible with the older version that "package Y" depends on. When you try to run your analysis, you encounter errors or unexpected behavior because "package Y" is no longer compatible with the updated version of "package Z." 
This mismatch in dependencies can result in reproducibility issues, making it challenging to replicate your previous results.

You may think I can still look at the `sessionInfo()` .txt file and install older packages to make things work again, right? Well, that will require some extra work and affect your other projects that may rely the same packages with different versions. In this case, we need to take an additional action avoid this problem.  

## Enhancing Reproducibility with Groundhog

R/RStudio offers a vast ecosystem of packages and libraries that cater to a wide range of data manipulation, visualization, and analysis needs. However, harnessing the full potential of R often involves juggling a multitude of dependencies, which can lead to complex versioning issues, compatibility challenges, and time-consuming troubleshooting.

This is where Groundhog comes to the rescue! Groundhog (<https://groundhogr.com>) was designed to streamline and simplify R dependency management. With Groundhog, R users can effortlessly tackle the intricacies of package installations, version control, and environment isolation, making it the go-to solution for researchers seeking to optimize their R workflow.

## Advantages

-   You may use it for individual .R scripts and do not have to work within a project structure.

-   Users don't need to know about the "groundhog" package or how it works behind the scenes to use the code. Running the script will automatically handle the installation and loading of required packages or display an error if this process fails.

-   It gives real-time feedback when each package is loaded, verifying whether versions match or not.

## How does it work?

The `groundhog. library()` loads packages & their dependencies as available on a chosen date on CRAN. Packages get automatically installed if needed. Installation keeps, rather than replaces, existing versions of that package.

### Writing a New R Script with Reproducibility in Mind

The first step is to choose a date. Think of it as setting the stage for your coding, having as a starting point the first day of the month. In that case, you load all the essential packages tailored to that chosen date before creating your code:

```{r}
# Imagine we're in 2023-12-01
library(groundhog)
pkgs <- c(pkg1, pkg2, pkg3, pkg4)
groundhog.library(pkgs, '2023-12-01')
```
The advantage of this approach? When you run or make any edits to your script in the future, you can stick with your original date choice or update that by changing that date accordingly.

And if you're going all out with multiple `groundhog.library()` calls, you can set the date as a variable, making your script even more dynamic.

```{r}
groundhog.day <- '2023-12-01'
groundhog.library(pkgs, groundhog.day)
```

### Using GroundHog in Existing Scripts

Assume you developed a script months ago before you knew Groundhog even existed. The good news is that you can still apply it retroactively. To do so, you will need to set a `groundhog day` and adjust the library loading to `groundhog.library`.
The key question is: what date should you choose? We advise you to try the date the script was created or last saved as a proxy. If the documentation includes that information, go for it and test if things will render correctly. If not, try a month before or later, and it should work. See why documenting your work matters? We want to avoid guessing games.  

After applying Groundhog, let's see what our code in our .qmd file would look like.



[add image - before and after] 



### Other Packages that Support Code Reproducibility in R 

Groundhog is only one solution to help you circumvent the dependency hell in R. While it is simple to implement and relatively effective, it may not be the best option depending on your project goals.  It is beyond the scope of this workshop to explore other packages available for dependency management in R, but if this is a topic you would like to explore further, below, we list packages you may consider exploring: 


| Package                                                                 | Description                                                                                                                                                                                                        |
|--------------|-------------------------------------------------------|
| [RENV](https://cran.r-project.org/web/packages/renv)                    | The ***renv*** package is integrated with RStudio and helps you create reproducible environments for your ***R*** projects. Use ***renv*** to make your ***R*** projects more isolated, portable and reproducible. |
| [RANG](https://cran.r-project.org/web/packages/rang)                    | The ***rang*** package is geared towards reconstructing historical R computational environments which have not been completely declared.                                                                           |
| [MiniCRAN](https://cran.r-project.org/web/packages/miniCRAN/index.html) | The ***miniCRAN*** package makes it possible to create an internally consistent repository consisting of selected packages from CRAN-like repositories.                                                            |
| [Require](https://cran.r-project.org/web/packages/Require/index.html)   | The ***require*** package includes all-in-one management for packages in R focused around a single function, `Require,`                                                                                            |
| [Checkpoint](https://cran.r-project.org/web/packages/checkpoint)        | The ***checkpoint*** package allows you to install packages as they existed on CRAN on a specific snapshot date as if you had a CRAN time machine.                                                                 |

: Other Options to Manage Dependencies in R.
