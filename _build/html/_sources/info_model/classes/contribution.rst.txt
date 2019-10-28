.. _contribution:

Contribution
!!!!!!!!!!!!

.. _artifact:



**Definition**: An action or set of actions performed by an agent toward the creation, modification, evaluation, or deprecation of an artifact. 

**Description and Use:**

* The Contribution class is the the core object in the CAM. They mediate a link between an Agent and an Artifact, and organize information about when, where, how, and in what context the agent contributed to the artifact.
* Ontologically, contributions are considered a type of process or activity. The scope of a Contribution activity includes only the actions of a single agent in contributing to a particular artifact, which may be performed in one continuous effort, or several discontinuous sessions of work.
* Contribution activities may include those leading to the initial creation or subsequent modification of an artifact, as well as activities that evaluate the artifact (e.g. to gauge its quality, completeness, status, or utility), or activities that deprecate an artifact such that it may no longer be used. 


**Information Model:**


.. list-table::
   :header-rows: 1
   :align: left
   :widths: 10 60 5 10 15

   * - Field
     - Description
     - Cardinality
     - Requirement
     - Data Type	 
   * - **id**
     - A unique string that identifies the artifact.
     - 1..1
     - MUST
     - :ref:`identifier <identifier>`
   * - **type**
     - The high-level class to which the artifact belongs (always set to 'Contribution').
     - 1..1
     - MUST 
     - :ref:`class <class>`
   * - **label**
     - A free-text name for the artifact.
     - 0..1
     - MAY
     - :ref:`string <string>`
   * - **description**
     - A free-text description of the artifact.
     - 0..1
     - MAY
     - :ref:`string <string>`
   * - **contribution MadeTo**
     - The artifact toward which the contribution was made.
     - 0..1
     - SHOULD
     - :ref:`Artifact <artifact>`
   * - **contribution MadeBy**
     - The agent that made the contribution.
     - 0..1
     - SHOULD
     - :ref:`Agent <agent>`
   * - **realizedRole**
     - A role indicating the nature of the contribution.
     - 0..m
     - MAY
     - coding <<:ref:`Contribution Role <contribution-role>`>>
   * - **startDate**
     - The date and/or time that the contribution activity began.
     - 0..1
     - MAY
     - :ref:`dateTime <dateTime>`
   * - **endDate**
     - The date and/or time that the contribution activity ended.
     - 0..1
     - MAY
     - :ref:`dateTime <dateTime>`
   * - **duration**
     - The total amount of time the agent spent performing the contribution.
     - 0..1
     - MAY
     - :ref:`duration <duration>`
   * - **occurredAt**
     - The location or locations where the contribution was performed.
     - 0..m
     - MAY
     - :ref:`Location <location>`
   * - **wasSpecifiedBy**
     - A specification (protocol, ruleset, method, guidelines) describing how all or part of the contribution was executed.
     - 0..m
     - MAY
     - :ref:`Method <method>`
   * - **organizational Context**
     - An organization whose resources and/or directives drive the contribution made by an Agent.
     - 0..m
     - MAY
     - :ref:`Organization <organization>`
   * - **wasFundedBy**
     - A grant or other source of resources that paid for the work representing the contribution.
     - 0..m
     - MAY
     - :ref:`Funding Source <funding-source>`
	 
.


**Examples:**
  
* The writing performed by a person toward the creation of a scientific publication (realizes an 'author role')
* The act of sharing of frozen embryonic fibroblasts performed by a researcher toward the creation of a transgenic mouse (realizes a 'resource provision role')
* The task of assembling a lecture slide deck performed by a graduate student in creating an online educational course offering (realizes an 'educational material development role')
* The performance of quality control checks on an integrated data set performed by a data steward toward the creation of a curated knowledgebase (realizes a 'quality assurance role') 
* The act of disposing of a transgenic cell line that was determined to be contaminated.
* The deprecation of an ontology term that its developers decide should not longer be used. 



**Implementation Notes:** 
 
* **Using the Contribution Role Value Set**

    * Use of the :ref:`Contribution Role Value Set <contribution-role>` that is bound to the *realizedRole* attribute above is RECOMMENDED but not required. 
    * Implementations can choose to refine or extend this value set that we provide as part of the CAM specification, or use their own, as described in the :ref:`Implementation Guide <implementation-guide>`.
	
* **‘Placeholder’ Classes** (Location, Method, Funding Source) 

    * At present the CAM considers modeling of Location, Method, and Funding Source to be out of scope, and does not provide concrete models for them. Rather, implementations can determine if and how they want to represent these concepts, and model them accordingly. For example, a Location could be captured simply as a free-text string, or an identifier or code from some controlled vocabulary (e.g. any of a number of existing `gazetteers <https://en.wikipedia.org/wiki/Gazetteer#List_of_gazetteers>`_,  such as `Geonames <https://www.geonames.org/>`_), or using a bespoke or standard location schema (e.g. `ISO19112 <https://test.geo.gob.bo/blog/IMG/pdf/iso_19112.pdf>`_), to create location objects allowing more precise and flexible descriptions.
	
* **Specifying a Contribution Date** (*startDate* and *endDate*): 

    * The model provides *startDate* and *endDate* attributes to allow precise reporting of the time the contribution occurred. Implementations wishing to specify a single time SHOULD simply report the date and/or time that the contribution ended, using the *endDate* attribute, and the *startDate* attribute SHOULD NOT be filled. An empty *startDate* means that the start time is unknown or unspecified.

* **Capturing Multiple Contribution Roles**: 

    * A contribution MUST connect a single Agent to a single Artifact. But a single Contribution object MAY capture multiple roles played by the agent in generating the artifact - simply by including more than one CRO contribution role in the *realizedRole* slot. This pattern provides a more concise representation when data creators do not need to capture details of each role played (i.e. how, when, and where each was realized). In cases where such details for each role are required, separate Contribution objects MUST be created for each role played. 
	
* **Direction of Contribution Relationships**:
  
    * Relationships to and from an Agent or Artifact can be created in a Contribution object. Note here that the *qualifiedContribution* relationship can be used to connect either an Artifact or an Agent to a Contribution. The relationships nd their directionality selected will depend on whether an Artifact- or Agent-centric perspective on the data is being captured. When the goal is to describe all contributions made to a particular Artifact, links are created from Artifact to Contribution to Agent. When the goal is to describe all contributions made by a particular Agent, links are created from AGent to Contribution to Artifact. 





 
