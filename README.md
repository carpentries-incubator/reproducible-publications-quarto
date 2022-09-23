# Introduction to Reproducible Publications with RStudio (Quarto)

This version is still in progress. We are updating the Rmarkdown content with Quarto.

[![Create a Slack Account with us](https://img.shields.io/badge/Create_Slack_Account-The_Carpentries-071159.svg)](https://swc-slack-invite.herokuapp.com/)

## Contributing

We welcome all contributions to improve the lesson! Maintainers will do their best to help you if you have any
questions, concerns, or experience any difficulties along the way.

This lesson has a supplementary repository with the [project example](https://github.com/carpentries-incubator/Reproducible-Publications-with-RStudio-Example) used for challenges and exercises.

We'd like to ask you to familiarize yourself with our [Contribution Guide](CONTRIBUTING.md) and have a look at
the [more detailed guidelines][lesson-example] on proper formatting, ways to render the lesson locally, and even
how to write new episodes.

Please see the current list of [issues](https://github.com/carpentries-incubator/Reproducible-Publications-with-RStudio/issues) for ideas for contributing to this
repository. For making your contribution, we use the GitHub flow, which is
nicely explained in the chapter [Contributing to a Project](http://git-scm.com/book/en/v2/GitHub-Contributing-to-a-Project) in Pro Git
by Scott Chacon.
Look for the tag ![good_first_issue](https://img.shields.io/badge/-good%20first%20issue-gold.svg). This indicates that the maintainers will welcome a pull request fixing this issue.


## Maintainer(s)

Current maintainers of this lesson are:

* Renata Curty (rcurty)
* Torin White (torwhite)
* Ian Lessing (ilessing)
* kristi Liu (kristi-sara)
* Amanda Ho (apandas)


## Authors

A list of contributors to the lesson can be found in [AUTHORS](AUTHORS)

## Citation

To cite this lesson, please consult with [CITATION](CITATION)

[cdh]: https://cdh.carpentries.org
[cdh-topic-tags]: https://cdh.carpentries.org/the-carpentries-incubator.html#topic-tags
[change-default-branch]: https://docs.github.com/en/github/administering-a-repository/changing-the-default-branch
[community-lessons]: https://carpentries.org/community-lessons
[lesson-example]: https://carpentries.github.io/lesson-example

**Thanks for contributing to The Carpentries Incubator!**
This repository provides a blank starting point for lessons to be developed here.

A member of the [Carpentries Curriculum Team](https://carpentries.org/team/)
will work with you to get your lesson listed on the
[Community Developed Lessons page][community-lessons]
and make sure you have everything you need to begin developing your new lesson.

## What to do next

Before you begin developing your new lesson,
here are a few things we recommend you do:

* [ ] If you're going to be developing lesson material for the first time
  according to our design principles,
  consider reading the [Carpentries Curriculum Development Handbook][cdh]
* [ ] Consult the [Lesson Example][lesson-example] website to find out more about
  working with the lesson template  -- specifically https://carpentries.github.io/lesson-example/05-rmarkdown-example/index.html 
  to see rmarkdown example
* [ ] Update this README with relevant information about your lesson  
  and delete this section


\* To set the URL on GitHub, click the gear wheel button next to **About**
on the right of the repository landing page.
The lesson URL structure is **https://carpentries-incubator.github.io/<repository-slug\>**:
a repository at https://github.com/carpentries-incubator/new-lesson/ will have pages at
the lesson URL https://carpentries-incubator.github.io/new-lesson/.


## R Markdown vs. Github Markdown
Note the two flavors of markdown are different. Some formatting tips:

- **Line Breaks:** must have two spaces at the end of the line or manually add a break <br>

### Lesson-specific formatting 
For formatting & consistency's sake, we should :
1) for examples that don't need to be input to the paper example rmd file, DON'T use `{: .source}` callouts but DO use  \``` \``` so the markdown doesn't render. For short partial line chunks ` ` can be used. 
2) use `{: .source}` callouts for code we're walking them through to add to the rmd file.
3) for challenge solutions the solutions should be unrendered markdown syntax between \``` \```
4) for tips, use the {: .callout} callout

Examples: 
1) **R markdown examples**  
code: 
![image](https://user-images.githubusercontent.com/58574172/100487984-54d48500-30c0-11eb-9a35-0705f9c5e15d.png)
*I can't get the markdown to render correctly this this comment so this is just a screenshot

outputs to:
![image](https://user-images.githubusercontent.com/58574172/100487875-b3e5ca00-30bf-11eb-98a8-554a7eb081bd.png)

2) **Exercises (i.e. "follow me" not challenges)**
code: 
```
~~~
## MATERIALS AND METHODS  
### Survey Overview  
### Data Analysis  
~~~
{: .source}
```
outputs as: 
![image](https://user-images.githubusercontent.com/58574172/100487796-55b8e700-30bf-11eb-8925-52fad5db9c18.png)

3) **Challenges**
- Make sure to label challenges `CHALLENGE [ep#.challenge#]`
- the solution is just `SOLUTION`
code: 
```
> ## CHALLENGE 3.1
> Insert headings throughout the rest of the paper so it is split into 5 sections (Introduction, Materials and Methods, Results and Discussion, Conclusion, and References). Use the search function in R Markdown to find these lines in the document. 
>
>> ## SOLUTION
>> ```
>> ## INTRODUCTION
>> ## MATERIALS AND METHODS
>> ## RESULTS AND DISCUSSION
>> ## CONCLUSION
>> ## REFERENCES
>> ```
>> Why are we using `##`? Because `#` should only be used once in the paper (for the title) and `##` is for the next heading level.
> {: .solution}
{: .challenge}
```
outputs as:
![image](https://user-images.githubusercontent.com/58574172/100487815-6e290180-30bf-11eb-8e54-c4f97dfb39be.png)

4) 
- heading should say `Tip: [short description of tip]`
```
> ## Tip: how to make callouts
> Use `>`s on each line of callout and after callout ends the next line should contain {: .callout}
{: .callout}
```

### Generate regular vanilla Markdown from R-markdown for episodes

When creating episodes in the `_episodes_rmd` directory you'll want to process them into rgular markdown so they will be further processed by Github and published when pushed to Github.  If you have the `make` utility, which Mac or Linux has by default you can call `make lesson-m`.   But if you do not have `make` which is the case for most windows users then you can use R and Knitr from the command line. There are two ways to do this for Windows users:

**1) Use knitr from the command line/ Rstudio terminal to process an R-markdown file into a regular markdown file:**
*assumes you are in the root directory
*change the file name to match the episode you edited
```
Rscript -e 'knitr::knit("./_episodes_rmd/01-r-markdown-episode-template.Rmd", output = "./_episodes/01-r-markdown-episode-template.md")'
```

**2) Change your knit button settings**
Next to the knit button there is a gear for options. Click it and chose `output options` at the very bottom of the list. Choose the `Advanced` tab and check `keep markdown source file`. Requires that you move some files around after: Make sure to 1) move the `.md` file to the `_episodes/` folder and 2) delete the html file output. 

*method 1 will work even if all your image links etc. aren't working. Method 2 won't work unless all links are correct - errors out otherwise.

#### Code for all lessons method 1 cheatsheet:
~~~
# episode 2:
Rscript -e 'knitr::knit("./_episodes_rmd/02-basic-rstudio.Rmd", output = "./_episodes/02-basic-rstudio.md")'
# episode 3:
Rscript -e 'knitr::knit("./_episodes_rmd/03-rmarkdown-file.Rmd", output = "./_episodes/03-rmarkdown-file.md")'
# episode 4:
Rscript -e 'knitr::knit("./_episodes_rmd/04-good-project.Rmd", output = "./_episodes/04-good-project.md")'
# episode 5:
Rscript -e 'knitr::knit("./_episodes_rmd/05-setup-versioning.Rmd", output = "./_episodes/05-setup-versioning.md")'
# episode 6:
Rscript -e 'knitr::knit("./_episodes_rmd/07-code-chunks.Rmd", output = "./_episodes/07-code-chunks.md")'
~~~


### Releases and Roadmap

- 2022-09-23 release [version 1.0](../../releases/tag/v1.0-rmarkdown) - This version compatibile with R-studio "Ghost Orchid" Release 2021.09.02 or thereabouts.
- Fall-Winter 2022 plan to update this workshop for compatibility with [Quarto](https://quarto.org) 
