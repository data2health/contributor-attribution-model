.. _information-model:

Information Model
!!!!!!!!!!!!!!!!!

An Information Model (IM) provides as an informal, language and format agnostic representation of a modeling domain.  Information models provide a unifying conceptual model that conveys the semantics and scope of the domain, and guide concrete implementations in any number of formal schema languages. They  abstract over protocol and implementation details to focus on defining the characteristics of and relationships between domain concepts.  

The Unified Modeling Language (UML) diagram in **Figure 2** presents a high-level view of the Contributor Attribution Information Model.  Subsequent pages in the IM specification provide detailed descriptions,  structural specifications, and implementation guidance for each Class, Data Type, and Value Set that comprise the model.  The CAM framework also provides a formal :ref:`JSON schema <json-schema>` specification of the Information Model, as one of many possible concrete versions data model.


.. figure:: ../images/information_model_uml.png
   :align: center

   **Figure 2**: A UML diagram of the Information Model, depicting attributes of each core class, relationships between them, and default cardinality constraints for data collection. Specific implementations can select from among these attributes, refine default cardinality constraints, and extend the model with type specializations and additional attributes to suit their domain and use case.




.. toctree::
   :maxdepth: 2
   :caption: Index
   
   terms_typo_conventions
   classes/index
   data_types
   value_sets