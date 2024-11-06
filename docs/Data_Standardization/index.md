---
layout: default
title: Data Standardisation
nav_order: 6
---

{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

# Data Standardization

The vision of automating the **discovery, retrieval, and reuse** of datasets therefore requires well-coordinated technical language to describe research aims and methods, and data objects, properties and relations (aka tables and fields) of project data.  As this information becomes standardised, so too will the data catalogue user interfaces for leveraging it.  Artificial Intelligence will likely be introduced to help pair users' plain language descriptions of sought-after data types and context to the catalogue's holdings, but either way, the discovery and reuse vision requires project data managers to provide sufficient information at various levels as shown below.  Examples are provided of associated tools and ontologies that improve standardized project and dataset information and downstream data catalogue capabilities:

## Standardisation layers

### **Dataset content summary**
 * Ontology-driven keyword systems are being increasingly adopted by data catalogues, for example, Fairsharing.org's liberal use of [EDAM](https://edamontology.org/page) and other [OBO Foundry](https://obofoundry.org/) ontologies for content description.
 * Potentially a dataset's record counts and serialization byte size information, tallies of demographic / contextual keywords, and perhaps spatiotemporal scope (a sample collection's collection time duration and location(s) for example) can be published.

### **Experimental design and protocol metadata** 
This metadata enables researchers to judge pertinence of a dataset.
 * For example, the [Experimental Design Assistant](https://nc3rs.org.uk/our-portfolio/experimental-design-assistant-eda) generates visual diagrams of multi-group and experimental variable studies in animal research for easy comparison.
 * The OBI ontology provides a sizeable list of [study design](http://purl.obolibrary.org/obo/OBI_0500000) terms which can be referenced from across life science research domains.
 * [Protocols.io](https://www.protocols.io/) is a popular system for detailing and publishing protocol information.

### **Data schema**: Dataset table and field-level information can be extracted from [data schemas](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Documentation/schemas.md) for display in agency or public FAIR data catalogues.
  * A side benefit of schemas is that they facilitiate API development and/or exposing the structural information that enables users to query datasets directly.
  * The remaining work to achieve **reuse** - inexpensive, efficient data harmonisation - is to standardise project datasets and their schemas down to the field name and picklist value level - or at least have standardized views of them so that idiosyncratic dataset table/object and field names and picklist values are recognized and harmonized with vocabulary commonly in use by other datasets.

### **Provenance**: Covers dataset hosting location, authorship, release dates, associated paper(s) and institutions, access criteria and proceedure. [PROVO](https://www.w3.org/TR/prov-overview/) is often used here.

### **Governance**: The above points focus on standardising project data for **discovery**.  Additionally, standardization of the data governance aspect, including **data access and retrieval** processes like user authentication and permissioned access via content privacy rules, is evolving with the help of ontologies such as the Data Use Ontology [DUO](https://github.com/EBISPOT/DUO), and standardized authentication systems such as [OAuth 2.0](https://oauth.net/2/).

## Timing of standardisation work

Up-front attention to data standardization encourages reuse and avoids later costly work required for peer-to-peer data mapping as new downstream users of project data are encountered.  _It has been estimated that data federation of non-standardized data requires 80% of data scientists time, whereas a 5% project budget devoted up front to standardization would greatly reduce downstream harmonization, not to mention the lost-opportunity costs of failure to discover data._  

If anticipated early in the project design cycle, standardised data components may be incorporated directly into a project’s primary data schema itself. Often however, whether because of project momentum or a commitment to existing information technology infrastructure, the specifications for standardised data products are done after a project infrastructure data schema is established, and so require a mapping process to transform existing project data into standardised format for external use. This mapping process is performed either by specialised conversion scripts that often have to be tweaked over time, or ideally by using data schemas established (e.g. for target [storage repositories](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/storage/index.md)) for the target standardised data products, and a more generic programmatic template to do the conversion from one schema to another. One can also expect iteration of specification work as data schemas evolve for surveillance or longitudinal research.

[ontologies]()

## Training resources ###
TBD


Authors: Damion Dooley
