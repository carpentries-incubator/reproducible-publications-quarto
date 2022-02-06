---
source: Rmd  
title: "Getting Your project set up with Version Control in RStudio"  
teaching: FIXME
exercises: FIXME
questions:
- How do I start or continue a project with Git versioning?
- What are the features in the RStudio Interface for working with Git?
- What are the basics of the Git versioning workflow?

objectives:
- Copy an existing project on Github to make contributions
- Open a project with Git versioning in RStudio
- Learn the basics of Git - pull, add, commit, push
- Make our first edits in a verison controlled project

keypoints:
- keypoint #1. Specific concept or syntax learned in this episode
- keypoint #2. Specific concept or syntax learned in this episode
---




### Using R projects and version control in RStudio
There are several options for working with R projects in RStudio. If you aren't already working in an R Project, you can create a new one. There are three options here:
1. Start a brand new R project and use version control from the start aka ""
2. Continue an R project that was started without version control and begin versioning
3. Continue an existing R project that already uses version control (i.e. download from GitHub)

![new r project options](../fig/05-new-project.PNG)

To start an R project, you would navigate to `File > new project` rather than just `File > new file`. 
1. Starting a new project (with version control)
![Add image starting new R project project type screen]()

*Note when you choose directory name, it will create a new directory in the directory you specified along with an .Rproj file of the same name. Avoid spaces here. underscores "_", dashes "-" or camel case "NewProject" is the recommended way to name this directory/file.

*Make sure the checkbox for git version control is checked. 

*Optionally, check the box next to Open in new session if you want it to appear in a new RStudio window. 

2. If you've already started an R project WITHOUT version control, you have the option to add version control retrospectively. You can also add existing R files to a project and version control if you've done neither. We won't go over that here, but to see an example please see episode from x lesson here: FIXME add link
![Add image of this option]()

3. Continue a version-controlled project
The final option is to continue a version controlled project. This is the option we will do.
![Add image new project version control option]()
![Add image import project from Git]()

But first, we need to navigate to GitHub and make a copy of the project for this workshop -> FIXME add instructions. 


Woo hoo! We have the project we are collaborating on for this workshop open in a new RStudio session!

Let’s take a second to pause and look at our materials in the folders to acquaint ourselves with them.
Now, how to use version control. 

### Using version control

The most simple workflow for version control (working on your computer only)
is referred to as "add" and "commit": 

But what do those words even mean?

add: definition  
Commit: definition 


If we are saving our work to a version control hosting cloud platform such as GitHub, 
our workflow gets a bit more complex, we add a "pull" and "push" step at the beginning and end of a work session. 

Pull > add > commit > push


Pull: definition  
 
Push: definition  

### Tips for working with Git

- You should pull each time you start working on your project after a hiatus, or before each edit if you know a team member is working at the same time. 
- Commit frequently, each commit should be a distinct set of edits which you can summarize in 50 characters or less. Don’t add a bunch of unrelated edits to the same commit, it makes it harder to look back through your “snapshots” and find the right one if you need to. 
- At the end of your work session (or more frequently if you are working at the same time as team members), “push” your commits to the remote repository - this is the only way your local changes get added to your team’s remote repository.

This pull, add, commit, push routine will become second nature. Pulling at the beginning and pushing at the end of your work session becomes a sort of ritual that marks the beginning and end of your work session. 

Show how to commit

> ## Tip: add files that don’t need to be tracked to the .gitignore
> Such as data files, outputs, references (you want to save those, but you 
> aren’t actively making changes to them so we don’t need to “track” them through 
> version control. Mostly scripts and rmd files need tracking
{: .callout}

> ## Challenge: (optional) Add the following files to the .gitignore 
>
{: .challenge}

### Your first edit

Demonstrate an edit

> ## Challenge: Find the FIXMEs and add the Markdown formatting indicated. 
>
{: .challenge}

Make a commit when you’re done with a message that is descriptive of the edits made. 

