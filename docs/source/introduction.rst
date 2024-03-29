Overview
!!!!!!!!

The **Contributor Attribution Model (CAM) Specification** is a standard developed within the `Center for Data to Health <https://github.com/data2health>`_ (CD2H) `Architecting Attribution <https://github.com/data2health/architecting_attribution>`_ project. It provides a **simple and tightly scoped data model** for representing information about contributions made to research-related artifacts - for example when, why, and how a researcher contributed to a publication, or a curator contributed to a gene annotation record. This core model is intended to be **used as a modular component of larger data models** that underpin data collection and curation systems. Additional components of the CAM specification support implementation of the model, data collection using the model, and ontology-based query and analysis of contribution metadata. 

Background and Motivation
@@@@@@@@@@@@@@@@@@@@@@@@@
Open science, team science, and a drive to understand meaningful outcomes have transformed research at all levels. Scholars and researchers contribute to research and scholarship in ways that can no longer be recognized via traditional means of publication counts and grant dollars received. Efforts to rigorously attribute, evaluate, and reward such contributions must be built on a data models that facilitate nuanced and computable characterization of research products, and the context in which they are developed and used. Unfortunately, little infrastructure exists to identify, aggregate, present, and understand the impact of non-traditional contributions (e.g. curation or data analysis). Challenges to recognizing these contributions are technical as well as cultural, and addressing them requires an approach that assimilates various perspectives for investigators and organizations, alike.

| Here we define an ontology-based **Contributor Attribution Model (CAM)** specification that aims to address these challenges. The data model itself was designed to be **as simple, intuitive, and concise a representation as possible**, so as to minimize barriers to adoption by diverse systems where use of community standards has historically been an unexplored or prohibitive endeavor.  
| The specification as a whole includes the following components:

Specification Components
@@@@@@@@@@@@@@@@@@@@


1. An :ref:`information-model` (IM) that provides an informal, format-agnostic specification for representing contribution data.
2. A :ref:`JSON-LD schema <json-schema>` that provides a computable specification of the IM to support data creation and validation. This includes an Linked Data (LD)-context document with mappings between schema elements and ontology terms, enabling the creation of RDF/Linked Data. ``coming soon``
3. A :ref:`Tabular File Format <tsv-format>` representation of the IM that provides a low-tech, curator friendly tool for collecting contribution metadata. ``coming soon``
4.  :ref:`Ontologies <ontologies>` that provide a semantic foundation for the data model. These will support a complete ontological mapping of schema elements and provide terms for value sets - enabling ontological support for operating on contribution metadata. ``coming soon``
5. A :ref:`Code Library <code>` that can support interconversion of data formats (e.g. tabular to RDF), identifier mappings, and terminology support for building valu sets. ``coming soon``
6. An :ref:`Implementation Guide <implementation-guide>` to support creation of CAM-compliant data in different formats and contexts. ``coming soon``


Modeling Scope
@@@@@@@@@@@@@@

The scope of the Contributor Attribution Model is limited to representing the nature of an agent's contribution to a research artifact - specifically when, where, how, and in what context the contribution was made. It achieves this with a simple and concise model composed of three core classes: an **Artifact**, an **Agent** who contributes to it, and a **Contribution** object that sits between them (**Figure 1**). 

.. figure:: images/introduction_model.png
   :align: center

   **Figure 1**: Definition of core classes and relationships in the CAM. Details about each class can be found in the :ref:`Information Model<information-model>`, and a formal specification is provided by a :ref:`JSON schema <json-schema>`.

This three object structure is intended to be used as a **module** in the context of a larger data model that captures the complete semantics of a given domain or use case. Implementations can refine or extend the CAM in different ways to suit their specific domain and use case, as described in more detail in the :ref:`implementation-guide`. 


Relationship to PROV
@@@@@@@@@@@@@@@@@@@@
The scope of the CAM overlaps with a subset of the `W3C PROV specification <https://www.w3.org/2011/prov/wiki/Main_Page>`_ that covers agent attribution, but CAM has been tailored to fit the Contribution use case more directly and succinctly. While informed by the work of PROV, CAM was developed independently due to a few small but significant semantic and normative incompatibilities (see :ref:`Appendix I <relationship-to-standards>`), which prevented PROV from meeting our primary use case for as simple and concise a model as possible to connect an Artifact to an account of Agent contributions. 

Mappings between the CAM and PROV models will be provided in :ref:`Appendix I <relationship-to-standards>`, where areas of semantic incompatibility and efforts toward harmonization are also discussed. Mappings between the CAM and the `FHIR Provenance resource <https://www.hl7.org/fhir/provenance.html>`_, , will also be described here.


Application Use Cases
@@@@@@@@@@@@@@@@@@@@@
Applications implementing CAM-based modules may include:

* **Publication Databases** capturing author contributions to papers.
* **Curated knoweldgebases** collecting information on curators contributions to annotation records as they mature through the system.
* **Research profiling applications** describing contributions to diverse types of scholarly outputs.
* **Research data management platforms** detailing contributions to data objects they manage.
* **Data repositories** capturing contributions to cataloged data sets.
* **Software development platforms** capturing contributions to code and other software artifacts. 

In these contexts, the model can support the **collection**, **provision**, and **exchange** of detailed contribution metadata, **display** of this metadata to system users, and the ability to perform precise contribution-related **queries** and **computational analyses**. 


Data Examples
@@@@@@@@@@@@@


**1. An Author Contribution to a Journal Article**  

This simple example includes minimal metadata describing one author's contribution to the publication of a `journal article <https://journals.plos.org/plosgenetics/article?id=10.1371/journal.pgen.1006186#authcontrib>`_, structured according to the CAM specification. The Conribution object in this record describes the role the agent played, and the organizational context in which the contribution was made.

::

	"id": "doi:10.1371/journal.pgen.1006186", # the Artifact (a published journal article)
	"type": "camo:Artifact",
	"artifactType": "wd:Q18918145"  # Journal Article,
	"label": "Epistatic Gene-Based Interaction Analyses for Glaucoma in eMERGE and NEIGHBOR Consortium",
	"dateCreated": "2016-09-13",
	"qualifiedContribution": [    # the Contribution object
                {
		"id": "ex:contribution001",
		"type": "cro:Contribution",
		"contributionMadeBy":    # the Agent
			{
			"id": "ex:agent001",
			"type": "camo:Agent",
			"label": "Cathy McCarty",
			"externalId": orcid:1234-5678-XXXX
			},
		"realizedRole":   # the specific role they played
			{
			"code": "cro:0000055",
			"label": "study design role",
			"system": "Contribution Role Ontology",
			"systemURL": "http://purl.obolibrary.com/obo/cro.owl"
			},
		"organizationalContext":   # an organization they acted within when making the contribution
			{
			"id": "ex:org001",
			"type": "camo:Organization",
			"label": "eMERGE Network",
			"url": "https://emerge.mc.vanderbilt.edu/"
			}
                }
	]


**2. A Curator Contribution to a CIViC Database Record**  

This richer example includes more extensive contribution metadata from `this variant interpretation record <https://civicdb.org/api/assertions/10>`_ in the CIViC Knowledgebase, structured according to the CAM specification. The record includes details of **when**, **how**, **where**, and **in what context** contributions were made by four agents during the life-cycle of this curated record. The example below captures just one of these contributions, but the `complete example describing all four dontributions is here <https://github.com/data2health/contributor-attribution-model/blob/master/examples/civic_aid10_example.yaml>`_. 

::

	"id": "civic:AID10",  # the Artifact (a curated variant interpretation record)
	"type": "camo:Artifact",
	"artifactType": "wd:Q49848",
	"label": "AID10",
	"description": "Vemurafenib and cobimetinib combination is an...",
	"url": "https://civicdb.org/api/assertions/10",
	"dateCreated": "2018-11-08T16:42:21.820Z",
	"qualifiedContribution": [   # the Contribution
		{
		"id": "ex:contribution001",
		"type": "cro:Contribution",
		"endDate": "2018-11-01T18:54:05.924Z",
		"contributionMadeBy":    # the Agent
			{
			"id": "civic:110",
			"type": "camo:Agent",
			"externalId": "orcid:0000-0001-9815-2288",
			"label": "Arpad Danos",
			"_display_name": "arpaddanos",
			"_expertise": "Research Scientist",
			"_orgRole": "admin"
			},
		"realizedRole": [    # here multiple roles are captured in a single Contribution object
			{
			"code": "cro:0000XXX",
			"label": "creator role",
			"system": "Contribution Role Ontology",
			"systemURL": "http://purl.obolibrary.com/obo/cro.owl"
			},
			{
			"code": "cro:0000105",
			"label": "submitter role",
			"system": "Contribution Role Ontology",
			"systemURL": "http://purl.obolibrary.com/obo/cro.owl"
			}
		   ],
		"organizationalContext":   # an Organization they acted within when making the Contribution
			{
			"id": "wd:Q27612411",
			"type": "camo:Organization",
			"label": "Clinical Interpretation of Variants in Cancer (CIViC)",
			"url": "https://civicdb.org/"
			},
		"wasSpecifiedBy":    # a Method that guided how the contribution was made
			{
			"id": "doi:10.1101/700179",
			"type": "camo:Method",
			"label": "The CIViC knowledge model and standard operating procedures for curation and clinical interpretation of variants in cancer"
			},
		"occurredAt":   # the Location where the contribution was made
			{
			"id": "civic:214",
			"type": "camo:Location",
			"label": "United States",
			"externalID": "iso:US"
			}
	    }
	]

**Additional Notes:** 

* Expansions of json keys and identifier prefixes in the data above will be provided in a :ref:`JSON-LD context file <ld-context>`.  
* Attributes preceded by an underscore (e.g. ``"_expertise"``) represent extensions to the core CAM model that CIViC might create to capture application-specific content in their system.'
* Additional data examples will be provided as part of the :ref:`Implementation Guide <implementation-guide>`.

.. important:: How concepts such as **Organizations**, **Methods**, and **Locations** are represented is not in scope for the CAM, and is left to implementations to decide.  In the CIViC example above, a structured json object is created to represent these concepts and a few attributes of each. But implementations could choose to capture organization, method, and location values as simple strings if desired, for a much more concise representation. For example: 

::

	"organizationalContext":  "Clinical Interpretation of Variants in Cancer (CIViC)",
	
	"wasSpecifiedBy": "The CIViC SoP for curation and clinical interpretation of variants in cancer",
	
	"occurredAt": "United States"



