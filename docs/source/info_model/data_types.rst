.. _data-type:

Data Types
!!!!!!!!!!

Data type specifications define more fundamental, general-purpose constructs that provide structure and semantics to data. In addition to a set of classes, the CAM defines a handful of simple and complex data types that define the type of value that a given attribute may take. 

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

    "url": "http://purl.obolibrary.org/obo/cro.owl 
	    (URL of the Contribution Role Ontology)


.. _code:
code
####

**Definition:** a string value that is taken from a set of controlled strings defined by some system or authority

**Description and Use:**

* A code can be opaque (e.g. ``CRO:0000001``, ``90210``) or convey meaning (e.g. ``author``, ``AFR``, ``PDX``)
* In the CAM codes are used primarily within a :ref:`Coding <coding>` object, where they hold the core value of the Coding. Codings and codes are used in Value Sets bound to selected attributes to control data entry.

**Examples of data structures using codes as values:**

 * A ‘Coding’ object, in which the ‘code’ element holds the code "CRO:0000001"::

    “hadRole”: {
       “system”: “http://purl.obolibrary.org/obo/cro.owl”
       “systemVersion”: 1.0, 
       “code”: “CRO:0000001”
       “label”: “author role”
    }
 


.. _identifier:
identifier
##########



.. _class:
class
#####



.. _integer:
integer
#######



.. _date:
date
####



.. _dateTime:
dateTime
########



.. _duration:
duration
########



.. _boolean:
boolean
#######



Complex Data Types
@@@@@@@@@@@@@@@@@
.. _coding:

Coding
######