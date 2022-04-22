---
source: Rmd  
title: "Adding Code-Generated Plots and Figures"  
teaching: 50
exercises: 20
questions:
- "What is Knitr?"
- "What are code chunks and how they are structured?"
- "How can you run code from your rmd document?"
- "What are global knitr options?"
- "What are global chunk options?"
objectives:
- "Understand the syntax of a code chunk."
- "Learn how to insert run-able blocks of code to integrate into your report"
- "Learn how to source external scripts to run within an rmd document."
- "Learn about using global knitr options and global chunk options"
keypoints:
- "Knitr will render your code and R markdown-formatted text and output your document format of choice"
- "Code chunks are runable piece of R code. Each time you knit the document, calculations and plots will be run and displayed"
- "Options for code chunks can be set at the individual level or at the global level"
---

## Utilizing the Code Features of R Markdown

We've learned about the text-formatting options of R Markdown, now let's dive into the code portion of R Markdown documents. R Markdown flips around the defaults of code and text in the documents. Instead of priortizing the code and making you comment out (#) text, they priortize text and force you to specially signal the code portions. How do you signal to R the difference between code and text when you're not using code commments (#)? That's where "Code Chunks" come into play (Yes that's RStudio's technical name for them). Instead of R Markdown's rendering system processing the markdown styling into the final output, Code chunks are sent to a preceding stage of processing by Knitr, which "knits" the code output and text together. Secondly, rmarkdown processes the code output and displays it in the document format of our choice - i.e. Knitr runs the lines of code for a plot in a code chunk, joins it to the markdown text portions, and rmarkdown outputs that as an html document. 

## What is Knitr?

But what is Knitr? Knitr is the engine in RStudio which creates the “dynamic” part of R Markdown reports. It’s specifically a package that allows the integration of R code into the html, word, pdf, or LaTex document you have specified as your output for R Markdown. It utilizes Literate Programming to make research more reproducible. There are two main ways to process code with Knitr in R Markdown documents:

1. Code Chunks
2. Inline Code

First, we're going to talk about code chunks more substantial portions of code into our narrative such as figures and plots. There are a plethora of options that become available to us when using code chunks so this tends to be the more complex part of R Markdown documents. Now, sometimes you just need to do a quick calculation - like a count of total observations in your data or the mean of one of your variables. In those cases, it may not be worth setting up a code chunk to calculate those values, so after code chunks we will see how to add inline code - which allows one to add a quick line of code or single function to be executing within the text portion of the document. But let's start with code chunks.

## Inserting Code Chunks

Code chunks are better when you need to do something more sophisticated with your code than inline code, such as building plots or tables.  They also incorporate syntax which allows modifications to how that code is rendered and styled in your final output. We’ll learn more about that as we walk through the “anatomy” of a code chunk.

### Basic Anatomy of the Code Chunk

You can quickly insert chunks like these into your file with:  
- the keyboard shortcut Ctrl + Alt + I (OS X: Cmd + Option + I)  
- the Add Chunk command in the editor toolbar  
- or by typing the chunk delimiters {r} and ```.  

The most basic (and empty) code chunk looks like so:

![blank Rmd code chunk](../fig/07-blank-code-chunk.PNG)

Other than our backticks ``` for code chunks that surround the code top and bottom, the only **required** piece is the specified language (r) placed between the curly brackets. This indicates that the language to read the code is R.

> ## Fun fact: Other Programming Languages
> Although we will (mostly) be using R in this workshop, it’s possible to use other programming or markup languages. For example, we have seen that we can use LaTeX code for equations. You can also use python and a handful of other languages, so if R is not your preferred programming, but you like working in the RStudio environment, don’t despair! Other options for languages include: sql, julia, bash, and c, etc. It should be noted however, that some languages (like python) will require installing and loading additional packages. 
{: .callout}

## Add a Code Chunk

Ok, let's add some code! There are already some plots included in our code but as static images. This time, we are going to opt to add these plots as code chunks - which are also more reproducible and easier to update. This is because, as with our inline code, this assures that if there are any changes to the data, the plots update automatically. This also makes our life easier because when there’s a change we don’t have to re-generate plots, save them as images and then add them back in to our paper. This will potentially help prevent version errors as well! So we’re actually going to go ahead and add a few plots with code chunks.

First, though, let's open a new `.rmd` document to get a look at how code chunks work before integrating them into our paper. 

Again, open a new document by navigating to `File > New File > R Markdown`. Add the title `Code-Chunk-Test`. 

Let's first delete the generic text because we don't need it at this point (all except the first code chunk that is - we'll get back to that in a second).

FIXME - add fig of new document with just the setup code chunk

 We’ll start a new code chunk by typing our our starting backticks & r between curly brackets. (in your own workflow you may want to add the ending three backticks as well so you don’t forget after adding your code - it's a common mistake):

Now, let's open our `03_HR_analysis.R` script in our `code` folder. Copy the code and paste it in between the two lines with backticks and `{r}` in our `DataPaper-ReproducibilityWorkshop.rmd` file.

FIXME update screenshot to display in new document ![heartrate code in chunk](../fig/07-heartrate-code.PNG)

> ## Tip:
> There's actually a button you can use in the RStudio menu to generate the code chunks automatically. Automatic code chunk generation is available for several other languages as well. Also, you can use the keyboard shortcut `ctrl`+`alt`+`I` for Windows and `command`+`option`+`I` for Mac. 
> ![auto create code chunk](../fig/07-auto-code-chunk.PNG)
{: .callout}

Now, to check to make sure our code renders, we could click the "knit" button as we have been doing. However, with the code chunks we have other opportunities for rendering. 

1) Knit button - knitting will automatically run the code in all code chunks
![code chunk with plot1 code](../fig/07-run-code-with-knit.PNG) 

2) Run from code chunk (green play button on the right top corner)

![run from code chunk](../fig/07-heartrate-code-runfromchunk.png)

3) Run menu

![run code menu](../fig/07-rmd-run-options.PNG)

4) Keyboard shortcuts: 

**Task**	| **Windows & Linux**	| **macOS**
---       |---                  |---
Create a code chunk | Ctrl + Alt + I | Cmd + Option + I
Run all chunks above |	Ctrl+Alt+P	| Command+Option+P
Run current chunk	| Ctrl+Alt+C	| Command+Option+C
Run current chunk	| Ctrl+Shift+Enter	| Command+Shift+Enter
Run next chunk	| Ctrl+Alt+N	| Command+Option+N
Run all chunks	| Ctrl+Alt+R	| Command+Option+R
Go to next chunk/title	| Ctrl+PgDown	| Command+PgDown
Go to previous chunk/title	| Ctrl+PgUp |	Command+PgUp

> ## Time to Knit!
> Use one of the above options to run your code. 
{: .checklist}

Wait... what's all that output in our document? We don't want that in our paper! 

FIXME - update screenshot
![Heart rate code no options for code chunk](../fig/07-HR-output-no-options.PNG)

This happens because the output from running code (messages, results, warnings, etc.) get's added to the R Markdown document instead of being printed to the console. Let's see about adjusting the output to make it look better with code chunk rendering options. 

## Code Chunk Naming and Options

### Name Your Code Chunk

Before we get to fixing how our code output looks, let's make sure to give our code chunk a name. While not necessary for running your code, it is good practice is to give a name to each code chunk because it gives the chunk a unique identifier which allows for more advanced options (such as cross-referencing) to work with your rmd files later on:

`{r chunk-name}`

Some things to keep in mind
- The chunk name is the only value other than r in the code chunk options that doesn’t require a tag (i.e. `echo =` )
- The chunk label has to be unique (i.e.you can't use the the same name for multiple chunks)

We’ll see in a bit where this code chunk label comes in handy. But, for now let's go back and give our first code chunk a name:

`{r fig3-heartrate}`

> ## Tip: Don't use spaces, periods or underscores in code chunk labels
>Try to avoid spaces, periods (.), and underscores (_) in chunk labels and paths. If you need separators, you are recommended to use hyphens (-) instead. For example, setup-options is a good label, whereas setup.options and chunk 1 are bad; fig.path = 'figures/mcmc-' is a good path for figure output, and fig.path = 'markov chain/monte carlo' is bad. See more at: [https://yihui.org/knitr/options/](https://yihui.org/knitr/options/)
{: .callout}

### Code Chunk Options

There are over 50 different code chunk options!!! Obviously we will not go over all of them, but they fall into several larger categories including: code evaluation, text output, code style, cache options, plot output and animation. We’ll talk about a few options for code evaluation, text output and plot output specifically.

> ## Tip: Learn more about code chunk options
> Find a complete list of code chunk options on Knitr developer, Yihui Xie's, [online guide to knitr](https://yihui.org/knitr/options/). Or, you can find a brief list of all options on the R Markdown Reference guide on page 3 accesible through the RStudio Interface by navigating to the main menu bar `Help > Cheat Sheets > R Markdown Reference Guide`.
{: .callout}

The chunk name is the only value other than r in the code chunk options that doesn’t require a tag (i.e. the "= VALUE" part of `option = VALUE`). So these chunk options will always require a tag whose syntax looks like:

`{r chunk-label, option = VALUE}`

the option always follows the code chunk label (don't forget to add a `,` after the label either). 


#### Common text output & code evaluation options: 

##### Code evaluation option

**include** = (logical) whether to include the chunk output in the output document (default TRUE).

##### Text output options

**eval** = (logical or numeric) TRUE/FALSE to evaluate (or not) or a numeric value like c(1,3) (only evaluate expressions 1 and 3). 
**echo** =  (logical or numeric - following the same rules as above) whether to display source code or not.  
**results** = (logical or character) text output of the code can be hidden (hide or FALSE), or delineated in a certain way (default 'markup').       
**warning** = (logical) whether to display the warnings in the output (default TRUE). FALSE will output warnings to the console only.       
**message** = (logical) whether or not to display messages that appear when running the code (default TRUE).
 
 
> ## CHALLENGE 9.1 - Rendering Codes
> How will some hypothetical code render given the following options?
> `{r global-chunk-challenge, eval = TRUE, include = FALSE}`
> 
>> ## SOLUTION
>> The expressions in the code chunk will be evaluated, but the outputed figures/plots will not be included in the knit document.   
>> When might you want to use this?   
>> If you need to calculate some value or do something on your dataset for a further calucation or plot, but the output is not important to be included in your paper narrative. 
> {: .solution}
{: .challenge}

> ## CHALLENGE 9.2 - add options to your code  
> Add the following options to your code:  
> echo = FALSE, message = FALSE, warning = FALSE, results = FALSE  
> 
> What will this do?  
>> ## SOLUTION
>> ![solution to 9.3](../fig/07-solution-9.3.PNG)    
>>
>> These options mean the source code will not be printed in the knit html document, messages from the code will not be printed in the knit html document, and warnings will not be printed in the knit html document (but will still output to the console). Plots, figures or whatever is printed by the code WILL show up in the final html document.  
> {: .solution}
{: .challenge}

### Caption your code chunk output:

The options we just looked at focus on code evaluation and text output. However, we have another set of options that deal with how plot or figure outputs look at act. Many of the options start with `fig.`. The one we will use today allows us to add a caption to our figure. Again, this is an optional feature, but if you need (or want) to add captions to your publication, it is straightforward to do in code chunks. 

The caption information also resides between your brackets at the beginning of the chunk: `{r}`

the tag is `fig.cap` followed by a `=` and the captions within quotes `"caption for figure"`

> ## Challenge 9.3: Add a caption to Figure 3
> Let's add a caption to our heartrate figure. Add the caption:
> 
> > "Fig 3: Mean heart rate of stress and control groups at baseline and during intervention."
> 
> > ## Solution
> > so, you should end up with the following in your code chunk:
> > ~~~
> > {r fig3-heartrate, echo = FALSE, message = FALSE, warning = FALSE, results = FALSE, fig.cap = "Fig 3: Mean heart rate of stress and control groups at baseline and during intervention."}
> > ~~~
> > {: .language-r}
> {: .solution}
{: challenge}

Let's knit one more time to see if our figure outputs how we'd like and has a caption.

> ## Time to Knit!
> Let's try that again 
{: .checklist}


### Global Code Chunk Options:

Now we’ve learned how to create a code chunk and learned about options for adjusting how that code renders in our output document. However, let's direct our attention back to the first code chunk in this document that I asked you not to delete. 

The code looks like: 

`knitr::opts_chunk$set()`

FIXME add screenshot of code

This is an option to globally set options for the entire R Markdown document. 

With our first plot we set the four options that adjust how that one chunk renders. However, we may end up with quite a few code chunks in our paper. For example, if we have 10 code chunks in the final paper, can you imagine how much work it would be to add the options in manually each time? and if we need different options for different figures, it could be a lot of work to keep track of what options we’re using throughout the paper. We can automate setting options by adding this special code chunk at the beginning of the document. Then, each code chunk we add will refer to those “global” options when it runs.

To test this, let's add the options we put in our code chunk (and make sure to delete them from the code chunk with the heart rate code)

In the `()` after the `knitr::opts_chunk$set()` add the options:

`knitr::opts_chunk$set(echo = FALSE, message = FALSE, warning = FALSE, results = FALSE)`

> ## Tip: Overiding global options  
> What if you want most of your code chunks to render with the same options (i.e. echo = FALSE), but you just have one or two chunks that you want to tweak the options on (i.e. display code with echo = TRUE)? Good news! The global options can be overwritten on a case by case basis in each individual code chunk. Test this by adding `echo = TRUE` to your code chunk in your document and knitting. Did you override the global settings successfully?
{: .callout}

#### Add global options to our paper

Now, let's navigate back to our paper `` and add global options there. 

To set global options that apply to every chunk in your file, we will call `knitr::opts_chunk$set()` in a new code chunk right after our yaml header (name the new code chunk `setup`.

Knitr will treat each option that we add to this call as default settings for all code chunks. However, we will need to set the options for this code chunk in the first place! so make sure to use `include = FALSE` as in the generic R Markdown document.

In the `()` after the `knitr::opts_chunk$set()` add the options:

`knitr::opts_chunk$set(echo = FALSE, message = FALSE, warning = FALSE, results = FALSE)`

Alright! That sets us up well for adding code chunks into our paper (which we will do next)


> ## CHALLENGE 9.5 (optional) global & individual code chunk options  
>
> How would appear in our html document if we knit a code chunk with the following options?  
> `{r challenge-5, warning = TRUE, echo = TRUE}`
>
> ...considering the global chunk settings were as listed: 
> `knitr::opts_chunk$set(echo = FALSE, include = FALSE)`  
>> ## SOLUTION  
>> In this case, the global settings are set so neither the code nor the output will display. However, the individual chunk reverses the echo setting so the code will display, and it also indicates that any warnings the code renders should output too. The outputs of the code would still not be displayed (include = FALSE) The hypothetical situation for this configuration may be for debugging while writing the rmd document.   
> {: .solution}  
{: .challenge}










