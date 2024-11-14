---
layout: default
title: Ontology
parent: Data Standardisation
nav_order: 3
---

# Ontology
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

To evolve towards a findable and federatable data future, projects are adopting an ontology framework layer which essentially attempts to externalise as much of the language a dataset uses as possible, enabling it to join a larger semantically interoperable community of datasets.  Other benefits accrue - database development personnel reuse 3rd party structured vocabulary rather than unwittingly maintaining semblances of them, for example.  We begin with a short discussion of what ontologies are, how they differ from simpler kinds of structured vocabulary, and why certain features of them are needed to achieve a federated data future.  We also cover tips and training resources about how to locate and reuse ontologies in study metadata and data schemas.   

The definition of "**ontology**" in Wikipedia speaks to its historical roots as an area of philosophy dedicated to the "study of being in reality", and dives into how things can be categorized and identified through time.  Our focus is on "**applied ontology**", which makes use of categorization and formal logic work in philosophy, but turns to description of **material entities** (things), their **characteristics** (attributes), **processes** or events that they are involved in, and **roles, functions or dispositions** they may have.  All this formality is in an effort to come to a shared agreement about how to categorize scientific terms systematically, once and for all - but recognizing that science itself makes room for hypotheses, revisions, and paradigm shifts, and so needs ontologies to evolve.

Most ontologies were created after the web itself, and as inter-agency collaborative open source projects, many are still evolving, taking on new terms and deprecating archaic ones, refining their own domain(s) of content, and handing terms over to other ontologies for more focuse curation, and visa versa.  The sociotechnical complexity of locating or building fit-for-purpose ontology resources can be frustrating, and we discuss strategies for success in choosing and using them.

## Ontology user roles
People use ontologies in different ways, and thankfully most people don't need to know the complexity of building or maintaining one.

* User: 
* Implementer
* Curator

## Advantages of ontology format
Our data standardization writeup has explained the need for kinds of structured vocabulary covering agriculture and related domains with features that make them reusable, infrastructure friendly, and semantically precise.  Ontologies, combined with some curational best-practices, have these features built-in in a way that other structured vocabulary formats can't match.  Not all ontologies are created equal, and there are dead ones, and incomplete or very poorly designed ones.  Consequently, ontology collaboratives such as the OBO Foundry have created [curational principles](https://obofoundry.org/principles/fp-000-summary.html) to enable recognition of gold standard ontologies. 

We will also mention some other structured vocabulary formats like the common Simple Knowledge Organization System [SKOS](https://en.wikipedia.org/wiki/Simple_Knowledge_Organization_System) that though logically and/or semantically lax, may be useful since they have institutionally-backed resources, and meet the needs of library science style category indexes, like the [AGROVOC](https://www.fao.org/agrovoc/) agricultural concepts, definitions and relationships vocabulary.

A brief note about the ontology terminology detailed below: One may open an OWL ontology in a popular ontology editor like Stanford's [Protege](https://protege.stanford.edu/) and see hierarchies and lists of terms in different places; mousing over a term will yeild a unique purl identifier for it.  Ontologies express a few kinds of term: "**classes**"" which are categories of things, and "**instances**"" which are things that (by explicit statement, or by reasoned inference) belong to one or more class categories.  Two kinds of relation are offered, namely "**object properties**" like "part of" that connect between classes or instances, and "**data properties**" like "has value" that connect between instances (and sometimes classes) and particular values.

A good ontology should be:

* in an [OWL format](https://en.wikipedia.org/wiki/Web_Ontology_Language) which has a few [syntax variations](https://oboacademy.github.io/obook/explanation/owl-format-variants/) and logical reasoning powers.
* hosted on a public versioned repository such as GitHub.
* have a build system that assembles the various parts of an ontology in addition to applying quality control checks to ensure edits haven't created contradictions or other unintended consequences.  (The [Ontology Development Kit](https://github.com/INCATools/ontology-development-kit) is one tool used here.)
* supported by volunteer or funded curators (ideally experts from multiple collaborating organizations) who can respond to user inquiries and requests.
* available on one or more ontology lookup services.
* connections between terms and their synonyms, to solve the problem of people not being able to [locate](https://oboacademy.github.io/obook/explanation/intro-to-ontologies/#we-cant-find-what-were-looking-for) a good term to use just because they're using a synonym to search with.

To support their own projects, research or other agencies can also have their own private ontologies and/or mirrored versions of publicly available ontologies; this provides version control and reliability in the face of internet disruptions.

In this context an ontology is capable of providing:

### Permanent URLs
Each ontology term is given a URL and attached to a web service which returns human and computer readable information about the term, such as label, definition, synonyms, parent and child entities. The term's purl is expected to exist in perpetuity; a deprecation and replacement term reference system exists which facilitates database updates in the face of evolving ontologies. 

### Hierarchic terms and inheritance
Each term appears in a hierarchy of terms of the same type, whether it be material entities, process types, or characteristics of things.  Here we more aptly switch to referencing an ontology term as an **entity** or **class** because ontologies enable logical reasoners to take in an ontological description of some entity, and figure out what classes (categories) it fits or belongs to in an ontology, e.g. an animal which "'has part' exactly 4 legs" can be categorized as a member of a "quadriped" class.  Any subclass (a child of a given class) of "quadruped" is also expected to have 4 legs due to the power of inheritance that OWL ontologies have.  If a reasoner is run on an ontology with a quadruped class, and it or its descendent has an instance which has only 3 legs, a logical error will result.  This highlites a quality control metric - logical consistency - that can be obtained within an ontology, and also when reasoning "over" merged ontologies that share the same set of relations, and over ontologies + data described by them.

Note that a term can have more than one parent in an ontology, and if that occurs, it is called a [polyhierarchic](https://oboacademy.github.io/obook/explanation/intro-to-ontologies/#polyhierarchy) ontology. Simple one-parent ontology design is encouraged to identify the "primary" or essential parent for each class, but reasoning can yeild a polyhierarchic ontology due to the other classes a subordinate class may have.

A hierarchical organization of terms also enables using branches of an ontology as a source of picklist choices for some attribute, similar to term lookup tables that computer science developers are familiar with.

### Relations between entity kinds
Naturally an ontology needs a language of relations between classes (called "**object properties**") such as "located in" or "part of" and a way to use them in expressing logical statements, called axioms, that must be true for an entity to match to some given class. There is also some functionality (using "**data properties**") for associating specific values or ranges to class axioms (e.g. "pi 'has value' "3.1415927"^^xsd:decimal).

### Curation standards
There are a number of ontology curation communities, often based around a top-level ontology such as [BFO](https://basic-formal-ontology.org/) or [UFO](https://philarchive.org/rec/PORUUF), each with their own practices.  In the OBO Foundry community, terms are explained in the singular, are provided in a primary language like English, and are lowercase except for proper noun parts.  (The singular requirement allows curators (or computers) to fashion plural terms and their characteristics with reference to singular ones, though english still has its odd cases to consider - e.g. a "pair of pants"!)

### Textual definition
A class should have a textual definition which reflects in plain language the logic of any important axioms it has, or if no such axioms exist, at least helps the reader to recognize what is included or excluded from its category of entity.  This style of definition is called the Aristotelian genus-differentiae form which reference a class's parent class and goes on to differentiate the kinds of entity it matches from those which its siblings would match.  OBO Foundry has more advice about [definitions](https://obofoundry.org/principles/fp-006-textual-definitions.html).

### Synonyms and multilingual labels
Just as an ontology term has a label and textual definition, it may also have synonyms and language variants of those, improving its findability in free text search engines, and enabling it to be displayed in multiple languages. 

### Imported content from other ontologies
While a "**reference ontology**" may provide a comprehensive hierarchy of terms for some narrow domain, often a more **application oriented ontology** will have terms imported from other ontologies, for example a food ontology will have anatomy and taxonomy terms included to describe parts of plants and animals. This is the so-called [MIREOT](https://www.nature.com/articles/npre.2009.3576.1) principle.

It is very important when importing terms from other ontologies to keep them as a separate file from the ontology that is importing them, to facilitate refreshing the imports which are likely to change as months go by. Its also important to import only the third party terms that are needed, rather than a whole ontology, otherwise curators can become confused over time about what terms are important for maintenance and which aren't. There are a few systems that enable fetching selected portions of other ontologies, such as [OntoFox](https://ontofox.hegroup.org/) and the [robot](https://github.com/ontodev/robot) command.

### Authorship
Contributor credits are provided for term curators and definition sources, ideally by [ORCID](https://orcid.org/) identifier and purl, respectively.

## Data schemas and ontologies
Much standardization work can be done on a data schema before introducing ontology ids into it.  The schema is the practical tree on which ontology purls hang, and those purls then provide the comparable fruits of interoperability.  The separation of concern between what a data schema primarily needs to do - arranging attributes in tables or objects, and provide plain text, coding names and datatypes for attributes - and its role in FAIR data interoperability, mapping ontology or structured vocabulary identifiers to those attributes, enables the often slower ontology work to be carried on separately.

Data schemas often draw upon four ontological kinds of terms: 
material entity references, processes, characteristics, and information references (such as a reference to a measurement, or a protocol document).  Consider an example about methane:

* "[**methane**](http://purl.obolibrary.org/obo/CHEBI_16183)" is a material (chemical) in the CHEBI ontology (defn. "A one-carbon compound in which the carbon is attached by single bonds to four hydrogen atoms. It is a colourless, odourless, non-toxic but flammable gas".)
* "**concentration of methane in air**" is a characteristic.
* "[**methane measurement**](http://purl.obolibrary.org/obo/NCIT_C186080)" is a process in the NCIThesaurus ontology (defn. "The determination of the amount of methane present in a sample.).
* "**methane assay concentration datum**" is a data item output of a methane measurement process (aka assay) that provides a measure of it in parts per million.

Or, for carbon dioxide:

* "**[carbon dioxide](http://purl.obolibrary.org/obo/CHEBI_16526)**" is a chemical in the CHEBI ontology (defn. "A one-carbon compound with formula CO2 in which the carbon is attached to each oxygen atom by a double bond. A colourless, odourless gas under normal conditions, [...].")
* "[**concentration of carbon dioxide in air**](http://purl.obolibrary.org/obo/ENVO_04000004)" with defn. "The concentration of carbon dioxide when measured in air."
* "[**carbon dioxide assay**](http://purl.obolibrary.org/obo/OBI_2100001)" is a process with defn. "An analyte assay that measures the abundance of carbon dioxide".  Note however none of its children are about sampling air.
* "**carbon dioxide concentration datum**" is a data item output of a carbon dioxide assay. that provides a measure of it in parts per million.

Unfortunately one might not find the above terms in ontologies you expect would have them; for example, while **[concentration of methane in liquid water](http://purl.obolibrary.org/obo/ENVO_3100020)** exists in ENVO, there is no term for methane concentration in air - this would have to be a New Term Request (NTR) for that ontology. 

**The DCC Hub team will assist in ensuring NTRs get submitted and looked after in the appropriate ontologies.**

## Knowledege graph modelling
Research and other agencies often rely upon tabular data formats - spreadsheets or SQL databases - and are only considering knowledge graphs in an experimental way.  Meanwhile ontologists often attempt to add relations and attempt recommended models (graph components, including [nanopublications](https://pmc.ncbi.nlm.nih.gov/articles/PMC7959622) that could contribute to larger potentially federated graph databases. Some data schema systems like LinkML provide a cross-walk between these two worlds, but in this project we focus on use of ontologies for project data in tabular format.

## Training

* Force 11 course: [L14 Introduction to Data Curation Using Ontologies: FAIR Datasets and Community Collaboration](https://osf.io/fj38v/) written from a public health perspective but equally applicable to biosample metadata in other fields.

* For more technical users, there is an extensive [OBO Semantic Engineering Training](https://oboacademy.github.io/obook/) website that contains an [ontology introduction](https://oboacademy.github.io/obook/explanation/intro-to-ontologies/), tutorials, how-to guides (for Protege, ODK GitHub etc), reference guides [incl. logic](https://oboacademy.github.io/obook/explanation/subClassOf-vs-equivalentTo/), and other content that has application beyond just OBO Foundry compatible ontologies.

### Resources
There are many places to find structured vocabularies such as ontologies and taxonomies as a source for terms.

* The organization CGIAR has published a resource of common [Ontologies for agriculture](https://bigdata.cgiar.org/ontologies-for-agriculture/).
* [AgroPortal](https://agroportal.lirmm.fr/) is another source of agriculture research vocabulary.
* The above resources relay a number of [OBO Foundry](https://obofoundry.org/) life science ontologies related to agriculture, biology, climate, and ecology research, as detailed in the [ontology](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/ontology.md) documentation section.

