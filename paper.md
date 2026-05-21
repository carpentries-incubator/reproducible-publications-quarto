---
title: "An introductory workshop on authoring scientific publications with Quarto"
tags:
  - code reproducibility
  - open science
  - quarto documents
  - reproducible workflows
  - scientific publishing
authors:
  - name: Renata Gonçalves Curty
    orcid: 0000-0002-4615-6030
    affiliation: 1
  - name: Torin White
    orcid: 0000-0003-4671-188X
    affiliation: 2
  - name: Ian Lessing
    orcid: 0000-0003-4165-1064
    affiliation: 1
  - name: Greg Janée
    orcid: 0000-0001-8785-0021
    affiliation: 1
  - name: Kristi Liu
    orcid: 0000-0003-0679-0202
    affiliation: 1
  - name: Julien Brun
    orcid: 0000-0002-7751-6238
    affiliation: 1
  - name: Jose Nino
    orcid: 0000-0002-1841-8355
    affiliation: 1
  - name: Seth Erickson
    orcid: 0000-0002-5570-7201
    affiliation: 1
  - name: Jon Jablonski
    orcid: 0009-0007-0104-4135
    affiliation: 1
affiliations:
  - name: UCSB Library, University of California Santa Barbara
    index: 1
  - name: Advanced Cyberinfrastructure for Education and Research, University of Illinois Chicago
    index: 2
date: 9 December 2025
bibliography: paper.bib
---

# Introduction

Scientific reporting is time-consuming and iterative, often involving multiple rounds of refinement and revision in response to collaborators, editors, and reviewers [@jiang2019]. Data-centric research amplifies this complexity: researchers repeatedly interrogate data, update analyses, regenerate figures, and refine narratives while meeting formatting requirements.  

General-purpose word processors often hinder reproducible research by lacking integration of code, data, and outputs, introducing inefficiencies for authors and reviewers and limiting reproducibility [@randall2018; @haven2025]. Addressing these challenges requires not only tools but also a cultural shift toward transparency, collaboration, and accountability throughout the research lifecycle [@brownlee2021; @rasmussen2023].  

Tools such as Overleaf, Living Papers, and Quarto [@quarto2025] support transparent, reproducible workflows. Quarto, a free and open-source system developed by Posit, integrates narrative prose, executable code, visualizations, formulas, and citations into a single reproducible document. Built on Pandoc [@pandoc2025], it supports multiple programming languages, fine-grained control over code visibility, and diverse output formats (HTML, PDF, Word) while accommodating journal templates and custom designs. Beyond manuscripts, Quarto enables high-quality presentations, websites, and books, facilitating reproducible dissemination and research reuse.  

This paper introduces a modular workshop designed to familiarize learners with Quarto and to strengthen project and data management skills, with an emphasis on reproducible research practices.  


# Statement of Need

The [workshop lesson](https://carpentries-incubator.github.io/reproducible-publications-quarto) aligns with open science principles and the pedagogical philosophy of [The Carpentries](https://carpentries.org). Existing Carpentries curricula focus on computational skills in data manipulation, analysis, and visualization, leaving a gap in instruction on publication and reproducible reporting.  

Our module provides hands-on experience in creating dynamic, reproducible documents with Quarto. Learners integrate executable code, narrative text, and citations into cohesive outputs, while also learning structured file organization, naming conventions, scalable directory structures, and strategies for managing project dependencies to ensure reproducibility over time.   

By the end of the workshop, participants are expected to integrate Quarto into their workflows and apply the core principles of reproducible research effectively in their own projects.  


# Target Audience

The workshop targets academic researchers tasked with scientific reporting, including faculty, graduate students, research assistants, and postdocs. While Quarto supports Julia, Python, and Observable JavaScript, this workshop focuses on R. Prior experience with R and RStudio is recommended but not required. Basic familiarity with the Unix Shell and Git is expected.  


# Lesson Structure

The lesson consists of 15 episodes in three modules:  

## Module 1 – Reproducibility and Project Organization

Introduces the importance of transparent workflows, core principles of reproducible research, and good-enough practices for organizing projects. This module includes two episodes and ensures a common foundation for all learners.  

## Module 2 – Quarto and RStudio

Eight episodes provide hands-on practice creating data papers in Quarto. Learners format and style documents containing code, text, images, formulas, and citations, using local and global (YAML) settings.  

## Module 3 – Collaboration

Five episodes cover collaborative workflows using Git and GitHub, dependency management, reproducible environments with the `renv` package [@renv2025], and options for publishing outputs.  

The workshop is supported by a [project example repository](https://github.com/carpentries-incubator/quarto-project-example), including R scripts, data files, figures, and a functional Quarto document. The curriculum is designed for flexibility, allowing it to be delivered as a full workshop or as shorter, focused sessions, as outlined in the instructors' notes.


# Acknowledgements

We thank Felix Jan Nitsch, Manuela Sellitto, and Tobias Kalenscher for sharing their project files; Paul Harrison and the Monash Bioinformatics Platform for feedback; and organizers of the 1st Asian Student Symposium for insights. Special thanks to Toby Hodges (The Carpentries) for support in transitioning the lesson to Workbench, and to UCSB Carpentry members, helpers, instructors, and learners for their contributions.


# References