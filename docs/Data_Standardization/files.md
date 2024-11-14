---
layout: default
title: File, Folder and Workflow Standards
parent: Data Standardisation
nav_order: 5
---

# File, Folder and Workflow Standards
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## File standards

File names, formats, and character sets each have standardization aspects.

### Why standardize file names?
Standardizing file naming conventions helps researchers better organize their own work and collaborate with others. 
Benefits include: 
* Consistent structure across files, making it easier for researchers to locate and identify documents.
* Uniform file names make it easier to sort and arrange files in alphabetical or chronological order. 
* Promotes a shared understanding of how files are named and organized.
* Version numbers or dates in file names helps manage version control effectively.

### File naming recommendations
The Caltech Library offers a "[File Naming Convention Worksheet](https://doi.org/10.7907/894q-zr22)" with a series of questions and tips, culminating in a naming convention pattern with examples for the project Data Management Plan. (e.g. pattern “SA-MPL-EID_YYYYMMDD_\#\#\#_status.tif” Examples are “P1-MUS-023_20200229_051_raw.tif” and “P2-DRS-285_20191031_062_composite.tif”)

### File character sets
Data "serialized" into a text file will be encoded as strings characters from a character set which may include accents etc. A popular [UTF-8](https://en.wikipedia.org/wiki/UTF-8) standard (used to encode most web pages) includes character encodings that cover many languages and [dingbats](https://en.wikipedia.org/wiki/Dingbat) to boot!  Unfortunately that's not the only character set around, and software often has to guess what encoding an input file has, and some versions of programs like [MS Excel](https://support.guidebook.com/hc/en-us/articles/360016372414) have their own coding, leading to confusion in translation.  If odd characters are displaying in an application from an input file, try to resave the input file in an appropriate character set option before opening it in the app.

## File folder structure guidelines
As mentioned in the [Data Analysis](https://climatesmartagcollab.github.io/Documentation-en/Data_Analysis/) section, the [TIER Protocol 4.0](https://www.projecttier.org/tier-protocol/protocol-4-0/) is a recommended file structure for analytic pipelines to adopt.

## Data Management Plans
All research projects for the Genome Canada's Climate-Smart Agriculture and Food Systems Initiative have created a [Data Management Plan (DMP)](../datamanagementplan.md) using the [DMP Assistant of Portage](https://dmp-pgd.ca/). This DMP typically includes recommended file naming protocols for each research project.

## Recommendations

Briney, Kristin A. 2020. “File Naming Convention Worksheet”. June 2. [https://doi.org/10.7907/894q-zr22](https://doi.org/10.7907/894q-zr22).

- Authors: Carly Huitema, Damion Dooley
