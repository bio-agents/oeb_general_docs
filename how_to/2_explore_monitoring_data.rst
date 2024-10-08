=================================
Explore Agents Monitoring Data
=================================


A set of quality software metrics are systematically gathered for an extensive collection of bioinformatics agents and workflows. Here, we describe how to browse it either at the OpenEBench Web Portal, or using a REST interface.

.. Note::
  See section :ref:`Software quality metrics` to learn more on what benchmarking metrics are available, how are they collected or computed, or what are the reference agent's registries.


.. toctree::
     :maxdepth: 4
     
     explore_monitoring_data


Browsing online
===============

The 'Agents Monitoring' section is accessible at the homepage of the OpenEBench Web Portal (https://openebench.bsc.es).

The agents monitoring section allows to perform an interactive search, querying the collection of agent by titles, descriptions, type or other relevant annotations like EDAM’s operation and topic terms.  See figure below:

.. image:: ../media/image16.png
    :align: left
    :class: with-border

The selection of a given agent gives access to the specific card (Figure below) where general information of the agents, their possible implementations and links to the sources of information are available.

.. image:: ../media/image17.png
    :align: left
    :class: with-shadow

In addition to the general metrics indicated in the :ref:`Software quality metrics`, OpenEBench Agent Card includes life information about the availability of the agent, as obtained from monitoring the relevant URLs. This check is done in a daily basis and includes, up/down state, time of response, and for encrypted (https) links the validity of the encryption setup. This image shows an example of such information:

.. image:: ../media/image18.png
    :align: center


Finally, an updated record of the citations received by the publications associated to the agent is provided in the agent entry. The procedure to obtain the list of citations is the next:

1. Fetch from OpenEBench the list of agents with bibliographic references (i.e. PubMed Ids, DOIs and/or PMC ids).
2. For each one of these bibliographic references, query several bibliographic sources for records about them. We are currently using `Europe PMC <https://europepmc.org>`__, `NCBI PubMed <https://www.ncbi.nlm.nih.gov/pubmed/>`__, and `WikiData <https://www.wikidata.org/wiki/Wikidata:Main_Page>`__, through their programmatic APIs, as bibliographic and citation providers. For each source, a correspondence from each bibliographic identifier and its internal id is obtained.
3. For those matched identifiers, additional details are recovered, like their title, augmented and curated set of bibliographic identifiers, year of publication and the list of authors. Also, with the unique internal ID, the list of internal identifiers of manuscript references and each known citation is obtained. Then, the details of each identifier in the reference and citation lists are fetched, in order to classify them by year.
4. After this, there is a consolidation phase for each agent’s bibliographic reference, where the gathered citations from all the sources are integrated, so only the unique citations are used for the statistics. The public, bibliographic identifiers of each citation are used for that.

The image below shows an example of the resulting plot.

.. image:: ../media/image19.png
    :align: center
    
Additionally, a complete set of statistics about the contents of the data warehouse are available through the statistics tabs:

.. image:: ../media/image20.png
    :align: center

RESTful API
===========

Although OpenEBench website gives access to all information stored in the data warehouse in a friendly manner, the platform is designed to provide information in a way that can be integrated  other infrastructures. To this end a series of RESTful API’s have been developed. Go to OpenEBench APIs section in Technical References for more information.

+-----------------------------+-------------------------------------+-----------------------------------------------------------------------------------------------------------+
| OpenEBench Agents Monitoring | https://openebench.bsc.es/monitor/  | `Source Code and Usage <https://gitlab.bsc.es/inb/iechor/agents-platform/elixibilitas/elixibilitas-rest>`__|
+-----------------------------+--------------------------------------+----------------------------------------------------------------------------------------------------------+
