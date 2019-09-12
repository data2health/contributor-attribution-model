.. Contribution Model documentation master file, created by
   sphinx-quickstart on Tue Sep  3 09:48:09 2019.

Welcome to the Contributor Attribution Model
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

The **Contributor Attribution Model (CAM) Specification** is a standard developed within the `Center for Data to Health <https://github.com/data2health>`_ (CD2H) `Architecting Attribution <https://github.com/data2health/architecting_attribution>`_ project. It provides a **simple and tightly scoped data model** for representing information about contributions made to research-related artifacts - for example when, why, and how a curator contributed to a gene annotation record. This core model is intended to be **used as a modular component of broader data models** that support data collection and curation systems, to facilitate reliable and consistent exchange of computable contribution metadata. Additional components of the CAM specification support implementation of the model, data collection, and ontology-based query and analysis of contribution metadata. 
  
The final CAM Specification will be comprised of the following **six components**. More information about each can be found using the links below, or navigating the **Site Contents** menu to the left.

1. A format-agnostic :ref:`information-model` of the domain.
2. A formal :ref:`JSON-LD schema <json-schema>` serialization of the Information Model. ``coming soon`` 
3. A :ref:`TSV format and curation template <tsv-format>`, based on the Information Model. ``coming soon``
4. :ref:`Ontologies <ontologies>` and :ref:`LD-Context Mappings <ld-context>` to support creation of RDF linked data. ``coming soon``
5.  A :ref:`code library and services <code-and-services>` to support data creation and format interchange. ``coming soon``
6. An :ref:`Implementation Guide <implementation-guide>` to support creation of CAM-compliant data in different formats and contexts. ``coming soon``

.. note:: At present only the foundational :ref:`information-model` has been defined, along with the supporting :ref:`Contribution Role Ontology (CRO) <cro-ontology>`. We expect an initial draft of all six components to be complete and ready for a v0 release by the end of Spetember 2019.  

.. toctree::
   :maxdepth: 4
   :caption: Site Contents

   introduction
   info_model/index
   schema/index
   ontologies
   tsv_format
   code_and_services
   implementation_guide/index
   appendices/index





.. Indices and tables
.. !!!!!!!!!!!!!!!!!!
.. * :ref:`genindex`
.. * :ref:`modindex`
.. * :ref:`search`
