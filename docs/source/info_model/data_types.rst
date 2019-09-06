.. _data-type:

Data Types
!!!!!!!!!!

'Data type' specifications define more fundamental, general-purpose constructs that provide structure and semantics to data. In addition to a set of classes, the CAM provides a handful of simple and complex data types that are used to specify the type of value that a given attribute may take. 

.. toctree::
   :maxdepth: 3
   :caption: Contents
   
   data_types



Simple Data Types
@@@@@@@@@@@@@@@@@

.. _string:
string
######

**Definition:** a sequence of Unicode characters

**Description and Use:**

* The string data type represents free-text that is not constrained to some code set or associated with some semantic interpretation
* It is the most generic form of free-text literal in our model, and conceptually subsumes string-based data types with more constrained interpretations (e.g. code, identifier, url)   identifiers)  
* It is most often used to capture names and free-text descriptions of entities in the model or data.

**Examples of attributes taking strings as values**::

    "label": "author role"    
    "title": "Semantic Web for Dummies"    
    "description": "A cell line derived from cervical tumor cells of a cancer patient"
	

.. _url:
url
###

**Definition:** A Uniform Resource Locator (RFC 1738) representing a web address where a resource can be found or information about the resource discovered. Common URL protocols are http{s}:, ftp:, mailto: and mllp:, though many others are defined.

**Description and Use:**

* Used in place of a plain string datatype when a resolvable web address for a resource is desired.
* URLs with an http{s} protocol are preferred where available.

**Examples of attributes taking a url as values**::

    "systemURL": "http://purl.obolibrary.org/obo/cro.owl 


.. _code:
code
####

**Definition:** a string value that is taken from a set of controlled strings defined by some system or authority

**Description and Use:**

* A code can be opaque (e.g. ``CRO:0000001``, ``90210``) or convey meaning (e.g. ``author``, ``AFR``, ``PDX``)
* Codes are used primarily within a :ref:`Coding <coding>` object, where they hold the core value of the Coding. Codings and codes are used in Value Sets bound to selected attributes to control data entry.
* Codes are used primarily within a :ref:`Coding <coding>` object, where they hold the core value of the Coding. Codings and codes are used in Value Sets bound to selected attributes to control data entry.

**Examples of data structures using codes as values:**

 A ‘Coding’ object, in which the ‘code’ element holds the code "CRO:0000001"::

    "realizedRole”: {
       “system”: “http://purl.obolibrary.org/obo/cro.owl”
       “systemVersion”: 1.0, 
       “code”: “CRO:0000001”
       “label”: “author role”
    }
 


.. _identifier:
identifier
##########

**Definition:** A string that uniquely identifies a specific instance of an object in a dataset or document.

**Description and Use:**

* An identifier refers to exactly one instance, but a given instance in the data may be associated with more than one identifier.
* Identifiers SHOULD be globally unique, persistent, and machine-resolvable.
* Use of the `W3C Compact URI (CURIE) <https://www.w3.org/TR/curie/>`_ syntax to structure identifiers is one way to meet these criteria. CURIEs consist of prefix and reference components that correspond to a namespace and local identifier within that namespace, respectively, and are deterministically expandable into a full URI.  
* It is strongly RECOMMENDED, but not required, that identifiers are represented using CURIE or URI syntax. General guidelines and identifier best practices, including use of CURIEs, are well described `here <https://doi.org/10.1371/journal.pbio.2001414>`_ and `here <https://doi.org/10.1038/sdata.2018.29>`_. 
* Instance identifiers can be generated de novo by a system creating data, or borrowed from external systems/authorities that mint identifiers (e.g. databases, registries, ontologies). For example, a Person instance can be assigned a de novo internal identifier by the system generating the record (e.g. ex:12345), or the system can choose to use an established ORCID for that person (e.g. ``orcid:0000-0002-1048-5019``). For de novo identifiers, we strongly recommend the use of a services such as `w3id <https://w3id.org/>`_ to enable web resolution (even if simply resolving to an informal document providing minimal metadata about each identifier).
* If a system wishes to capture both an internal and external identifiers, the internal one should be captured in the *identifier* attribute, and the *externalId* attribute can be used to record one or more established identifiers from community authorities.
 
**Examples of attributes taking identifiers as values**:

CURIEs::

    "identifier": “orcid:0000-0002-1048-5019”
    "identifier": “pmid:123456”
    "identifier": “ga4gh:VX60NSGLem4X3Q8gnOSx48pZDCmJVSUk”
    "externalId": “doi:10.1111/2041-210x.12970” 
    "externalId": “IGSN:ECS000004”
	
Full URIs::

    "identifier": "http://doi.org/10.1111/2041-210x.12970"
    "identifier": “http://n2t.net/ark:/65665/3f09e18cb-fb47-4ea8-ae3b-694a89ea8ff4”
 
Non-CURIE/URI Identifiers::

    "identifier": “USNMENT00945454”
    "identifier": "MGI41353"


.. _class:
class
#####

**Definition:** a string value representing the class of objects to which an instance belongs.

**Description and Use:**

* This string MUST be the name of a concrete class from the base CAM specification (i.e. one of Artifact, Contribution, Person, Organization, Computational Agent, Location, Method, Funding Source), or a specialization of such a class in an extension defined by a particular implementation.
* Note that when an attribute bound to a value set takes an ontology class (e.g. a CRO term in the :ref:`Contribution Role Value Set <contribution-role>`), the :ref:`Coding <coding>` data type MUST be used - as the class data type is reserved for specifying the type of proper instances in a dataset. 


.. _date:
date
####

**Definition:** specifies a date comprised of a year, month, and day, following the form "YYYY-MM-DD", with an optional time zone parameter.

**Description and Use:**

* The date data type is used when precision down to a specific day is required, but not a specific time of day.
* Conventions for representing dates defined here are based on the `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_ standard. 
* A time zone can be indicated by appending a "Z" to specify UTC time (e.g. ``"1978-01-20Z"``), or specifying an offset from UTC time by adding positive or negative time after the date (e.g. ``"1978-01-20+5:00"``)

**Examples of attributes taking dates values**::

    "startTime": "2018-04-12TZ"
    "startTime": "1998-12-18T+06:00"


.. _dateTime:
dateTime
########

**Definition:** specifies a date and time of day comprised of a year, month, day, hour, minute, and second, following the form "YYYY-MM-DDThh:mm:ss"

**Description and Use:**

* The dateTime data type is used when precision down to a specific time of day is required.
* Conventions for representing date + time defined here are based on the `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_ standard. 
* Hours of the day should use 24-hour time (e.g. 2PM = 14:00:00)
* A time zone can be specified as described for 'dates' above, e.g. ``"1978-01-20T05:15:00Z``, and ``"1978-01-20T05:15:00+5:00"``.
* If precision down to time of day is not possible or necessary, the hours, minutes, and seconds must still be provided due to schema constraints, but can all be set to "00" and ignored at the instruction of the message sender.

**Examples of attributes taking dateTime values**::

    "startTime": "2018-04-12T11:05:25+08:00"
    "startTime": "2004-09-05T00:00:00Z" 

.. _duration:
duration
########

**Definition:** specifies a length of time, using the form "PnYnMnDTnHnMnS"

**Description and Use:**

* The duration data type should be used to directly assert the length of time a contribution took to perform.
* Conventions for representing duration defined here are based on the `ISO 8601 <https://en.wikipedia.org/wiki/ISO_8601>`_ standard. 
* A 'P' prefix and at least one of the temporal components below is required in a duration value:

    * 'nY' indicates a number of years
    * 'nM' indicates a number of months
    * 'nD' indicates a number of days
    * 'T' indicates the start of a time section (required to specify precision down to hours, minutes, or seconds)
    * 'nH' indicates a number of hours
    * 'nM' indicates a number of minutes
    * 'nS' indicates a number of seconds


**Examples of attributes taking duration values**::

    "duration": "P8Y"  (8 years)
    "duration": "P8Y4M15D"  (8 years 4 months 15 days)
    "duration": "P8Y4M15DT2H6M35S"  (8 years 4 months 15 days 2 hours 6 minutes 35 seconds)
    "duration": "P8Y215D"  (8 years 215 days)
    "duration": "PT2H6M35S"  (2 hours 6 minutes 35 seconds)
    "duration": "PT35S"  (35 seconds)


Complex Data Types
@@@@@@@@@@@@@@@@@

In contrast to ‘simple’ data types, ‘complex’ data types specify structured objects with attributes of their own. These objects do not represent primary domain entities, are not 'identified' in the data.

.. _coding:

Coding
######

**Definition:** a structured representation of a :ref:`code <code>` from some code system, that includes additional metadata about the code and code system.

**Description and Use:**

* The specification for this data type was adapted from the `FHIR 'Coding' <https://www.hl7.org/fhir/datatypes.html#Coding>`_ data type. It provides a structure to include additional metadata about a 'code' used to capture data in a dataset - for example, the human-readable name for the code, or the code system from which it came. In this way it differs from the primitive 'code' data type, which specifies only a string value representing the code itself.
* The CAM opts to require a Coding object in places where a value set is bound to an attribute, rather than allowing direct capture of the code alone, as we believe that users will minimally want to see the human-readable name of the code in a message or dataset.

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
   * - **system**
     - The code system where the code is defined.
     - 0..1
     - MAY
     - :ref:`string <string>`
   * - **systemURL**
     - A URL where the code system can be found.
     - 0..1
     - MAY
     - :ref:`url <url>`
   * - **systemVersion**
     - The version of the code system.
     - 0..1
     - MAY
     - :ref:`string <string>`
   * - **code**
     - The value of the code itself.
     - 1..1
     - MUST
     - :ref:`code <code>`
   * - **label**
     - A human-readable name for the code.
     - 0..1
     - MAY
     - :ref:`string <string>`

.


**Examples of data structures using Codings as values:**

 A ‘Coding’ object, in which the ‘code’ element holds the code "CRO:0000001"::

    “realizedRole”: {
       “system”: “http://purl.obolibrary.org/obo/cro.owl”
       “systemVersion”: 1.0, 
       “code”: “CRO:0000001”
       “label”: “author role”
    }
 
