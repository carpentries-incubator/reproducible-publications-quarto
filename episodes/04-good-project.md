---
source: Rmd  
title: "Good Practices for Research Projects in RStudio"  
teaching: FIXME
exercises: FIXME
questions:
- What are good research project management practices?
- What is an R Project file?
- How do you start a new or open an existing R Project?
- How do you use version control to keep track of your work?

objectives:
- Best pratices for working on research projects involving data
- The purpose of using .Rproj files
- Using version control in RStudio
- Starting or continuing an R project

keypoints:
- keypoint #1. Specific concept or syntax learned in this episode
- keypoint #2. Specific concept or syntax learned in this episode
---



## Managing Research Projects in R
Now that we’ve learned some of the basics of authoring in RStudio with R Markdown documents, let’s take a step back and talk about research project management as a whole. The ability to integrate code and narratives is a major advantage of the RStudio environment, especially consideringthe scientific process is naturally incremental, and many projects start life as random notes, some code, then a manuscript, and eventually everything ends up a bit mixed together. To complicate things further, we are often working with other collaborators, lab members, graduate students, faculty from the same or different institutions, which makes it that much more difficult to keep projects organized. When you throw data into the mix (sometimes huge amounts of it!), it’s integral to use best practices to maintain the integrity of your analysis and to be able to publish high quality and reproducible research. Using Rmarkdown is a powerful tool, but it can’t be fully utilized unless your project documents, scripts and other files are well-organized. So let’s take a look at RStudio’s features to manage projects and discuss some of the best practices when working with data and collaborators. 

Project Stress Points
We often have organizational or logistical stress points in our research that may become breaking points, especially when it comes to working with collaborators, returning to a project after a hiatus, or dealing with data and scripts. Let’s discuss three of those common stress points:

File/folder disorganization
I.e. cannot find files on your computer
Unsure what is the most recent version of your work
Path issues when trying to run code 
Reviewers or colleagues cannot understand or run code/analyses
Storage and sharing issues
Files are only saved to your computer and are vulnerable to computer/harddrive failure
When working with collaborators, they (or you) don’t share the files needed
Files are shared via email attachments
Difficult to know if you have the latest version of documents
Losing track of project status
You cannot remember where you are in a project after being away for an extended period (or what you worked on the previous day (no judgement))
You aren’t sure what you should be working on next
You have various to-do notes spread across your office or home (or never write them down in the first place)

> ## Discussion
> To what extent do these stress points affect your research projects? Are there additional issues that you’ve encountered that slow down or derail your work?
{: .challenge}

> ## Discussion: Antidotes
> What are some practices you implement to keep yourself on track with your projects?
{: .challenge}

## Antidotes

A good project layout will ultimately make your life easier:
- It will help ensure the integrity of your data
- It makes it simpler to share your code with someone else (a lab-mate, collaborator, or supervisor)
- It allows you to easily upload your code with your manuscript submission
- It makes it easier to pick the project back up after a break.
- It makes your research reproducible!

We’ll discuss three aspects of project management and then implement those practices for the remainder of this workshop in the RStudio environment.

1. File/ Folder Organization
2. Storage & Sharing
3. Using Version Control

Then, we’ll get started on our project!

## Project File/Folder Organization
### Important principles:  

Although there is no “best” way to lay out a project, there are some general principles to adhere to that will make project management easier:  
**Practice good file-naming practices**
FIXME add content  
**Keep your project within one folder**  
FIXME add content  
**Use relative paths**  
This goes hand-in-hand with keeping your project within one “root” directory. If you use complete paths to say, read in your data to RStudio and then share your code with a collaborator, they won’t be able to run it because the complete path you used is unique to your system and they will receive an error that the file is not found. That is why one should always use relative paths to link to other files in the project. I.e. “where is my data file in relation to the script I’m reading the data into?” The practice of using relative paths is made easier by having a logical directory set up and keeping all project files within one root project folder. For review on relative vs. complete paths please see: FIXME add  
**Treat data as read only**  
This is probably the most important goal of setting up a project. Data is typically time consuming and/or expensive to collect. Working with them interactively (e.g., in Excel or R) where they can be modified means you are never sure of where the data came from, or how it has been modified since collection. It is therefore a good idea to treat your data as “read-only”.
Keep your “dirty” and “clean” data separate
However, in many cases your data will be “dirty”: it will need significant preprocessing to get into a format R (or any other programming language) will find useful. Storing these scripts in a separate folder, and creating a second “read-only” data folder to hold the “cleaned” data sets can prevent confusion between the two sets. You should have separate folders for each: raw data, code, and output data/analyses. You wouldn’t mix your clean laundry with your dirty laundry, right?  
**Treat generated output as disposable**
Anything generated by your scripts should be treated as disposable: it should all be able to be regenerated from your scripts.
There are lots of different ways to manage this output. Having an output folder with different sub-directories for each separate analysis makes it easier later. Since many analyses are exploratory and don’t end up being used in the final project, and some of the analyses get shared between projects.  
**Include a README file**  
FIXME With project details such as?  

> ## Tip: Suggestions from Good Enough Practices for Scientific Computing
> Good Enough Practices for Scientific Computing gives the following recommendations for project organization:  
> 1. Put each project in its own directory, which is named after the project.
> 2. Put text documents associated with the project in the doc directory.
> 3. Put raw data and metadata in the data directory, and files generated during cleanup and analysis in a results directory.
> 4. Put source for the project’s scripts and programs in the src directory, and programs brought in from elsewhere or compiled locally in the bin directory.
> 5. Name all files to reflect their content or function.
> Additionally, we'd recommend to include README, LICENSE, and CITATION files!
{: .callout}

For our project we’re working in today, we used the following setup for folders and files:

**code:** contains the scripts that generate the plots and analysis (found in `output/plots`)  
    **/functions:** contains custom functions written for the data pre-processing  
**data:** this folder contains the raw and cleaned data files  
	**/foodchoice_data:** contains the individual data files from food choice trials  
**output:**
	**/data:** contains the output data file after applying custom pre-processing function  
	**/plots:** contains pdfs of the plots generated from the plot scripts in the code folder  
**pub:** All files needed for the publication of the research project  
	**/source:** .Rmd file for the paper and additional files needed for rendering the paper  
    **/fig:** contains the images created specifically (not through the analysis scripts) for the paper  
	**/output:** contains the final html output of the Rmd paper  
**R-repro-pub.Rproj:** R project file that lives in the root directory.  
**README.md:** A detailed project description with all collaborators listed.
**CITATION.md:** Directions to cite the project.
**LICENSE.md:** Instructions on how the project or any components can be reused.  

Again, there are no hard and fast rules here, but remember, it is important at least to keep your raw data files separate and to make sure they don’t get overridden after you use a script to clean your data. It’s also very helpful to keep the different files generated by your analysis organized in a folder.

*what’s this .Rproj file? We’ll explain next.

### Working in R Projects
One of the most powerful and useful aspects of RStudio is its project management functionality. We’ll be using an R project today to complement our R Markdown document and bundle all the files needed for our paper into a self-contained, reproducible project. An `.Rproj` file makes it easy to open a project - just navigate through your file system to get to your project directory and double click on the .Rproj file. This will automatically open RStudio and start your R session in the same directory as the `.Rproj` file. RStudio projects have the added benefit of allowing you to open multiple projects at the same time each open to its own project directory. This allows you to keep multiple projects open without them interfering with each other.


#### Features of R Projects

FIXME add content
Version control
R History saved

Modular - All your data, plots and scripts will now be relative to the project directory. (This is true whether you use a .Rproj file or not, but re-emphasizes the fact.

Other features?

> ## Tip: R Project in “root” folder
> `.Rproj` files must be in the root directory of your project folder/directory. What is the root directory?  
{: .callout}

### Storage and Sharing
Backup/Storage principles
3-2-1 rule
For more information on the 3-2-1 rule, see: https://www.uschamber.com/co/run/technology/3-2-1-backup-rule 

You should avoid only having a copy of your project on your personal, work computer or a lab computer at all costs. At the very least, you should backup your project into cloud storage (either provided by your university or paid for yourself). Common cloud storage platforms include Google drive, Box, OneDrive, Dropbox, etc. 

If your research project involves code, the best way to make sure you have your work backed up AND keep track of your code and data is to use a version control hosting service such as GitHub (2 birds one stone). 

Variations of backup plans may look like: 
Copy on personal computer > copy on GitHub < copy on collaborators computer
Adheres to 3-2-1 rule: yes. 3 copies, 2 different media (disk/cloud), and 1(actually 2!) copy offsite
Copy on personal computer > copy on GitHub
Adheres to 3-2-1 rule: not quite. Only 2 copies, 2 different media, 1 offsite
copy on GitHub > Copy on personal computer > copy on external harddrive
Adheres to 3-2-1 rule: yes! 3 copies, 2 different media, 1 offsite (maybe 2 offsite if your external harddrive is separate from your computer)

Version Control hosting services 
The main three are GitHub, GitLab, and BitBucket  
**GitHub:** 
+Most popular version control hosting service
+Free private and public repositories
+Can use GitHub pages to create free websites for your project
+Built-in project management capabilities
-Not open source (owned by Microsoft) so subject to terms of use changes or fees

**GitLab:**
+Free private and public repositories
+Built-in project management capabilities
+Open source - completely free!
-Less popular than GitHub (less visibility for your project)

**BitBucket:**
+Free private and public repositories
+Built-in project management capabilities
+Can be used with Git and Mercurial (another type of version control system)
-Less popular than GitHub (less visibility for your project)
-Not open source (owned by Atlassian) so subject to terms of use changes or fees

Source: https://www.linkedin.com/pulse/demystifying-git-vs-github-atlassian-bitbucket-gitlab-pawan-verma?trk=read_related_article-card_title 

We will proceed using GitHub. 

### Using Version Control
Ok, now let’s talk about implementing version control in your project through RStudio! But first… the difference between Git/GitHub
What is Git?

What is GitHub?
Include issues/project management benefits

What are the benefits of Version Control

### Using R projects and version control in RStudio
1. Starting a new project (with version control)
![Add image starting new R project project type screen]()
![Add image create new project version control checked]()

2. Continue a version-controlled project
![Add image new project version control option]()
![Add image import project from Git]()

To see how to add an existing project you're working on in RStudio to an Rproj file and add version control please see episode from x lesson here: FIXME add link

Woo hoo! We have the project we are collaborating on for this workshop open in a new RStudio session!

Let’s take a second to pause and look at our materials in the folders to acquaint ourselves with them.
Now, how to use version control. 
### Using version control
The simple workflow for version control is: 
Pull > commit > push
First, define Repository
Pull: definition
Commit: definition
Push: definition
You should pull each time you start working on your project after a hiatus, or before each edit if you know a team member is working at the same time. 
Commit frequently, each commit should be a distinct set of edits which you can summarize in 50 characters or less. Don’t add a bunch of unrelated edits to the same commit, it makes it harder to look back through your “snapshots” and find the right one if you need to. 
At the end of your work session (or more frequently if you are working at the same time as team members), “push” your commits to the remote repository - this is the only way your local changes get added to your team’s remote repository. 
Show how to commit
Tip: add files that don’t need to be tracked to the .gitignore
Such as data files, outputs, references (you want to save those, but you aren’t actively making changes to them so we don’t need to “track” them through version control. 
Mostly scripts and rmd files need tracking

> ## Challenge: (optional) Add the following files to the .gitignore 
>
{: .challenge}
### Your first edit

Demonstrate an edit

> ## Challenge: Find the FIXMEs and add the Markdown formatting indicated. 
>
{: .challenge}

Make a commit when you’re done with a message that is descriptive of the edits made. 

