.. Contribution Model documentation master file, created by
   sphinx-quickstart on Tue Sep  3 09:48:09 2019.

Contributor Attribution Model
!!!!!!!!!!!!!!!!!!!!!!!

The Contributor Attribution Model (CAM) is a standard developed within the `Center for Data to Health <https://github.com/data2health>`_ (CD2H) `Architecting Attribution <https://github.com/data2health/architecting_attribution>`_ project. It provides a simple and modular specification for representing information about contributions made to research-related artifacts. For example, describing when, why, and how a curator contributed to a gene annotation record. Use of this model in the context of data collection and curation systems can facilitate reliable and consistent exchange of computable contribution metadata. 
  
The final CAM Specification will be comprised of the following components: 

1. A format-agnostic :ref:`information-model` of the domain.
2. A :ref:`JSON-LD schema <json-schema>` formalization of the Information Model.
3. A :ref:`TSV-based format and curation template <tsv-format>`, based on the Information Model.
4. :ref:`Ontologies <ontologies>` and :ref:`LD-Context Mappings <ld-context>` to support creation of RDF linked data.
5.  A :ref:`code library and services <code-and-services>` to support format interchange and identifier and terminology use.
6. An :ref:`Implementation Guide <implementation-guide>` to support creation of CAM-compliant data in different formats and contexts.

At present only the foundational :ref:`information-model` has been defined, along with the supporting :ref:`Contribution Role Ontology (CRO) <cro-ontology>`. We expect an initial draft of all five components to be complete and ready for a v0 release by the end of Spetember 2019.  

.. toctree::
   :maxdepth: 4
   :caption: Site Contents

   introduction
   info_model/index
   schema/index
   ontologies
   code_and_services
   implementation_guide/index





.. Indices and tables
.. !!!!!!!!!!!!!!!!!!
.. * :ref:`genindex`
.. * :ref:`modindex`
.. * :ref:`search`
