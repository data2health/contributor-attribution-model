Introduction
!!!!!!!!!!!!

| The **Contributor Attribution Model (CAM) Specification** is a standard developed within the `Center for Data to Health <https://github.com/data2health>`_ (CD2H) `Architecting Attribution <https://github.com/data2health/architecting_attribution>`_ project. It provides a **simple and tightly scoped specification** for representing information about contributions made to research-related artifacts - for example when, why, and how a curator contributed to a gene annotation record. 
| It is intended to be **used as a modular component of broader data models** that support data collection and curation systems, to facilitate reliable and consistent exchange of computable contribution metadata. 

Background and Motivation
@@@@@@@@@@@@@@@@@@@@@@@@@
Open science, team science, and a drive to understand meaningful outcomes have transformed research at all levels. Scholars and researchers contribute to research and scholarship in ways that can no longer be recognized via traditional means of publication counts and grant dollars received. Efforts to rigorously attribute, evaluate, and reward such contributions must be built on a data models that facilitate nuanced and computable characterization of research products, and the context in which they are developed and used. Unfortunately, little infrastructure exists to identify, aggregate, present, and understand the impact of non-traditional contributions (e.g. curation or data analysis). Challenges to recognizing these contributions are technical as well as cultural, and addressing them requires an approach that assimilates various perspectives for investigators and organizations, alike.

Here we define a simple yet powerful ontology-based **Contributor Attribution Model (CAM)** Specification that aims to address these challenges, and is comprised of hte following components:

Specification Components
@@@@@@@@@@@@@@@@@@@@



1. An :ref:`information-model` (IM) that represents an informal, format-agnostic specification of the domain.
2. A :ref:`JSON-LD schema <json-schema>` that provides a computable specification of the IM to support data creation and validation. This includes an Linked Data (LD)-context document with mappings between schema elements and ontology terms, enabling the creation of RDF/Linked Data. ``coming soon``
3. A :ref:`Tabular File Format <tsv-format>` representation of the IM that provides a low-tech, curator friendly tool for collecting contribution metadata. ``coming soon``
4.  :ref:`Ontologies <ontologies>` that provide a semantic foundation for the data model. These will support a complete ontological mapping of schema elements and provide terms for value sets - enabling ontological support for operating on contribution metadata. ``coming soon``
5. A :ref:`Code Library and Services <code-and-services>` that can support interconversion of data formats (e.g. tabular to RDF), identifier mappings, and terminology support for building valu sets. ``coming soon``
6. An :ref:`Implementation Guide <implementation-guide>` to support creation of CAM-compliant data in different formats and contexts. ``coming soon``


Modeling Scope
@@@@@@@@@@@@@@

The scope of the Contributor Attribution Model is limited to representing the nature of an agent's contribution to a research artifact - specifically when, where, how, and in what context the contribution was made. It achieves this with a simple and concise model composed of three core classes: an **Artifact**, an **Agent** who contributes to it, and a **Contribution** object that sits between them (**Figure 1**). 

.. figure:: images/introduction_model.png
   :align: center

   **Figure 1**: Definition of core classes and relationships in the CAM. A structured representation of each class can be found in the :ref:`Information Model<information-model>`, and a formal specification provided by a :ref:`JSON schema <json-schema>`.

This three object structure is intended to be used as a **module** in the context of a larger data model that captures the complete semantics of a given domain or use case. Implementations can refine or extend the CAM in different ways to suit their specific domain and use case, as described in more detail in the :ref:`implementation-guide`. 

Application Use Cases
@@@@@@@@@@@@@@@@@@@@@
Applications implementing CAM-based modules may include:

* **Publishers** capturing author contributions to papers.
* **Curated knoweldgebases** collecting information on curators contributions to annotation records as they mature through the system.
* **Research profiling applications** describing contributions to diverse types of scholarly outputs.
* **Research data management platforms** detailing contributions to data objects they manage.
* **Data repositories** capturing contributions to cataloged data sets.
* **Software development platforms** capturing contributions to code and other software artifacts. 

In these contexts, the model can support the **collection**, **provision**, and **exchange** of detailed contribution metadata, **display** of this metadata to system users, and the ability to perform precise contribution-related **queries** and **computational analyses**.


A Simple Example
@@@@@@@@@@@@@@

*TO DO: add exampe of a curator contribution to a CIViC database record.*


Additional and more complex examples can be found in the :ref:`implementation-guide`.
