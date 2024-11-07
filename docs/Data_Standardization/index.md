---
layout: default
title: Data Standardisation
nav_order: 6
---

# Data Standardization
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

The vision of FAIR **discovery and reuse** of datasets has a number of [motivations and challenges](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/motivation.md). A key requirement for success is a well-coordinated technical language to describe research aims and methods, and dataset tables and fields (or objects, properties and relations) of project data.  As this metadata becomes standardised, data catalogues can leverage it in their search interfaces.  Artificial Intelligence will likely be introduced to help pair users' plain language descriptions of sought-after data types and context to the catalogue's holdings, but either way, the discovery and reuse vision requires project data managers to provide sufficient information at various layers as shown below.  Examples are provided of associated tools and ontologies that improve standardized project and dataset information and downstream data catalogue capabilities.

## Standardisation layers

### **Dataset content summary**

 * Ontology-driven keyword systems are being increasingly adopted by data catalogues, for example, Fairsharing.org's liberal use of [EDAM](https://edamontology.org/page) and other [OBO Foundry](https://obofoundry.org/) ontologies for content description.
 * Potentially a dataset's record counts and serialization byte size information, tallies of demographic / contextual keywords, and perhaps spatiotemporal scope (a sample set's collection date and location(s) for example) can be published.

### **Experimental design and protocol metadata**

This metadata enables researchers to judge pertinence of a dataset arising from samples or observations where the data itself doesn't clearly define the experimental groups or context of collection, or sensitive methodology involved.

 * For example, the [Experimental Design Assistant](https://nc3rs.org.uk/our-portfolio/experimental-design-assistant-eda) generates visual diagrams of multi-group and experimental variable studies in animal research for easy comparison.
 * The OBI ontology provides a sizeable list of [study design](http://purl.obolibrary.org/obo/OBI_0500000) terms which can be referenced from across life science research domains.
 * [Protocols.io](https://www.protocols.io/) is a popular system for detailing and publishing protocol information.

### **Data schema**

Dataset table and field-level information can be extracted from [data schemas](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Documentation/schemas.md) for display in agency or public FAIR data catalogues.

 * **API**: A side benefit of schemas is that they facilitiate application interface (API) development and/or expose the structural information that enables users to query datasets directly.
 * **Ontology**: The remaining work to achieve discovery and reuse - inexpensive, efficient data harmonisation - is to standardise project datasets and their schemas down to the field name and picklist value level - or at least have standardized views of them so that idiosyncratic dataset table/object and field names and picklist values are recognized and harmonized with vocabulary commonly in use by other datasets.

### **Provenance**
Covers dataset hosting location, authorship, release dates, associated paper(s) and institutions, access criteria and proceedure.

 * [PROVO](https://www.w3.org/TR/prov-overview/) is often used here.

### **Governance**

The above points focus on standardising project data for **discovery**.  Additionally, standardization of the [data governance](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Sharing/index.md#administrative) aspect, including **data access and retrieval** processes like user authentication and permissioned access via content privacy rules, is evolving with the help of ontologies such as the Data Use Ontology [DUO](https://github.com/EBISPOT/DUO), and standardized authentication systems such as [OAuth 2.0](https://oauth.net/2/).

## Implementation

Its important to stress that researchers shouldn't have to take on the bulk of standardization work since it does involve a number technical skills and general awareness of controlled vocabularies and standardized data formats that take time to aquire.  Ideally agency data management/science/analyst staff are available to help with standardizing data schemas or exported data projects. 

Project data schema(s) is/are a prerequisite for creating standardised data products. 
* **standardized data components**: If anticipated early in the project design cycle, standardised data components may be incorporated directly into a project’s primary data schema itself.
  
* **data schema mapping**: Often however, whether because of project momentum or a commitment to existing information technology infrastructure, a data schema is non-standardised, and so data products require a mapping process to transform existing project data into standardised format for external use. This mapping process is performed either by specialised conversion scripts that often have to be tweaked over time, or ideally by using data schemas established (e.g. by [storage repositories](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/storage/index.md)) for the target standardised data products, combined with a more generic programmatic template to do the conversion from one schema to another. One can also expect iteration of specification work as data schemas evolve for surveillance or longitudinal research.
  
* **Data naming convention**: Regardless of whether a data schema is reusing elements from other schemas, it is very beneficial to impose data naming conventions on its home-grown components.  This is done mainly to avoid issues in applying or developing software scripts for validation, transformation, and/or database interaction.
  * **Coding name**: Have a "coding name" for a field or variable name that is safe for use in most programming languages and analytic tools.  This avoids problems where some programs or databases can't handle spaces, dashes, slashes or dots etc. in a name.  Data schema frameworks like LinkML have been guided by [Python](https://peps.python.org/pep-0008/#naming-conventions) / [R and SQL compatible](https://bookdown.org/content/d1e53ac9-28ce-472f-bc2c-f499f18264a3/names.html) field names, and standardized table / object names.
     * **PascalCase** for table, object and picklist names.
     * **lower_camel_case** for record field names (object properties).
  * **Plain names**: Ensure that a separation of concern is established in the schema between the title or label that a field or variable might have in some context, and its coding name. Enabling the title or label to have language variants also paves the way for other multilingual interfaces.
  
* **Ontologies**: In the [ontology](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/ontology.md) section there is a list of recommended ontologies and ways of implementing them as a layer upon a data schema.
  * For every coding name there can be a comparable ontology identifier that points to online information about the semantics that facilitates automated machine comparison of the data item.

## Training resources ###
TBD


Authors: Damion Dooley
