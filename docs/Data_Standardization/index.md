---
layout: default
title: Data Standardisation
nav_order: 6
---

# Data Standardization
### Motivation

While a project’s datasets may have been built and hosted to support the immediate needs of its research aims, extra attention is usually required to create standardised data products so they can be found and reused by other stakeholders (academic, government, industry, and other research agency staff) with minimal effort. Up-front attention to data standardization encourages reuse and avoids later costly work required for peer-to-peer data mapping as new downstream users of project data are encountered.  Various tools and artefacts enable discoverability and reuse:

* Dataset table and potentially field-level information can be extracted from [data schemas](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Documentation/schemas.md) for display in agency or public FAIR data catalogues like [FAIRsharing.org](https://fairsharing.org/) or Google's [dataset search](https://datasetsearch.research.google.com/) which utilises the general https://schema.org/Dataset framework for describing data. 
* Datasets can be queried to report dataset size, record quantity, and perhaps spatiotemporal scope (a sample collection's collection time duration and location(s) for example) for display in data catalogues.

### FAIR Data discovery and reuse challenges

Even if project datasets are registered in FAIR data catalogues (aka data search portals) discovery and reuse can be confounded by non-harmonized metadata and data, as well as limitations of the catalogues themselves, especially in the context of the flood of experimental and surveillance datasets being generated annually in many areas of research.

* A semantic description of a dataset is often limited to a "bag" or set of keywords - and these keywords are often user-supplied free text and/or selected from a broad rather than comprehensive menu.
* Providing a few general dataset domain keywords to the search form on a data catalogue site will yield too many results to humanly sift through (and not likely ranked to facilitate a cutoff point).  On the other hand, providing more keywords, and more specific ones, may winnow down candidate datasets too sharply, excluding good ones that simply used some different keyword synonyms (including taxonomy, e.g. "Malus pumila vs. Malus domestica to reference an apple tree).  While schema.org, a commonly used general data schema specification language, provides a few dimensions to describe the scope of database content (e.g. [temporalCoverage](https://schema.org/temporalCoverage), [countryOfOrigin](https://schema.org/countryOfOrigin), and 
[contentLocation](https://schema.org/contentLocation)), this is still just a fraction of the terms needed to differentiate what datasets are about.
* Project data schemas are usually not available for perusal in data catalogues.   
* On the search side, features for filtering datasets by dimensions of their experimental designs and protocols are often missing from a data catalogue.  It ends up being a manual task to locate datasets that have pertinent subject demographics, sample time, location, biological or social environment, or experimental protocols.

### Layers of standardisation

The vision of automating the **discovery, retrieval, and reuse** of datasets therefore requires well-coordinated technical language to describe research aims, and methods, and data objects, properties and relations (aka tables and fields) of project data.  As this information becomes standardised, so too will the data catalogue user interfaces for leveraging it.  Artificial Intelligence will likely be introduced to help pair users' natural language descriptions of sought-after data types and context to the catalogue's holdings, but either way, the discovery and reuse vision requires project data managers to provide sufficient information at various levels.

* At a metadata level:
  * The data schema enables publishing information about available objects and their properties (fields) to a data catalogue.
    * This has the side benefit of facilitiating API development and/or exposing the structural information to enable users to query the dataset directly.
  * The database's content can be described by publishing its record counts and serialization byte size information, and demographic/spatiotemporal/contextual tally of terms used in actual data.

The above points support standardising the data **discovery** process, and some attention will also be required to standardise the **access and retrieval** process through the interplay between user authentication and permission and content privacy rules.  The main challenge that remains to achieve **reuse** - inexpensive, efficient data harmonisation - is to standardise project data schemes and databases down to the field name and picklist value level - or at least data views of them.  (If an idiosyncratic dataset has its own table/object and field names, and its own picklist values which frequently don't match 1-1 with any vocabulary commonly in use, this leads to the mapping of its content to other upstream data providers, or downstream data users.  If done directly, this becomes an expensive peer-to-peer mapping exercise that repeats as each new provider or user shows up).

Providence fit-for-purpose
80% of data handling is wasted on data harmonization...

To evolve towards a federated data future, an extra "applied ontology" framework layer has to be added which essentially attempts to externalise as much of the language a database uses as possible, essentially enabling it to join a larger semantically interoperable community of datasets.  Other benefits accrue - database development personnel become acquainted with a 3rd party standardised vocabulary rather than doing the work to unwittingly maintain a mirrored semblance of one.

### Ontology

We begin with a short discussion of what applied ontologies are, how they differ from simpler kinds of standardised vocabulary, and why certain features of them are needed to achieve a federated data future.

* Unique identifiers
* Globally resolvable
* No term deletion, only deprecation and replacement
* Multilingual
* Hierarchic terms
* Object properties (relations between objects)
 
[NOTE: Check in with Laurette's contact at Amsterdam about his paradigm.]

### Timing of standardisation work

If anticipated early in the project design cycle, standardised data components may be incorporated directly into a project’s primary data schema itself. Often however, whether because of project momentum or a commitment to existing information technology infrastructure, the specifications for standardised data products are done after a project infrastructure data schema is established, and so require a mapping process to transform existing project data into standardised format for external use. This mapping process is performed either by specialised conversion scripts that often have to be tweaked over time, or ideally by using data schemas established (e.g. for target [storage repositories](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/storage/index.md)) for the target standardised data products, and a more generic programmatic template to do the conversion from one schema to another. One can also expect iteration of specification work as data schemas evolve for surveillance or longitudinal research.
