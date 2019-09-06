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
     - A unique string that identifies the artifact.
     - 1..1
     - MUST
     - :ref:`identifier <identifier>`
   * - **type**
     - The high-level class to which the agent belongs ('Person', 'Organization', or 'Computational Agent').
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
   * - **externalID**
     - Additional identifier(s) for the agent that come from an external system or authority.
     - 0..m
     - MAY
     - :ref:`identifier <identifier>`
   * - **qualified Contribution**
     - A particular contribution made by the agent to an artifact.
     - 0..m
     - MAY
     - :ref:`Contribution <contribution>`
 
. 

**Implementation Notes**

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
* Person is a concrete sublass of Agent. It can be instantiated in the data, and inherits from its abstract parent Agent class. 
* At present the CAM does not define additional person-specific attributes - preferring a minimal but extensible model that allows implementation control over how Persons are represented.

**Information Model:**  

* This class inherits from the :ref:`Agent <agent>` class defined above, and does not define additional attributes.

**Examples:**
  
* In the research domain, examples may include an individual researcher, teacher, curator, administrator, technician, . . .
 
**Implementation Notes:** 
  
* **Person Identifiers**:  

    * Identifiers for Persons SHOULD come from an open and authoritative provider. `ORCIDs <https://orcid.org/>`_ are becoming a de facto standard in this space, and are strongly recommended. But other identifier systems/providers exist (e.g. `ResearcherID <http://www.researcherid.com/>`_, `ISNI <http://www.isni.org/>`_).  

* **Person Contributions in Organizations**: 

    * If the person making a contribution is acting as a member of an organization, this MAY be captured using the organizationalContext attribute of the Contribution class. Alternatively, the Organization itself may be indicated as the agent making the contribution. 

* **Organization Membership:** 

    * The details of a Person’s membership in an Organization (dates they were active, roles/status they held, etc.) could support advanced queries relating contributions to organizational membership (e.g. “Find all contributions made in 2014 by persons who were members of organization X that year”).  Details about organizational membership are not yet represented in the CAM, but this capability may be added in the future, and for now implementations can define their own models to support these use cases.
	 
* **Extensions to the Person Class**: 

    * As noted above, this minimal Person model is meant to be extended with additional attributes by implementations as needed to suit their requirements.  Examples of information that may be useful include given and family name, date of birth, employer, organizational memberships, professional titles, etc.  We recommend looking to community standards such as `FOAF <http://www.foaf-project.org/>`_ to provide modeling constructs here, to facilitate data sharing and interoperability. 




.. _organization:
Organization
@@@@@@@@@@@@

.. _computational-agent:
Computational Agent
@@@@@@@@@@@@@@@@@@@
