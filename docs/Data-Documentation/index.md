---
layout: default
title: Data Documentation
nav_order: 3
has_children: true
---

# Documenting Data 
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

All datasets have a schema, either implicit or explicit. The goal of the Semantic Engine is to take your knowledge of the data and document that explicitly using a schema. 

## Data Schemas

A schema describes the structure of the data. A good schema will tell you what the column labels are and what they mean. It will tell you the units and it will tell you what type of data is in each column.

To help you understand and use the data you need a well documented data schema. 

![A dataset and its schema](../assets/images/attributes_labels_english.PNG)

Better data schemas aid researchers in sharing data with the research community. Better documentation enables researchers to effectively communicate the context of the data to other users, ensuring that the information is used accurately. This is especially valuable in cross-disciplinary research where other users are less familiar with the conventions of a particular discipline.

Formalized, machine-readable schemas are very useful and can be expressed in a number of languages including Overlays Capture Architecture (OCA), JSON Schema, XML Schema Definition, JSON-LD, and Link-ML. 

With a machine-readable schema you can use it for many other tasks including data verification, data entry and data harmonization. For example, the [Semantic Engine](https://www.semanticengine.org) helps researchers write their own data schemas using the OCA schema language. The [Data Harmonizer](https://github.com/cidgoh/DataHarmonizer) uses custom Link-ML schemas to let researchers verify their data according to the Link-ML schema.

- written by Carly Huitema
