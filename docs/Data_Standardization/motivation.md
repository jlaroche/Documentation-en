---
layout: default
title: Motivation
parent: Data Standardisation
nav_order: 1
---

# Motivation for Data Standardization
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}


While a project’s datasets may have been built and hosted to support the immediate needs of its research aims, extra attention is usually required to create standardised data products so they can be found and reused by other stakeholders (academic, government, industry, and other research agency staff) with minimal effort. Even if project datasets are registered in FAIR data catalogues (aka data search portals), discovery and reuse can be confounded by non-harmonized metadata and data, as well as limitations of the catalogues themselves, especially in the context of the flood of experimental and surveillance datasets being generated in many areas of research.

Challenges faced by researchers and other data consumers:
* **Data catalogues**: For discovery, work is required to submit project dataset metadata to data catalogues like [FAIRsharing.org](https://fairsharing.org/) or Google's [dataset search](https://datasetsearch.research.google.com/), but the target catalogues themselves often don't share the same general data description framework (such as Schema.org [Dataset](https://schema.org/Dataset)), or the same semantic content terms.
* **Bag of keywords consistency**: In data catalogues, a semantic description of a dataset is often limited to a set of keywords - and these keywords are often user-supplied synonomy-rich free text and/or selected from a broad rather than comprehensive menu. Even where controlled vocabulary is used, changes in preferred labelling confound retrieval of past and present results (e.g. in taxonomy, "Malus pumila" vs. "Malus domestica" to reference apple tree).
* **Search result precision and recall**: Searching for a few general dataset domain keywords in a data catalogue will increasingly yield too many results to humanly sift through (false positives, and not suitably ranked to facilitate a cutoff point).  Conversley, providing more keywords, and more specific ones, may winnow down candidate datasets too sharply, excluding good ones that simply used some different keyword synonyms (false negatives).  Use of keywords within or across data catalogues is often inconsistent and is a fraction of the terms needed to differentiate what datasets are about.
* **Dimensional filters**: Filters specific to experimental design and protocol, subject demographics, and biological or social context are often missing, leading to further investigation to see if specific data types are being collected, with comparable methods, and in a comparable context. Some efforts to provide standard fields that pertain to database scope exist (e.g. fields for [temporalCoverage](https://schema.org/temporalCoverage), [countryOfOrigin](https://schema.org/countryOfOrigin), and 
[contentLocation](https://schema.org/contentLocation)).
* **Data normalization**: Once a researcher has located fit-for-purpose databases for federation towards answering research questions, much of their analytic time is consumed in field-level preparatory harmonization of the data.  It is estimated that 80% of Phd time is spent cleaning up and preparing data for analysis, and so FAIR data proponents advocate for an initial 5% investment of project budget towards data standardization to lessen this downstream burden as well as the lost-opportunity costs of failure to discover data. [[Invest 5% of research funds in ensuring data are reusable](https://www.nature.com/articles/d41586-020-00505-7)]

Up-front attention to data standardization encourages reuse and avoids later costly work required for peer-to-peer dataset mapping as new downstream users of project data are encountered. 

Authors: Damion Dooley
