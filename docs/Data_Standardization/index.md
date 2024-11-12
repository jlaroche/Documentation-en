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

The vision of FAIR **discovery and reuse** of datasets has a number of [motivations and challenges](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/motivation.md).  Standardization opportunities exist at both the project data format (syntax) layer, at provenance/process/workflow/file/folder levels and as well in terms of semantic or equivalent meaning or "aboutness" which often requires references to experimental design, protocol, and other contextual data. This allows us to determine when datasets or data points are comparable or not, and so is important dataset information for downstream data catalogues to absorb and leverage in their search interfaces.

Ultimately, a key requirement for success is a **well-coordinated technical language to describe project research aims and methods, and dataset tables and fields**.  Artificial Intelligence will likely be introduced to help pair users' plain language descriptions of sought-after data types and context to the catalogue's holdings, but either way, the discovery and reuse vision requires project data managers to provide sufficient information at various layers as shown below.  First we work through a description and recommendations on the mixture of language currently present in describing data standard content at various layers and in various software applications and storage technologies, and then discuss how ontologies can be layered on to help determine semantic comparability.

* **Values**: A form field, record field, table row field, spreadsheet cell, computational object/class attribute or property or slot, or variable can hold a **value** (aka data item or datum).

* **Character sets**: Data "serialized" into a text file will be encoded as strings characters from a character set which may include accents etc. A popular [UTF-8](https://en.wikipedia.org/wiki/UTF-8) standard (used to encode most web pages) includes character encodings that cover many languages and [dingbats](https://en.wikipedia.org/wiki/Dingbat) to boot!  Sadly software often has to guess what encoding an input file has, and some versions of programs like [MS Excel](https://support.guidebook.com/hc/en-us/articles/360016372414) have their own coding, leading to confusion in translation.

* **Fundamental datatypes**: Crucial to machine readability, a value can be of a certain fundamental "literal" or syntactic **datatype**, like a string, date, time, integer or decimal number, boolean, categorical value or URL reference type.  A few common standard "data-interchange languages" exist that express these: [XML](https://www.w3.org/TR/xmlschema11-2/#built-in-datatypes), [JSON](https://json-schema.org/understanding-json-schema/reference/type) and [SQL](https://www.digitalocean.com/community/tutorials/sql-data-types). (There one can see translation issues where one standard allows a less atomic "number" datatype while another only has "decimal" or "integer" - so a conversion from a schema using one datatype standard to another schema with a different data type requires "sniffing" or parsing what kind of number the former contains.)
  * **Units**: Numeric values may be accompanied by units (e.g. "1m" for a meter, or "2d" for 2 days).  Whether a unit is bundled with a number as a single string datatype value, or whether they are separated out into separate datatype values is a matter for the schema developers to settle. By themselves, units need a string or coding representation, such as provided by [UCUM codes](https://units-of-measurement.org/) or an ontology of units (e.g. [QUDT](http://qudt.org/), [OM](http://www.ontology-of-units-of-measure.org/), [UO](https://obofoundry.org/ontology/uo)).
  * A data schema can also provide more complex string data type extensions by imposing further constraints on their syntax in order to express for example the [ISO 19115-1:2014
Geographic information — Metadata](https://www.iso.org/standard/53798.html) for latitude and longitude coordinates. The standard way of doing this is with [regular expressions](https://en.wikipedia.org/wiki/Regular_expression).

Encountering a value that has a syntactic structure beyond random characters suggests that it has some meaning about something, which leads to the topic of attributes.

* **Attributes**:   A kind of table record, spreadsheet, computational object or class, ontological entity, or user interface form may have some number of required and/or optional **attributes**.  An attribute is also known as a **field, property, variable, or slot**.  An attribute specification should include a relatively plain language definition that distinguishes it from other attributes having similar names or semantics.  (In the ontology section we discuss Aristotelean definitions that depend on attributes organized in semantic hierarchies).

  When someone references an attribute there may be some ambiguity in what they mean - do they mean a column display name, a 3rd party standardized field name, or a programmatic name for use in scripts or databases?  A separation of concern needs to be established in a data schema about an attribute's title or label for display purposes, its database or programming reference, and its standardization name.

  * **Attribute naming**: It is important to distinguish the two kinds of name an attribute can have, a computational coding one which ideally enables lookup of its semantics (definition, datatype(s), synonyms etc.) in a schema, and a default plain name which may vary among applications/user interfaces that display/use an attribute.
    * **Plain name**: A default plain language user interface **label or title** (including spreadsheet column labels) for human readability, such as "Birth Date", "Birthdate", "date of birth", "born", etc. Enabling the title or label to have language variants also paves the way for multilingual interfaces. In software it should not be used as the key for looking up attribute information.
    * **Coding name**: A computer software/script/analytic/database/serialization-level attribute "coding" name, such as "birth_date".  This name is the key to machine readability, and its standard format should align with popular programming variable naming conventions to avoid errors in parsing data files and validation, and to enable code generation (e.g. alphanumeric + underscore only; no spaces, dashes, slashes, brackets, parentheses or dots etc. allowed in a name).  Data schema frameworks like LinkML have been guided by [Python](https://peps.python.org/pep-0008/#naming-conventions) / [R and SQL compatible](https://bookdown.org/content/d1e53ac9-28ce-472f-bc2c-f499f18264a3/names.html) attribute names, and standardized table / object names, in particular:
      
       * **PascalCase**: **for table, object and picklist names, use an alphanumeric string beginning with a capital letter.** A MS Excell regular expression
       * **lower_camel_case**: **for attribute coding names, use lowercase alphanumeric words separated by underscores.**
       * For those working in MS Excell, a regular expression for converting a column A, row 1 plain attribute name to PascalCase is: 
          =regexreplace(proper(A1),"[_ (/)-]","") 
         and for lower_camel_case: 
         =Lower(regexreplace(regexreplace(A1,"[ /]","_"),"[-()]",""))
  
    * **ontology id(s)**: As detailed in identifiers section below, for every attribute there can also be one or more ontology purl identifiers which indicate that the attribute is machine comparable with any similarly marked attribute; as well the purl may carry the burden of pointing to a resource that indicates the attributes semantic definition, synonymy and logical constraints.  For example the cell Ontology [cell type](http://purl.obolibrary.org/obo/CL_0000000) can be referenced in a "cell_type" attribute.

* **Attribute value(s)**: An attribute's schema specification allows at least one value datatype but in some schemas it may have more than one, such as a birthdate integer plus "null value list" (a picklist of missing, not collected, etc. data collection statuses).  Standards such as NCBI's [missing value reporting](https://www.ddbj.nig.ac.jp/biosample/submission-e.html#missing-value-reporting) cover this.
   
* **Attribute semantics**: As suggested by its coding or plain names, an attribute like "age" has a **semantic type** different from its **datatype**, so for example while an attribute might simply be called "age" (with datatype integer and implicit year unit), it wasn't intended to be compared with any dataset's "age" attribute out there in the world, as shown by the list of [age kinds](http://purl.obolibrary.org/obo/OBI_0001167) from the OBI ontology. So, while an attribute might state this in its plain language definition, the semantics of that (setting aside AI tools) are lost on computers trying to see if two age fields are comparable.  This is why data harmonization proponents advocate to include a mapping to one or more comparable ontology term ids in an attribute specification (or alternately, in a knowledge graph view, to use an ontology term identifier directly to indicate an attribute).  Ideally a schema draws upon a shared library of attributes organized by their semantic differentiae.
  * **Measures**: Another complication is that attributes aren't always measured in the same way, even within the same schema, so in that case different attributes (with different coding and plain names) should be defined that include the precise unit measure or scale in question (such as "age_in_years" or "age_in_weeks" or "gestational_age" or "trimester_age"). This solves computational ambiguity.
  * **Categorical attributes**: As shows up often in surveys, some attributes are measured by categorical/ordinal set of permissable values (such as "young | adult | elderly" for age). These choices are coming from schema-imbedded picklists, or from one or more controlled vocabularies.  Data schemas need a mechanism to indicate what the vocabulary "picklist" choices are, or in the case of large and evolving vocabularies, where they are online, and which branches to include or exclude choices from.

* **Compound attributes**: These are object or data structure specifications - which may be sumarized as a single attribute - made out of several attributes, so for example a "location" might be a combination of latitiude and longitude in one string.  Another example is the variety of address kinds (postal box, street, legal, head office, home) which could be serialized in a single string value, instead we prefer to break them up into a general "address" object containing street or post office box, city, postal code, region etc. Particular address kinds inherit attributes of the general address kind, and add their own, such as for the postal box kind.
  
* **Permanent identifiers**: Given the need to reference vocabulary and other data resources on the web, standardization work often involves a kind of value called a **permanent identifier** reference that points to a resource like a dataset, document, or vocabulary term detail page.  For a web reference this is called a **permanent URL or "purl"**, such as [http://purl.obolibrary.org/obo/OBI_0001167](http://purl.obolibrary.org/obo/OBI_0001167).  Once a purl goes into circulation on the web, it is expected to remain there so it can always retrieve the resource, or, if what it points to becomes archaic or discontinued, a "deprecated" code response. Additionally, if a newer vocabulary or resource replaces it, a replacement identifier is indicated. This way data content can be updated to harmonize and simplify federation and querying.

* **Structured vocabulary**: We use the term "structured vocabulary" to describe a file of vocabulary terms such as a taxonomy or ontology that includes attribute details to some extent - such as plain english or other language names, coding names, purls, definitions, and attribute semantics such as hierarchies of terms.  There are many structured vocabulary catalogues as lists or searchable portals, including:

  * The international CGIAR agricultural research agency has published a resource of common [Ontologies for agriculture](https://bigdata.cgiar.org/ontologies-for-agriculture/).
  * [AgroPortal](https://agroportal.lirmm.fr/) supported by a number of leading French research agencies is another source of agriculture research vocabulary.
  * [OBO Foundry](https://obofoundry.org/) is a multi-agency collaborative effort of life science ontologies related to agriculture, biology, climate, and ecology research, all operating within an aligned curational methodology.
  * [OLS](https://www.ebi.ac.uk/ols4) The European Molecular Biology Laboratory (EMBL) European Bioinformatics Institute ontology search interface reflects the agencies commitment to developing ontologies in the life science area.
  * [Fairsharing.org](https://fairsharing.org/search?fairsharingRegistry=Standard) has a standards registry dedicated to workflow and ontology resources.

More details on applying suitable ontologies to dataset standardization is provided in the [ontology](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/ontology.md) section.

## Standardisation layers

### Data schema and dataset content summary

Harmonized [Data schemas](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Documentation/schemas.md) contribute both to peer-to-peer data sharing as well as data catalogue visibility.  This involves standardising project datasets / schemas down to the field name and picklist value level - or at least map them to their semantic equivalents.  Idiosyncratic names are replaced in favour of terms referenced in standards.

* Human curated summary (metadata) information:
  * Dataset subject area keywords can be standardized via ontology-driven (as opposed to free-text) keyword menus; These are being increasingly adopted by data catalogues, for example, [Fairsharing.org's](https://fairsharing.org/) liberal use of EDAM ontology [topics]([https://edamontology.org/page](https://bioportal.bioontology.org/ontologies/EDAM?p=classes&conceptid=topic_0003) and other [OBO Foundry](https://obofoundry.org/) ontologies for content description.
  * Spatiotemporal scope (e.g. a sample set's collection date and location(s)) can be described using structured vocabularies like Wikidata's geographical knowledge base, e.g. [Canada](https://www.wikidata.org/wiki/Q16).
* Data schema derived information, including lists of standards and structured vocabularies in use, can be referenced in agency or public FAIR data catalogues.  
* Dataset derived information, including record counts and serialization byte size information, frequencies of demographic / contextual keyword use, harmonized dataset table and field-level information (e.g. counts of plant_growth_medium kinds occuring ) can be published.

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

If anticipated early in the project design cycle, data schema components can be standardized as copies of existing 3rd party standards components, as we are encouraging in the Schema Library section.  Often however, whether because of project momentum or a commitment to existing information technology infrastructure, a data schema is non-standardised, and so data products require a mapping process to transform existing project data into standardised format for external use. This mapping process is performed either by specialised conversion scripts that often have to be tweaked over time, or ideally by using data schemas established (e.g. by [storage repositories](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/storage/index.md) that store specific formats of data) for the target standardised data products, combined with a more generic programmatic template to do the conversion from one schema to another. One can also expect iteration of specification work as data schemas evolve for surveillance or longitudinal research.
  
* **Standardised data components**:
  * **Data schema attribute level**: If anticipated early in the project design cycle, data attributes can be standardized (or customized) as copies of existing 3rd party standards elements, sharing attribute specification elements described above.
  * **Data schema record level**: Usually producing standardised data products is accomplished by copying or mapping selected parts of target specifications into a project's [**data schema**](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Documentation/schemas.md).  The [NCBI BioSample](https://www.ncbi.nlm.nih.gov/biosample/docs/attributes/) pooled specification is a good source example of single and bundled attributes used to describe the environmental/farm or human/animal/plant context of biosamples for genomics research.  This specification is broken down into more topical "[packages](https://www.ncbi.nlm.nih.gov/biosample/docs/packages/)" areas for easier comprehension and copying of parts or wholes. 
  
* **Data naming convention**: Regardless of whether a data schema is reusing elements from other schemas, it is important to impose data naming conventions (described above) on its home-grown components.  This is done mainly to avoid issues in applying or developing software scripts for validation, transformation, and/or database interaction.
  
* **Ontologies**: In the [ontology](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/ontology.md) section there is a list of recommended ontologies and ways of implementing them as a layer upon a data schema and project metadata.

## Training resources ###
TBD


Authors: Damion Dooley
