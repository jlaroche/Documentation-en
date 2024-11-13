---
layout: default
title: Ontology
parent: Data Standardisation
nav_order: 2
---

# Ontology
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

To evolve towards a findable and federatable data future, projects are adopting an ontology framework layer which essentially attempts to externalise as much of the language a dataset uses as possible, enabling it to join a larger semantically interoperable community of datasets.  Other benefits accrue - database development personnel reuse 3rd party structured vocabulary rather than unwittingly maintaining mirrored semblances of them, for example.  We begin with a short discussion of what ontologies are, how they differ from simpler kinds of structured vocabulary, and why certain features of them are needed to achieve a federated data future.  We also cover tips and training resources about how to locate and reuse ontologies in study metadata and data schemas. 

The definition of "**ontology**" in Wikipedia speaks to its historical roots as an area of philosophy dedicated to the "study of being in reality", and dives into how things can be categorized and identified through time.  Our focus is on "**applied ontology**", which makes use of categorization and formal logic work in philosophy, but turns to description of **material entities** (things), their **characteristics** (attributes), **processes** or events that they are involved in, and **roles, functions or dispositions** they may have.  All this formality is in an effort to come to a shared agreement about how to categorize scientific terms systematically, once and for all - but recognizing that science itself makes room for hypotheses, revisions, and paradigm shifts, and so needs ontologies to evolve.

Most ontologies were created after the web itself, and as inter-agency collaborative open source projects, many are still evolving, taking on new terms and deprecating archaic ones, refining their own domain(s) of content, and handing terms over to other ontologies for more focuse curation, and visa versa.  The sociotechnical complexity of locating or building fit-for-purpose ontology resources can be frustrating, and we discuss metrics for success here too.

## Advantages of ontology format
Our data standardization writeup has explained the need for kinds of structured vocabulary covering agriculture and related domains with features that make them reusable, infrastructure friendly, and semantically precise.  Ontologies, combined with some curational best-practices, have these features built-in in a way that other structured vocabulary formats can't match.  Not all ontologies are created equal, and there are dead ones, and incomplete or very poorly designed ones.  Consequently, ontology collaboratives such as the OBO Foundry have created [curational principles](https://obofoundry.org/principles/fp-000-summary.html) to enable recognition of gold standard ontologies. We will also mention some other structured vocabulary formats like the common Simple Knowledge Organization System [SKOS](https://en.wikipedia.org/wiki/Simple_Knowledge_Organization_System) that though logically and/or semantically lax, may be useful since they have institutionally-backed resources, and meet the needs of library science style category indexes, like the [AGROVOC](https://www.fao.org/agrovoc/) agricultural concepts, definitions and relationships vocabulary.

A good ontology should be:

* in an [OWL format](https://en.wikipedia.org/wiki/Web_Ontology_Language) which has a few syntax variations and logical reasoning powers.
* hosted on a public versioned repository such as GitHub.
* supported by volunteer or funded curators (ideally experts from multiple collaborating organizations) who can respond to user inquiries and requests.
* available on one or more ontology lookup services.

In this context an ontology is capable of providing:

### Permanent URLs
Each ontology term is given a URL and attached to a web service which returns human and computer readable information about the term, such as label, definition, synonyms, parent and child entities. The term URL is expected to exist in perpetuity; a deprecation and replacement term reference system exists which facilitates database updates in the face of evolving ontologies. 

### Hierarchic terms and inheritance
Each term appears in a hierarchy of terms of the same type, whether it be material entities, process types, or characteristics of things.  Here we more aptly switch to referencing an ontology term as an **entity** or **class**, because ontologies enable logical reasoners to take in an ontological description of some entity, and figure out what classes it fits or belongs to in an ontology, e.g. an animal which "'has part' exactly 4 legs" can be categorized as a quadriped.  Any subclass (a child of a given class) of "quadruped" is also expected to have 4 legs due to the power of inheritance that OWL ontologies have.  If a reasoner is run on an ontology with a "quadruped" class, and a subclass of quadruped has only 3 legs, a logical error will result.  This highlites a quality control metric - logical consistency - that can be obtained within an ontology, and also when reasoning over merged ontologies that share the same set of relations.

A hierarchical organization of terms also sets up using branches of an ontology as a source of picklist choices for some attribute, equivalent to lookup tables that  computer science developers are familiar with.

### Entity or class properties
Naturally an ontology needs a language of relations (called object properties) such as "located in" or "part of" and a way to use them in expressing logical statements, called axioms, that must be true for a class to match some given candidate entity. There is also some functionality for associating specific values or ranges to class axioms (e.g. "pi 'has value' "3.1415927"^^xsd:decimal).

### Free-text definition
A class should have a free-text definition which reflects in plain language the logic of any axioms it has, or if no axioms exist, at least helps the reader to recognize what is included or excluded from its category of entity.  This style of definition is called the Aristotelian genus-differentiae form which reference a class's parent class and goes on to differentiate the kinds of entity it matches from those which its siblings would match.

### Curation standards
Terms are explained in the singular, are provided in a single language like English, and are lowercase except for proper noun parts.

### Authorship
Credit is provided for term curators and definition sources.

### Multilingual (also by way of synonymy lookup tables)

* Phenopacket output products

### Data Schemas: Database view and ontology view
A Separation of concern ...

### Keywords and picklists
...

https://github.com/cmungall/gold-ontology


### Knowledege graph modelling
Advanced! ...

### Roles
* User
* Implementer
* Curator

### Adoption Hurdles

Ontology development and reuse is relatively new to the data science world, and has its share of growing pains.  There are a variety of pitfalls to avoid:

## Training

* Force11 course: [L14 Introduction to Data Curation Using Ontologies: FAIR Datasets and Community Collaboration](https://osf.io/fj38v/) written from a public health perspective but equally applicable to biosample metadata in other fields.

### Resources
There are many places to find structured vocabularies such as ontologies and taxonomies as a source for terms.

- The organization CGIAR has published a resource of common [Ontologies for agriculture](https://bigdata.cgiar.org/ontologies-for-agriculture/).
- [AgroPortal](https://agroportal.lirmm.fr/) is another source of agriculture research vocabulary.
- The above resources relay a number of [OBO Foundry](https://obofoundry.org/) life science ontologies related to agriculture, biology, climate, and ecology research, as detailed in the [ontology](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/ontology.md) documentation section.

* 
