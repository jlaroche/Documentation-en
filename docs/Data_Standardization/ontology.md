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

* **User**: Users may not even know that they are using ontology-driven terminology, since in user interfaces, the ids of ontology terms are usually hidden away. For researcher users, they probably benefit from knowing some favoured ontologies pertinent to their discipline, for use as reference material, and to understand how much of their discipline terminology is covered semantically.  Expert users can contribute to the feedback loop on new term requests or revisions.

* **Implementer**: A programmer or developer who has been tasked with reusing existing ontologies in some application, including databases.  This person will typically need to know how to judge the quality of an ontology, contribute to an agency's recommendations for ontology use, and be able to use scripts to fetch and refresh ontology terms or branches from remote repositories for use in applications.  They will need to know at least about the different kinds of ontology term (class, instance, material entity, process, relation etc.)

* **Curator**: An ontology curator needs to know chunks of their ontology classes and relations, and as well the curation process for handling new term requests, and the build system for developing new releases. Since ontologies are often defacto evolving standards, curators should aspire to that level of quality control.

## Advantages of ontology format
Our data standardization writeup has explained the need for kinds of structured vocabulary covering agriculture and related domains with features that make them reusable, infrastructure friendly, and semantically precise.  Ontologies, combined with some curational best-practices, have these features built-in in a way that other structured vocabulary formats can't match.  Not all ontologies are created equal, and there are dead ones, and incomplete or very poorly designed ones.  Consequently, ontology collaboratives such as the OBO Foundry have created [curational principles](https://obofoundry.org/principles/fp-000-summary.html) to enable recognition and development of gold standard ontologies. 

There are other popular structured vocabulary formats like the common Simple Knowledge Organization System [SKOS](https://en.wikipedia.org/wiki/Simple_Knowledge_Organization_System) that though logically and/or semantically lax in comparison to ontology, may be useful since they have institutionally-backed resources, and meet the needs of library science style catalogue navigation of categories, like the [AGROVOC](https://www.fao.org/agrovoc/) vocabulary of agricultural concepts.

A brief preview about the ontology terminology detailed below: One may open an OWL ontology in a popular ontology editor like Stanford's [Protege](https://protege.stanford.edu/) and see hierarchies and lists of terms in different places; mousing over a term will yield a unique purl identifier for it.  Ontologies express a few kinds of term: "**classes**"" which are categories of things, and "**instances**"" which are things that (by explicit statement, or by reasoned inference) belong to one or more class categories.  Two kinds of relation are offered, namely "**object properties**" like "part of" that connect between classes or instances, and "**data properties**" like "has value" that connect between instances (and sometimes classes) and particular values.

A good ontology should be:

* in an [OWL format](https://en.wikipedia.org/wiki/Web_Ontology_Language) which has a few [syntax variations](https://oboacademy.github.io/obook/explanation/owl-format-variants/) and logical reasoning powers.
* hosted on a public versioned repository such as GitHub.
* have a build system that assembles the various parts of an ontology in addition to applying quality control checks to ensure edits haven't created contradictions or other unintended consequences.  (The [Ontology Development Kit](https://github.com/INCATools/ontology-development-kit) is one such tool.)
* supported by volunteer or funded curators (ideally experts from multiple collaborating organizations) who can respond to user inquiries and requests.
* available on one or more ontology lookup services.
* connections between terms and their synonyms, to solve the problem of people not being able to [locate](https://oboacademy.github.io/obook/explanation/intro-to-ontologies/#we-cant-find-what-were-looking-for) a good term to use just because they're using a synonym to search with.
* using a shared set of relationships and term categories with other ontologies to facilitate interoperability and data federation.  This is currently not so easy to attain insofar as there are many stand-alone ontologies, and it usually takes conformance with some [upper level ontology](https://en.wikipedia.org/wiki/Upper_ontology) to see such congruence, and there are a handful of those to choose from too.

To support their own projects, research or other agencies can also have their own private ontologies and/or mirrored versions of publicly available ontologies; this provides version control and reliability in the face of internet disruptions.

In this context an ontology is capable of providing:

### Permanent URLs
Each ontology term is given a URL and attached to a web service which returns human and computer readable information about the term, such as label, definition, synonyms, parent and child entities. The term's purl is expected to exist in perpetuity; a deprecation and replacement term reference system exists which facilitates database updates in the face of evolving ontologies. 

### Hierarchic terms and inheritance
Each term appears in a hierarchy of terms of the same type, whether it be material entities, process types, or characteristics of things.  Here we more aptly switch to referencing an ontology term as an **entity** or **class** because ontologies enable logical reasoners to take in an ontological description of some entity, and figure out what classes (categories) it fits or belongs to in an ontology, e.g. an animal which "'has part' exactly 4 legs" can be categorized as a member of a "quadriped" class.  Any subclass (a child of a given class) of "quadruped" is also expected to have 4 legs due to the power of inheritance that OWL ontologies have.  If a reasoner is run on an ontology with a quadruped class, and it or its descendent has an instance which has only 3 legs, a logical error will result.  This highlites a quality control metric - logical consistency - that can be obtained within an ontology, and also when reasoning "over" merged ontologies that share the same set of relations, and over ontologies + data described by them.

Note that a term can have more than one parent in an ontology, and if that occurs, it is called a [polyhierarchic](https://oboacademy.github.io/obook/explanation/intro-to-ontologies/#polyhierarchy) ontology. Simple one-parent ontology design is encouraged to identify the "primary" or essential parent for each class, but reasoning can yield a polyhierarchic ontology due to the other classes a subordinate class may have.

A hierarchical organization of terms also enables using branches of an ontology as a source of picklist choices for some attribute, similar to term lookup tables that computer science developers are familiar with.

### Relations between entity kinds
An ontology needs a language of relations between classes (called "**object properties**") such as "located in" or "part of" and a way to use them in expressing logical statements, called axioms, that must be true for an entity to match to some given class. There is also some functionality (using "**data properties**") for associating specific values or ranges to class axioms (e.g. "pi 'has value' "3.1415927"^^xsd:decimal).

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

Or, for carbon dioxide:

* "**[carbon dioxide](http://purl.obolibrary.org/obo/CHEBI_16526)**" is a chemical in the CHEBI ontology (defn. "A one-carbon compound with formula CO2 in which the carbon is attached to each oxygen atom by a double bond. A colourless, odourless gas under normal conditions, [...].")
* "[**concentration of carbon dioxide in air**](http://purl.obolibrary.org/obo/ENVO_04000004)" is a quality (aka. characteristic) with defn. "The concentration of carbon dioxide when measured in air."
* "[**carbon dioxide assay**](http://purl.obolibrary.org/obo/OBI_2100001)" is a process with defn. "An analyte assay that measures the abundance of carbon dioxide".  Note however none of its children are about sampling air.

Unfortunately one might not find the above terms in the ontologies you expect would have them; for example, while **[concentration of methane in liquid water](http://purl.obolibrary.org/obo/ENVO_3100020)** exists in ENVO, there is no term for methane concentration in air - this would have to be a New Term Request (NTR) for that ontology.

A cautionary note about choosing between a "[characteristic](http://purl.obolibrary.org/obo/BFO_0000020)" term or an "information" (aka "[information content entity](http://purl.obolibrary.org/obo/IAO_0000030)", ICE, or its subclass "data item") term to map to a data schema attribute. If an appropriate characteristic term is available, that is probably the best choice. For example, given a choice for a "temperature" attribute, choose a "[temperature](http://purl.obolibrary.org/obo/PATO_0000146)" PATO characteristic rather than an OBI "[temperature measurement datum](http://purl.obolibrary.org/obo/OBI_0003079)". (Every data item about a measure of a characteristic should properly presume that the characteristic term itself is established.  In theory one could generate a corresponding data item term for every measurable characteristic held in an ontology, but this shadow hierarchy of data item terms is hard to manually manage, so various ontologies within OBO Foundry are shying away from that approach.)

**The DCC Hub team will assist in ensuring NTRs get submitted and looked after in the appropriate ontologies.**

## Knowledege graph modelling
Research and other agencies often rely upon tabular data formats - spreadsheets or SQL databases - and are only considering knowledge graphs in an experimental way.  Meanwhile ontologists often add relations and attempt data structure models (i.e. graph components, including [nanopublications](https://pmc.ncbi.nlm.nih.gov/articles/PMC7959622) that could contribute to larger potentially federated graph databases. However, as noted in a [review](https://www.sciencedirect.com/science/article/abs/pii/S0950705121006092?via%3Dihub) of various ontologies, relations that appear in ontologies, knowledge graphs and lexical resources, though perhaps semantically close, are often named differently, which "make integration of these sources, and the understanding of their coverage and gaps, very challenging." Some data schema systems like LinkML provide ways to translate between tabular and knowledge graph worlds, but in this project we focus on use of ontologies for project data in tabular format.

## Training

* Force 11 course: [L14 Introduction to Data Curation Using Ontologies: FAIR Datasets and Community Collaboration](https://osf.io/fj38v/) written from a public health perspective but equally applicable to biosample metadata in other fields.

* For more technical users, there is an extensive [OBO Semantic Engineering Training](https://oboacademy.github.io/obook/) website that contains an [ontology introduction](https://oboacademy.github.io/obook/explanation/intro-to-ontologies/), tutorials, how-to guides (for Protege, ODK GitHub etc), reference guides [incl. logic](https://oboacademy.github.io/obook/explanation/subClassOf-vs-equivalentTo/), and other content that has application beyond just OBO Foundry compatible ontologies.

## Resources
There are many places to find structured vocabularies such as ontologies and taxonomies as a source for terms.

* The organization CGIAR has published a resource of common [Ontologies for agriculture](https://bigdata.cgiar.org/ontologies-for-agriculture/).
* [AgroPortal](https://agroportal.lirmm.fr/) is another source of agriculture research vocabulary.
* The above resources relay a number of [OBO Foundry](https://obofoundry.org/) life science ontologies related to agriculture, biology, climate, and ecology research, as detailed in the [ontology](https://github.com/ClimateSmartAgCollab/Documentation-en/blob/main/docs/Data_Standardization/ontology.md) documentation section.

### Useful ontologies for agricultural research
We welcome additions to this list!

Name | Prefix | Description 
--|--|--
[Agronomy Ontology](https://obofoundry.org/ontology/agro.html) | AGRO | "Ontology of agronomic practices, agronomic techniques, and agronomic variables used in agronomic experiments."
[Cell Ontology](https://obofoundry.org/ontology/cl.html) | CL | "The Cell Ontology is a structured controlled vocabulary for cell types in animals."
[Chemical Entities of Biological Interest](https://obofoundry.org/ontology/chebi.html) | CHEBI | "A structured classification of molecular entities of biological interest focusing on 'small' chemical compounds."
[Environment Ontology](https://obofoundry.org/ontology/envo.html) | ENVO | "An ontology of environmental systems, components, and processes."
[Food Ontology](https://foodon.org) | FOODON | "A broadly scoped ontology representing entities which bear a food role. It encompasses materials in natural ecosystems and agriculture that are consumed by humans and domesticated animals."
[Gene Ontology](https://obofoundry.org/ontology/go.html) | GO | Provides "a uniform way to describe the functions of gene products from organisms across all kingdoms of life and thereby enable analysis of genomic data"
[NCBI organismal classification](https://obofoundry.org/ontology/ncbitaxon.html) | NCBITaxon | "An ontology representation of the NCBI organismal taxonomy"
[Mondo Disease Ontology](https://obofoundry.org/ontology/mondo.html) | MONDO | "A global community effort to harmonize multiple disease resources to yield a coherent merged ontology." It covers both human specific disease, non-human animal disease, and infectious disease, including zoonotic disease.
[Phenotype And Trait Ontology](https://obofoundry.org/ontology/pato.html) | PATO | An ontology of phenotypic qualities (properties, attributes or characteristics).
[Plant Ontology](https://archive.plantontology.org/) | PO | That "describes plant anatomy and morphology and stages of development for all plants."
[Plant Stress Ontology](https://obofoundry.org/ontology/pso.html) | PSO | "The Plant Stress Ontology describes biotic and abiotic stresses that a plant may encounter."
[UBERON](https://obofoundry.org/ontology/uberon.html) | UBERON | "An integrated cross-species anatomy ontology covering animals and bridging multiple species-specific ontologies."
[Vertebrate Breed Ontology](https://monarch-initiative.github.io/vertebrate-breed-ontology/) | VBO | "\[Is] restricted to non-human vertebrate animal species. It covers breeds and breed populations for livestock, companion animals, and laboratory animals."
