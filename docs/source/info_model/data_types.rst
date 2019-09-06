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

**Examples:** (of attributes taking strings as values)

* ``"label": "author role"``
* ``"title": "Semantic Web for Dummies"``
* ``"description": "A cell line derived from cervical tumor cells of a cancer patient"``


.. _url:
url
###


.. _code:
code
####


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