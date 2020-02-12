.. _agent:

Agent
!!!!!

**Definition**: An autonomous actor that bears some form of responsibility for an activity taking place, for the existence of an entity, or for another agent's activity.
  
**Description and Use:**
  
* Agents make contributions to Artifacts. An agent can be an individual Person, an Organization of multiple individuals acting together, or a Computational Agent such as a software program or algorithm. 
* Agents can belong to Organizations, and act on behalf or in the context of an Organization when contributing to an Artifact. For example, curators generating these `variant pathogenicity interpretations <https://erepo.clinicalgenome.org/evrepo/ui/classifications?matchMode=exact&gene=PTEN>`_ do so in the context of the `ClinGen organization <https://www.clinicalgenome.org/>`_, which provides administrative, technical, and funding support for their contributions.
* The CAM model for Agent is minimal - providing only a few generic attributes. Future versions may provide more detailed specifications, but at present it is up to implementations to extend this base model as needed to meet their use cases.  


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
     - A unique string that identifies the agent.
     - 1..1
     - MUST
     - :ref:`identifier <identifier>`
   * - **type**
     - The high-level class to which the agent belongs ('Person', 'Organization', or 'Computational Agent').
     - 1..1
     - MUST 
     - :ref:`class <class>`
   * - **label**
     - A free-text name for the agent.
     - 0..1
     - MAY
     - :ref:`string <string>`
   * - **description**
     - A free-text description of the agent.
     - 0..1
     - MAY
     - :ref:`string <string>`
   * - **externalID**
     - Additional identifier(s) for the agent that come from an external system or authority.
     - 0..m
     - MAY
     - :ref:`identifier <identifier>`
   * - **url**
     - A URL where information about the agent can be found.
     - 0..m
     - MAY
     - :ref:`url <url>`
   * - **qualified Contribution**
     - A particular contribution made by the agent to an artifact.
     - 0..m
     - MAY
     - :ref:`Contribution <contribution>`
 
. 

**Implementation Notes:**

* **Agent Instances**:

    * Agent is an **‘abstract class’**, and therefore SHOULD NOT be directly instantiated. A concrete subclass (:ref:`Person <person>`, :ref:`Organization <organization>`, or :ref:`Computational Agent <computational-agent>`) SHOULD be selected to represent any agent in the data. The attributes defined for the abstract Agent are inherited and extended by its two child classes. 

* **Extensions to the Agent Class**: 

    * Implementations requiring more than the minimal attributes provided for describing agents MAY extend the model as needed, following the recommendations in the :ref:`Implementation Guide <implementation-guide>`. Extesnion may involve creating additional attributes for exsiting classes, and/or defineing additional subtypes. We recommend use of community  standards where possible for describing agents (e.g. `FOAF <http://www.foaf-project.org/>`_), to facilitate data sharing and interoperability.  



.. _person:
Person
@@@@@@


**Definition**: A human being.

**Description and Use:**
  
* Persons are human beings with agency who contribute to artifacts.
* Person is a **concrete subclass of Agent**. It can be instantiated in the data, and inherits from its abstract parent Agent class. 
* At present the CAM does not define additional person-specific attributes - preferring a minimal but extensible model that allows implementation control over how Persons are represented.

**Information Model:**  

* This class inherits from the :ref:`Agent <agent>` class defined above, and does not define additional attributes.

**Examples:**
  
* In the research domain, examples may include an individual researcher, teacher, curator, administrator, technician, . . .
 
**Implementation Notes:** 
  
* **Person Identifiers**:  

    * Identifiers for Persons SHOULD come from an open and authoritative provider. `ORCIDs <https://orcid.org/>`_ are becoming a de facto standard in this space, and are strongly recommended. But other identifier systems/providers exist (e.g. `ResearcherID <http://www.researcherid.com/>`_, `ISNI <http://www.isni.org/>`_).  

* **Person Contributions in Organizations**: 

    * If the person making a contribution is acting as a member of an organization, this MAY be captured using the *organizationalContext* attribute of the Contribution class. Alternatively, the Organization itself may be indicated as the agent making the contribution. 
	 
* **Extensions to the Person Class**: 

    * As noted above, this minimal Person model is meant to be extended with additional attributes by implementations as needed to suit their requirements.  Examples of information that may be useful include given and family name, date of birth, employer, organizational memberships, professional titles, etc.  We recommend looking to community standards such as `FOAF <http://www.foaf-project.org/>`_ to provide modeling constructs here, to facilitate data sharing and interoperability. 

* **Membership in Organizations:** 

    * The details of a Person’s membership in an Organization (dates they were active, roles/status they held, etc.) could support advanced queries relating contributions to organizational membership (e.g. “Find all contributions made in 2014 by persons who were members of organization X that year”).  Details about organizational membership are not yet represented in the CAM, but this capability may be added in the future, and for now implementations can define their own models to support these use cases.


.. _organization:
Organization
@@@@@@@@@@@@

**Definition:** A group of agents (typically persons) structured and managed to achieve a common goal. 

**Description and Use:**

* Organization is a **concrete subclass of Agent**. It can be instantiated in the data, and inherits from its abstract parent Agent class. But at present the CAM does not define additional organization-specific attributes.
* Organizations as defined here may include and group of individuals organized around a shared task or goal, including companies, academic interest groups, consortia, charitable foundations, formal research collaborations.  A group does not have to be formally recognized as an organization to be treated as such in the CAM.
* An organization can collectively be credited as making a contribution when it directly or indirectly supports the creation or modification of an artifact, e.g. through funding, defining, directing the work, and/or through its members performing the work.
 
**Information Model:**
  
* This class inherits from the :ref:`Agent <agent>` class defined above, and does not define additional attributes.

**Examples:**

* Scientific consortia such as the `Global Alliance for Genomics and Health <https://www.ga4gh.org/>`_ and `ClinGen <https://clinicalgenome.org/>`_.
* Businesses/companies such as the publisher `Elsevier <https://www.elsevier.com/>`_
* A medical non-profit organization scuch as the `American Heart Association <https://www2.heart.org>`_
* A government agency) such as the `Centers for Disease Control <https://www.cdc.gov/>`_
* A philanthropic fraternity such as `Shriners International <https://www.shrinersinternational.org/>`_
* A group of students assigned to complete a class project
 
**Implementation Notes:** 

* **Capturing Organization Contributions:**

    * Contributions of an organization to an artifact can be captured in two ways: **(1) Directly** as the asserted agent in a contribution, in cases where it reflects the collective effort of a group, or it is not important to capture the roles or actions of individual members acting on behalf of an organization; or **(2) Indirectly** as an organization on whose behalf an individual member's contribution was performed (using the *organizationalContext* attribute of the Contribution class).

* **Extensions to the Organization Class:**

	* As noted above, this minimal Organization model is meant to be extended with additional attributes by implementations as needed to suit their requirements. We recommend looking to community standards such as `FOAF <http://www.foaf-project.org/>`_ to provide modeling constructs here, to facilitate data sharing and interoperability.


.. _computational-agent:
Computational Agent
@@@@@@@@@@@@@@@@@@@


**Definition:** A software program or algorithm that can autonomously execute tasks to achieve a specified goal. 

**Description and Use:**

* A software program need not conceive of or initiate the task on its own to be considered an agent - it must only be capable of autonomously executing a programmed task.


**Information Model:**
  
* This class inherits from the :ref:`Agent <agent>` class defined above, and does not define additional attributes.

**Examples:**

* An `algorist <https://en.wikipedia.org/wiki/Algorithmic_art>`_ (computer algorithm designed to generate art)
* An algorithm that automatically generates an ontology by mining text for Wikipedia

 
**Implementation Notes:** 

    * **Inferring 'Transitive Credit' to Software Creators**
	
	    * As man-made entities, computational agents can be considered Artifacts, and contributions to them can be captured using the CAM. When this is done, 'transitive credit' can be inferred for software creators for Artifacts the software produces.

