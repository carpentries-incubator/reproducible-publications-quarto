---
title: "Creating and sharing reproducible environments using Renv"
teaching: 15
exercises: 10
questions:
- "How can I enhance reproducibility amongst collaborators, present and future?"
- "What is Renv?"
- "How Renv can support reproducibility?"

objectives:
- "Learn how to use renv in an RStudio project"


keypoints:
- "renv is a handy tool for capturing your project's package dependencies"

---

## Enhancing reproducibility with renv

renv is an R package that keeps track of your project's dependencies, specifically, the version of the R interpreter your project is using and the versions of any packages referenced by your R scripts.  renv can also download and install package versions according to a project's requirements.  This makes it easy for a downstream user to run an R project in the same environment in which it was originally developed.

In our workshop project, renv has already been set up--- you can tell by the presence of a file `renv.lock` in the project's root directory.  This file records package versions and other information.

Every time you open a project for which renv has been set up, renv automatically runs and checks that the package versions you have installed on your computer match those of the project.  If they match, there is nothing to do (perhaps that was the case for you today).  But if there are any mismatches (as might have happened to you today), renv will print a warning resembling the following:

```
* Project '~/Desktop/myproject' loaded. [renv 0.16.0]
* The project library is out of sync with the lockfile.
* Use `renv::restore()` to install packages recorded in the lockfile.
```

If this happens, simply run `renv::restore()` from the console pane to download and install the package versions needed to match the project's requirements.  For example, if the project uses tidyverse 1.3.2 and you have an older version tidyverse 1.3.1 installed on your computer, renv will upgrade your RStudio installation to tidyverse 1.3.2.  (This works conversely as well: if the project uses an older version of a package you have installed, renv will attempt to download and install the older version for you.  Don't worry about losing the newer version.  renv ensures that all versions of all packages remain installed on your computer, available to be used by projects as needed.)

A few more points on using renv.  To start using renv on a new project, run these commands in the console pane:

```
install.packages("renv")
library(renv)
renv::init()
```

This creates the initial `renv.lock` file.  Then, whenever you start using a new package (or otherwise change your project's dependencies), run `renv::snapshot()` to update the lockfile.  Finally, if you are using git and start using renv, you will notice that renv creates several files and directories in addition to `renv.lock`.  Go ahead and commit the files to your project's git repository.
