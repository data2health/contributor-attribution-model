## Overview
This repository will hold modeling artifacts and documentation for a data model specification based on the [Contribution Role Ontology](https://github.com/data2health/contributor-role-ontology) to support clear and concise representation of contributions made by agents to research artifacts. Applications for this model may include publishers capturing author contributions to papers, curated knoweldgebases collecting information on curators contributions to annotation records as they matures through the system, research profiling systems describing contributions of researchers to diverse research artifacts, research data management platforms detailing contributions to data objects it manages, and data repositories capturing contributions to submitted data sets it catalogs. In these contexts, the model will support the collection, provision, and exchange of detailed contribution metadata, display of this metadata to system users, and the ability to perform precise contribution-related queries and computational analyses. This work is being completed as part of the [Architecting Attribution](https://github.com/data2health/architecting_attribution) project in the [Center for Data to Health](https://ctsa.ncats.nih.gov/cd2h/).

## Contributors
- Melissa Haendel (MH)
- Matthew Brush (MB)
- Nicole Vasilevsky (NV)
- Marijane White (MJ)
- Anne Thessen (AT)
- Kristi Holmes (KH)
- Lisa O'Keefe (LO)
. . .
  
## Status
The Information Model is currently being developed in draft form [here](https://docs.google.com/document/d/1jMISwIFNj38AUfNZZbT_Osq7vrkmqZYsJ4ubmqEbOa8/edit). Once it is a bit more hardened, it will be moved into a readthedocs website linked to this repository. The other components of the framework listed below will then be generated, based on the content of this Information Model. An initial prototype v0 release is targeted for September 23, 2019.

## Components 
The following components will be developed as part of this effort.  

### 1. A high level information model
**Purpose:** informally define the model in format/language agnostic, and human-friendly way.  
**Deliverable:** a text document that includes: (1) an introduction outlining scope, goals, use cases, and overarching framework for the model, (2) the Information Model itself - described as some combination of UML-like diagrams, tables defining types and attributes in the model, and textual content (definitions, modeling considerations/rationale, and implementation guidance for each type).

### 2. The Contribution Role Ontology (CRO)
**Purpose:** provide ontology terms that map to each type, attribute, and coded values prescribed in the data model (mainly roles and artifact types). This will support creation of semantic data / RDF, and enable ontology-based support for working with contribution metadata
**Deliverable:** a CRO OWL file that includes: (1) the current role hierarchy, with completed term definitions/metadata.  
additional classes and properties needed to provide a complete ontological mapping for the data model; and (2) 
a 'research object/artifact' class hierarchy representing the high-level types of things to which agents contribute. The CRO will live in a separate repository [here](https://github.com/data2health/contributor-role-ontology).

### 3. A formal JSON(-LD) schema implementation of the information model
**Purpose:** provide a computable representation of the model to support data creation/validation.  
**Deliverable:** a JSON schema definition, and LD-context document with mappings between schema elements and ontology terms (from the CRO ontology).

### 4. A tab file format implementation of the information model
**Purpose:** provide a format/tool that poses a low technical barrier to adoption and  can be immediately used by curation efforts, while being easily/directly transformable to more formal representations (e.g. JSON-LD).  
**Deliverable**: a tab file specification document - similar to the [GAF file format spec](http://geneontology.org/docs/go-annotation-file-gaf-format-2.0/) and [HPO annotation format spec](https://hpo-annotation-qc.readthedocs.io/en/latest/annotationFormat.html).

### 5. User Documentation
**Purpose:** provide a centralized source of documentation for the model and ontology, and how they can be used, to support different use cases/stakeholders.  
**Deliverable:** a Github Pages or ReadtheDocs website for the Contribution Model repository that includes information about the motivation and use cases for this work, the overarching modeling framework, the information model, its ontological components, formal schema specifications, and implementation guidance for adopters.

[Architecting Attribution](https://github.com/data2health/architecting_attribution) is part of a suite of projects and activities being carried out by the [Center for Data to Health](https://ctsa.ncats.nih.gov/cd2h/), supported by the National Center for Advancing Translational Sciences (NCATS) at the National Institutes of Health (Grant U24TR002306). To learn more, visit https://ctsa.ncats.nih.gov/cd2h/.
