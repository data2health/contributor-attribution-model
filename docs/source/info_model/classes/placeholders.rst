Placeholder Classes
!!!!!!!!!!!!!!!!!!!

At present the CAM considers modeling of Location, Method, and Funding Source to be out of scope, and does not provide concrete models for them. Rather, implementations can determine if and how they want to represent these concepts, and model them accordingly. Below we describe and provide modeling recommendations for each of these classes, but do not formally define a specification for them.


.. _location:
Location
@@@@@@@@

**Definition:** A place where a contribution was made.


**Description and Use:**

* Location is defined as the type of value for the *occurredAt* attribute of the Contribution class.
* Locations can be referred to in various ways at various levels of granularity and formality - e.g. politically-defined areas such as countries, states or cities, street addresses, zip codes, buildings, spatial coordinates (e.g latitude/longitude).  
* Such locations can be referenced simply as a free-text string, or an identifier or code from some controlled vocabulary (e.g. any of a number of existing `gazetteers <https://en.wikipedia.org/wiki/Gazetteer#List_of_gazetteers>`_,  such as `Geonames <https://www.geonames.org/>`_), or using a bespoke or standard location schema (e.g. `ISO19112 <https://test.geo.gob.bo/blog/IMG/pdf/iso_19112.pdf>`_), to create location objects allowing more precise and flexible descriptions.
* Particular implementations can refine this concept as needed for their use case, and define a formal specification for how to represent it. 

.. _method:
Method
@@@@@@

**Definition:** A set of instructions that specify all or part of how a contribution was made.

**Description and Use:**

* Method is defined as the type of value for the *wasSpecifiedBy* attribute of the Contribution class. A Method SHOULD be referenced in a Contribution object if it informed part or all of the contribution process. In practice, not all contributions are guided by a referenceable method.
* Methods are directive informational artifacts that specify what actions to perform and how to perform them. They can be written at a very general or very precise level of detail.
* Examples include a recipe describing how to make a buffer solution for research, a protocol specifying how to execute an experiment to generate a specific type of data, or rules/guidelines for data curation or interpretation that specify how information can be organized, evaluated, and interpreted to generate new knowledge.
* Particular implementations can refine this concept as needed for their use case, and define a formal specification for how to represent it. 





.. _funding-source:
Funding Source
@@@@@@@@@@@@@@

**Definition:** A funding body or  mechanism that provided resources supporting a contribution.

**Description and Use:**

* Funding Source is defined as the type of value for the *wasFundedBy* attribute of the Contribution class. 

* Particular implementations can refine this concept as needed for their use case, and define a formal specification for how to represent it. 

* Funding Sources MAY be represented at different levels of specificity, including:  

   * A **particular funding body** (e.g. 'NIH', 'NSF', 'Elsevier Labs', an individual person, etc.) 
	
   * A **type/category of funding mechanism** (e.g. ‘grant’, 'NIH grant’,  ‘R01 grant’)

   * A **particular awarded grant or contract** (e.g. ‘NIH award no. 1R24OD011883’) 


