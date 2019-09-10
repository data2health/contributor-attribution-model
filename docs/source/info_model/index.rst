.. _information-model:

Information Model
!!!!!!!!!!!!!!!!!

| `Information Models <https://en.wikipedia.org/wiki/Information_model>`_ (IM) provide informal, language- and format-agnostic representations of a modeling domain.  They abstract over protocol and implementation details to define the characteristics and relationships between concepts. This provides a unifying conceptual model that conveys the semantics and scope of the domain, and guides concrete specifications in any number of formal schema languages (e.g. `JSON schema <https://json-schema.org/specification.html>`_).  

The `Unified Modeling Language <https://www.uml.org/>`_ (UML) diagram in **Figure 2** presents a high-level view of the **Contributor Attribution Information Model (CAM)**. Subsequent pages in this specification, indexed :ref:`below <index1>` and navigable from the menu on the left,  provide detailed descriptions, structural specifications, and implementation guidance for each :ref:`Class <class>`, :ref:`Data Type <data-type>`, and :ref:`Value Set <value-set>`. 

.. figure:: ../images/information_model_uml.png
   :align: center

   **Figure 2:** The UML diagram shows attributes of each core **class**, **relationships** between them, and default **cardinality constraints** and **data types** for data collection.  Specific implementations can refine and extend the model with to suit their domain and use case, as detailed in the :ref:`Implementation Guide <implementation-guide>`. The *italic* font of the Agent class indicates it is an 'abstract class' that is intantiated only through its subtypes.



.. _terms-typo-conventions:

.. important:: **TERMINOLOGICAL AND TYPOGRAPHIC CONVENTIONS IN THIS DOCUMENTATION**
	
	.. General Conventions
	    .. *Bold font is used for emphasis of important terms or points. 
	
    **Modeling Terms**: 
	
          * **'Class'**:  We use the term 'class' to refer to core modeling types in the specification. In other specifications this concept may be referred to as a 'type', 'resource', or 'object'. When referred to as modeling constructs in the text, class names are Capitalized (e.g. Person, Contribution)
          * **'Attribute'**: We use the term 'attribute' to refer to named characteristics or relationships of classes. In other specifications this concept may be referred to as a 'slot', 'element', 'field', or 'property'. When referred to as modeling constructs in the text, attribute names are italicized and camelCased (e.g. *startDate*, *qualifiedContribution*). Contribution attributes are named in past tense because they describe what has already occurred.
          * **'Data Type"**: We use the term 'data type' to refer to more fundamental and general-purpose categories of data objects. These may include ‘simple’ data types (e.g. string, integer, identifier) that are represented as a single literal value, or ‘complex’ data types that are represented as objects with their own attributes (e.g. Coding). When referred to as modeling constructs in the text, complex data types are capitalized, but simple data types are not capitalized or otherwise distinguished.
          * **'Instance'**: We use the term 'instance' or 'object' to refer to instantiations of classes in the data. References to a specific instance in descriptions of data examples are written as ``inline literals`` in red Courier font.
          * **'Value Set'**: We use the term ‘value set’ to refer to named collections of codes that are bound to specific attributes. These are Capitalized in the text and include ‘Value Set’ in their name (e.g. ‘Contribution Role Value Set’)

    **Requirement Specifications**:

          * Requirement levels described in the specificaiton are indicated by use of the capitalized keywords "MUST", "MUST NOT", "SHOULD", "SHOULD NOT", "MAY", “RECOMMENDED”, and “REQUIRED”.
          * These terms are to be interpreted as described in `RFC 2119 <https://www.ietf.org/rfc/rfc2119.txt>`_. 



.. _index1:

.. toctree::
   :maxdepth: 2
   :caption: IM Content Index
   
   classes/index
   data_types
   value_sets