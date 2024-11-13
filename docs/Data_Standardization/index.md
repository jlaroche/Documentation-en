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

The vision of FAIR **discovery and reuse** of datasets has a number of [motivations and challenges](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/motivation.md).  Standardization opportunities exist at both the project data format (syntax) layer, at provenance/process/workflow/file/folder levels and as well in terms of dataset semantic meaning or "aboutness" which often requires references to experimental design, protocol, and other contextual data. This allows us to determine when datasets or data points are comparable or not, and so is important dataset information for downstream data catalogues to absorb and leverage in their search interfaces.

Ultimately, a key requirement for success is a **well-coordinated technical language to describe project research aims and methods, and dataset tables and fields**.  In the future artificial intelligence will likely pair users' plain language descriptions of sought-after data types and context to data catalogue holdings, but either way, the discovery and reuse vision requires project data managers to provide sufficient information at various layers as shown below.  

## Standardisation layers

### Data schema and dataset content summary

Harmonized [Data schemas](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Documentation/schemas.md) contribute both to peer-to-peer data sharing as well as data catalogue visibility.  This involves standardising project datasets / schemas down to the field name and picklist value level - or at least map them to their semantic equivalents.  Idiosyncratic names are replaced in favour of terms referenced in standards.  We cover standardized ways of expressing tables, attributes and their values in the [Data Schema Standardization](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/schemas.md) page.

Dataset findability also benefits from:

* **Data schema derived information**, including lists of standards and structured vocabularies in use, can be referenced in agency or public FAIR data catalogues.  
* **Dataset derived information**, including record counts and serialization byte size information, frequencies of demographic / contextual keyword use, harmonized dataset table and field-level information (e.g. counts of plant_growth_medium kinds occuring ) can be published.

* **Human curated summary (metadata) information**: including **Dataset subject area keywords** which can be standardized via ontology-driven (as opposed to free-text) keyword menus; These are being increasingly adopted by data catalogues, for example, [Fairsharing.org's](https://fairsharing.org/) liberal use of EDAM ontology [topics]([https://edamontology.org/page](https://bioportal.bioontology.org/ontologies/EDAM?p=classes&conceptid=topic_0003) and other [OBO Foundry](https://obofoundry.org/) ontologies for content description.  Beyond keywords, dimensional metadata such as a sample set's spatiotemporal collection date and geographic location(s)) can be described using structured vocabularies like Wikidata's geographical knowledge base, e.g. [Canada](https://www.wikidata.org/wiki/Q16).
 
### Experimental design and protocol metadata

Going beyond subject areas, this metadata enables researchers to judge pertinence of a dataset arising from samples or observations where the data itself doesn't clearly define the experimental groups or context of collection, or sensitive methodology involved.

 * For example, the [Experimental Design Assistant](https://nc3rs.org.uk/our-portfolio/experimental-design-assistant-eda) generates visual diagrams of multi-group and experimental variable studies in animal research for speedier detailed comparison.
 * More generally, the [OBI](http://purl.obolibrary.org/obo/OBI_0500000) ontology and [NCIT Thesaurus](http://purl.obolibrary.org/obo/NCIT_C15320) provide a sizeable list of study design terms which can be referenced from across life science research domains.
 * [Protocols.io](https://www.protocols.io/) is a popular system for detailing and publishing protocol information.

### Provenance
The story of where datasets are hosted and the projects, people and agencies responsible for their creation and management.  Common language covers:
* Dataset hosting location, authorship, release dates, associated paper(s) and institutions.  The Provenance Ontology ([PROVO](https://www.w3.org/TR/prov-overview/)) is often used here, as well as a number of Dublin Core metadata [DCMI Metadata Terms](https://www.dublincore.org/specifications/dublin-core/dcmi-terms).
* Authorship: [ORCID](https://orcid.org/) identifiers are now the standard way of referencing authors

### Governance

The above points focus on standardising project data for discovery.  Additionally, standardization of the [data governance](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Sharing/index.md#administrative) aspect, including **data access criteria and retrieval** processes like user authentication and permissioned access via content privacy rules, is evolving with the help of ontologies such as the Data Use Ontology [DUO](https://github.com/EBISPOT/DUO), and standardized authentication systems such as [OAuth 2.0](https://oauth.net/2/).

### Files, folders, and workflow

A project is composed of many workflow-generated files and folders which need to be systematically organized, as covered [here](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/files.md)

## Implementation

Its important to stress that researchers shouldn't have to take on the bulk of standardization work since it does involve a number technical skills and general awareness of controlled vocabularies and standardized data formats that take time to aquire.  Ideally project data management/science/analyst staff are available to help with standardizing data schemas or exported data projects. This is where the DCC team can help!

If anticipated early in the project design cycle, data schema components can be standardized as copies of existing 3rd party standards components, as we are encouraging in the Schema Library section.  Often however, whether because of project momentum or a commitment to existing information technology infrastructure, a data schema is non-standardised, and so data products require a mapping process to transform existing project data into standardised format for external use. This mapping process is performed either by specialised conversion scripts that often have to be tweaked over time, or ideally by using a more generic programmatic template to convert between project schema components and target standardised data products (e.g. specific data formats supported by [storage repositories](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/storage/index.md)). One can also expect iteration of specification work as data schemas evolve for surveillance or longitudinal research.
  
* **Standardised data components**:
  * **Data schema attribute level**: If anticipated early in the project design cycle, data attributes can be standardized (or customized) as copies of existing 3rd party standards elements, sharing attribute specification elements described above.  The [NCBI BioSample](https://www.ncbi.nlm.nih.gov/biosample/docs/attributes/) pooled specification is one good source of attributes used to describe the environmental/farm or human/animal/plant context of biosamples for genomics research.
  * **Data schema record level**: Usually producing standardised data products is accomplished by copying or mapping selected parts of target specifications into a project's [**data schema**](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Documentation/schemas.md).  The NCBI BioSample specification is actually organized in more topical "[packages](https://www.ncbi.nlm.nih.gov/biosample/docs/packages/)" for easier comprehension and copying of parts or wholes.  Work has been done to convert the majority of these specifications into a machine readable [MIxS LinkML](https://github.com/turbomam/mixs-subset-examples-first) GitHub repository format, with a browsable [documentation version](https://turbomam.github.io/mixs-subset-examples-first/).
  
* **Data naming convention**: Regardless of whether a data schema is reusing elements from other schemas, it is important to impose data naming conventions (described above) on its home-grown components.  This is done mainly to avoid issues in applying or developing software scripts for validation, transformation, and/or database interaction.
  
* **Ontologies**: Much standardization work can be done in advance of introducing ontology id’s to a schema.  In a way ontologies provide the comparable fruits of interoperability, but a data schema is the practical tree that needs to be built on which ontology terms hang. In the [ontology](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/ontology.md) section there is a list of recommended ontologies and ways of implementing them as a layer upon a data schema and project metadata.

## Training resources ###
TBD


Authors: Damion Dooley
