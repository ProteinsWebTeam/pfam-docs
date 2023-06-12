************************************
Querying Pfam using the InterPro API 
************************************

This is an introduction to the `InterPro API <https://www.ebi.ac.uk/interpro/api>`_ to retrieve Pfam annotations. A programmatic interface, 
commonly called an `Application Programming Interface <http://en.wikipedia.org/wiki/Api>`_ (API) allows users to write scripts or programs 
to access data, rather than having to rely on a browser to view a site.


Basic concepts
==============

URLs
----

A RESTful service typically sends and receives data over `HTTP <http://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol>`_, 
the same protocol that's used by websites and browsers. As such, the services provided through a RESTful interface are identified using URLs.

In the InterPro website we use a different URL to provide the standard HTML representation of Pfam data and the alternative 
programmatic JSON format through the API. 

To see the data for a particular Pfam-A family, you would visit the following URL in your browser:

  `/entry/pfam/PF02171/ <https://www.ebi.ac.uk/interpro/entry/pfam/PF02171/>`_

To retrieve the data in JSON format, just add an extra parameter, **api**, to the URL:

  `/api/entry/pfam/PF02171/ <https://www.ebi.ac.uk/interpro/api/entry/pfam/PF02171/>`_

The response from the server will now be an JSON document, rather than an HTML page. 

The table below lists the website vs API url (scroll the table to right/left to see the corresponding API url):

+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Data                                            | Example website url                                                                                                    | Example API url                                                                                                                |
+=================================================+========================================================================================================================+================================================================================================================================+
| List all Pfam entries                           | `/entry/pfam/#table <https://www.ebi.ac.uk/interpro/entry/pfam/#table>`_                                               | `/api/entry/pfam/ <https://www.ebi.ac.uk/interpro/api/entry/pfam/>`_                                                           |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| List all Pfam entries of type Family            | `/entry/integrated/pfam/?type=family#table <https://www.ebi.ac.uk/interpro/entry/integrated/pfam/?type=family#table>`_ | `/api/entry/pfam/?type=family <https://www.ebi.ac.uk/interpro/api/entry/pfam/?type=family>`_                                   |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Information about a specific Pfam entry         | `/entry/pfam/PF02171/ <https://www.ebi.ac.uk/interpro/entry/pfam/PF02171/>`_                                           | `/api/entry/pfam/PF02171/ <https://www.ebi.ac.uk/interpro/api/entry/pfam/PF02171/>`_                                           |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| List of proteins matching a specific entry      | `/entry/pfam/PF02171/protein/UniProt/ <https://www.ebi.ac.uk/interpro/entry/pfam/PF02171/protein/UniProt/>`_           | `/api/protein/UniProt/entry/pfam/PF02171/ <https://www.ebi.ac.uk/interpro/api/protein/UniProt/entry/pfam/PF02171/>`_           |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Different domain architectures matching         | `/entry/pfam/PF02171/domain_architecture/ <https://www.ebi.ac.uk/interpro/entry/pfam/PF02171/domain_architecture/>`_   | `/api/entry/pfam/PF02171?ida <https://www.ebi.ac.uk:443/interpro/api/entry/pfam/PF02171?ida>`_                                 |
|a specific entry                                 |                                                                                                                        |                                                                                                                                |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| List of PDB structures matching                 | `/entry/pfam/PF02171/structure/PDB/ <https://www.ebi.ac.uk/interpro/entry/pfam/PF02171/structure/PDB/>`_               | `/api/structure/PDB/entry/pfam/PF02171/ <https://www.ebi.ac.uk/interpro/api/structure/PDB/entry/pfam/PF02171/>`_               |
|a specific entry                                 |                                                                                                                        |                                                                                                                                |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| Download the PDB file of the predicted          | `/entry/pfam/PF14331/rosettafold/ <https://www.ebi.ac.uk/interpro/entry/pfam/PF14331/rosettafold/>`_                   | `/api/entry/pfam/PF14331?model:structure <https://www.ebi.ac.uk:443/interpro/api/entry/pfam/PF14331?model:structure>`_         |
|structure from RoseTTAFold                       |                                                                                                                        |                                                                                                                                |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
|                                                 |                                                                                                                        |                                                                                                                                |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| List all Pfam clans/sets                        | `/set/all/entry/pfam/#table <https://www.ebi.ac.uk/interpro/set/all/entry/pfam/#table>`_                               | `/api/set/pfam <https://www.ebi.ac.uk/interpro/api/set/pfam>`_                                                                 |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| List of Pfam entries in                         | `/set/pfam/CL0219/entry/pfam/ <https://www.ebi.ac.uk/interpro/set/pfam/CL0219/entry/pfam/>`_                           | `/api/entry/pfam/set/pfam/CL0219?page_size=100 <https://www.ebi.ac.uk/interpro/api/entry/pfam/set/pfam/CL0219?page_size=100>`_ |
|a specific clan/set                              |                                                                                                                        |                                                                                                                                |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
| General information about a specific clan/set   | `/set/pfam/CL0219/ <https://www.ebi.ac.uk/interpro/set/pfam/CL0219/>`_                                                 | `/api/set/pfam/CL0219 <https://www.ebi.ac.uk/interpro/api/set/pfam/CL0219>`_                                                   |
+-------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

Available outputs formats
-------------------------

By default, the output of the API calls are in JSON format. However, we also support Text and TSV formats. To obtain the results in Text or TSV format,
add the `?format=txt` or `?format=tsv` to the API url.

Examples of API outputs
=======================

Pfam-A annotations
------------------

You can retrieve a sub-set of the data in a Pfam-A family page as an JSON document using the following URL:
`/api/entry/pfam/PF02171 <https://www.ebi.ac.uk/interpro/api/entry/pfam/PF02171>`_

.. code-block:: bash

  HTTP 200 OK
  Allow: GET, HEAD
  Content-Type: application/json
  InterPro-Version: 94.0
  InterPro-Version-Minor: 3
  Vary: Accept

  {
      "metadata": {
          "accession": "PF02171",
          "entry_id": null,
          "type": "family",
          "go_terms": null,
          "source_database": "pfam",
          "member_databases": null,
          "integrated": "IPR003165",
          "hierarchy": null,
          "name": {
              "name": "Piwi domain",
              "short": "Piwi"
          },
          "description": [
              "<p>This domain is found in the protein Piwi and its relatives.  The function of this domain is the dsRNA guided hydrolysis of ssRNA. Determination of the crystal structure of Argonaute reveals that PIWI is an RNase H domain, and identifies Argonaute as Slicer, the enzyme that cleaves mRNA in the RNAi RISC complex [[cite:PUB00020128]].  In addition, Mg+2 dependence and production of 3'-OH and 5' phosphate products are shared characteristics of RNaseH and RISC. The PIWI domain core has a tertiary structure belonging to the RNase H family of enzymes.  RNase H fold proteins all have a five-stranded mixed beta-sheet surrounded by helices. By analogy to RNase H enzymes which cleave single-stranded RNA guided by the DNA strand in an RNA/DNA hybrid, the PIWI domain can be inferred to cleave single-stranded RNA, for example mRNA, guided by double stranded siRNA.</p>"
          ],
          "wikipedia": {
              "title": "Argonaute",
              "extract": "<p>The <b>Argonaute</b> protein family, first discovered for its evolutionarily conserved stem cell function, plays a central role in RNA silencing processes as essential components of the RNA-induced silencing complex (RISC). RISC is responsible for the gene silencing phenomenon known as RNA interference (RNAi). Argonaute proteins bind different classes of small non-coding RNAs, including microRNAs (miRNAs), small interfering RNAs (siRNAs) and Piwi-interacting RNAs (piRNAs). Small RNAs guide Argonaute proteins to their specific targets through sequence complementarity, which then leads to mRNA cleavage, translation inhibition, and/or the initiation of mRNA decay.</p>",
              "thumbnail": "iVBORw0KGgoAAAANSUhEUgAAAUAAAAERCAYAAAAKQn74AAAABmJLR0QA/wD/AP+plGSa52gioXAaa3IEVq0YtzeLBALwLopkkEqrtLV1UFV1Bi5X3tc2hQbOd2BxHJxefuXrDIOykhL2rFvHJ+3tlE6fzkljxnD1+..."
          },
          "literature": {
              "PUB00020128": {
                  "PMID": 15284453,
                  "ISBN": null,
                  "volume": "305",
                  "issue": "5689",
                  "year": 2004,
                  "title": "Crystal structure of Argonaute and its implications for RISC slicer activity.",
                  "URL": null,
                  "raw_pages": "1434-7",
                  "medline_journal": "Science",
                  "ISO_journal": "Science",
                  "authors": [
                      "Song JJ",
                      "Smith SK",
                      "Hannon GJ",
                      "Joshua-Tor L."
                  ],
                  "DOI_URL": "http://dx.doi.org/10.1126/science.1102514"
              },
              "PUB00018283": {
                  "PMID": 11050429,
                  "ISBN": null,
                  "volume": "25",
                  "issue": "10",
                  "year": 2000,
                  "title": "Domains in gene silencing and cell differentiation proteins: the novel PAZ domain and redefinition of the Piwi domain.",
                  "URL": null,
                  "raw_pages": "481-2",
                  "medline_journal": "Trends Biochem Sci",
                  "ISO_journal": "Trends Biochem. Sci.",
                  "authors": [
                      "Cerutti L",
                      "Mian N",
                      "Bateman A."
                  ],
                  "DOI_URL": "http://dx.doi.org/10.1016/S0968-0004(00)01641-8"
              }
          },
          "set_info": {
              "accession": "CL0219",
              "name": "RNase_H"
          },
          "overlaps_with": null,
          "counters": {
              "subfamilies": 0,
              "domain_architectures": 602,
              "interactions": 0,
              "matches": 29456,
              "pathways": 0,
              "proteins": 28420,
              "proteomes": 2266,
              "sets": 1,
              "structural_models": {
                  "alphafold": 21504,
                  "rosettafold": 0
              },
              "structures": 112,
              "taxa": 9708
          },
          "entry_annotations": {
              "hmm": 0,
              "logo": 0,
              "alignment:uniprot": 22300,
              "alignment:full": 14038,
              "alignment:seed": 15
          },
          "cross_references": {}
      }
  }

Some Pfam families are removed or merged into others, in which case they become "dead" families. 
If you try to retrieve annotation information about a dead family, you'll get a simple JSON document that only tells you that there 
aren't any content associated to this entry.

.. If you try to retrieve annotation information about a dead family, you'll get a simple JSON document that only includes information on the replacement (if any) for the family: 

.. code-block:: bash

  GET /api/entry/pfam/PF06700

  HTTP 204 No Content
  Allow: GET, HEAD
  Content-Type: application/json
  InterPro-Version: 94.0
  InterPro-Version-Minor: 3
  Vary: Accept

  {
      "detail": "There is no data associated with the requested URL.\nList of endpoints: ['entry', 'pfam', 'PF06700']"
  }

Pfam-A family list
------------------

You can retrieve a list of all Pfam-A families in the latest Pfam release, either as an JSON document or as a tab-delimited text file. 
Both formats contain the Pfam-A accession, Pfam-A identifier and description:

- `/api/entry/all/pfam?format=json <https://www.ebi.ac.uk/interpro/api/entry/all/pfam/?format=json>`_
- `/api/entry/all/pfam?format=tsv <https://www.ebi.ac.uk/interpro/api/entry/all/pfam/?format=tsv>`_

You can also view the list in a web browser by removing the format=json parameter from the URL. 


.. code-block:: bash

  HTTP 200 OK
  Allow: GET, HEAD
  Content-Type: application/json
  InterPro-Version: 94.0
  InterPro-Version-Minor: 3
  Vary: Accept

  {
    "count": 19632,
    "next": "https://www.ebi.ac.uk/interpro/api/entry/all/pfam/?cursor=cD1QRjAwMDIw",
    "previous": null,
    "results": [
        {
            "metadata": {
                "accession": "PF00001",
                "name": "7 transmembrane receptor (rhodopsin family)",
                "source_database": "pfam",
                "type": "family",
                "integrated": "IPR000276",
                "member_databases": null,
                "go_terms": null
            }
        },
        ...

Protein data
------------

You can retrieve a sub-set of the data in a protein page as a JSON document using any of the following URL:
`/api/protein/uniprot/P00789 <https://www.ebi.ac.uk/interpro/api/protein/uniprot/P00789>`_


.. code-block:: bash

  HTTP 200 OK
  Allow: GET, HEAD
  Content-Type: application/json
  InterPro-Version: 94.0
  InterPro-Version-Minor: 3
  Vary: Accept

  {
    "metadata": {
        "accession": "P00789",
        "id": "CANX_CHICK",
        "source_organism": {
            "taxId": "9031",
            "scientificName": "Gallus gallus",
            "fullName": "Gallus gallus (Chicken)"
        },
        "name": "Calpain-1 catalytic subunit",
        "description": [
            "Calcium-regulated non-lysosomal thiol-protease which catalyze limited proteolysis of substrates involved in cytoskeletal remodeling and signal transduction"
        ],
        "length": 705,
        "sequence": "MMPFGGIAARLQRDRLRAEGVGEHNNAVKYLNQDYEALKQECIESGTLFRDPQFPAGPTALGFKELGPYSSKTRGVEWKRPSELVDDPQFIVGGATRTDICQGALGDCWLLAAIGSLTLNEELLHRVVPHGQSFQEDYAGIFHFQIWQFGEWVDVVVDDLLPTKDGELLFVHSAECTEFWSALLEKAYAKLNGCYESLSGGSTTEGFEDFTGGVAEMYDLKRAPRNMGHIIRKALERGSLLGCSIDITSAFDMEAVTFKKLVKGHAYSVTAFKDVNYRGQQEQLIRIRNPWGQVEWTGAWSDGSSEWDNIDPSDREELQLKMEDGEFWMSFRDFMREFSRLEICNLTPDALTKDELSRWHTQVFEGTWRRGSTAGGCRNNPATFWINPQFKIKLLEEDDDPGDDEVACSFLVALMQKHRRRERRVGGDMHTIGFAVYEVPEEAQGSQNVHLKKDFFLRNQSRARSETFINLREVSNQIRLPPGEYIVVPSTFEPHKEADFILRVFTEKQSDTAELDEEISADLADEEEITEDDIEDGFKNMFQQLAGEDMEISVFELKTILNRVIARHKDLKTDGFSLDSCRNMVNLMDKDGSARLGLVEFQILWNKIRSWLTIFRQYDLDKSGTMSSYEMRMALESAGFKLNNKLHQVVVARYADAETGVDFDNFVCCLVKLETMFRFFHSMDRDGTGTAVMNLAEWLLLTMCG",
        "proteome": "UP000000539",
        "gene": null,
        "go_terms": [
            {
                "identifier": "GO:0004198",
                "name": "calcium-dependent cysteine-type endopeptidase activity",
                "category": {
                    "code": "F",
                    "name": "molecular_function"
                }
            },
            {
                "identifier": "GO:0006508",
                "name": "proteolysis",
                "category": {
                    "code": "P",
                    "name": "biological_process"
                }
            },
            {
                "identifier": "GO:0005509",
                "name": "calcium ion binding",
                "category": {
                    "code": "F",
                    "name": "molecular_function"
                }
            }
        ],
        "protein_evidence": 1,
        "source_database": "reviewed",
        "is_fragment": false,
        "ida_accession": "664e4b66bad68bfc279e99cc8deefa39a1edf04a",
        "counters": {
            "domain_architectures": 10280,
            "entries": 30,
            "isoforms": 0,
            "proteomes": 1,
            "sets": 5,
            "structures": 0,
            "taxa": 1,
            "dbEntries": {
                "prosite": 2,
                "panther": 1,
                "prints": 1,
                "profile": 2,
                "smart": 2,
                "pfam": 2,
                "cathgene3d": 3,
                "cdd": 3,
                "ssf": 3,
                "interpro": 11
            },
            "proteome": 1,
            "taxonomy": 1,
            "similar_proteins": 10280
        }
    }
  }

Sending requests using a script
===============================

Most programming languages have the ability to send HTTP requests and receive HTTP responses. A Python script to retrieve 
data about a Pfam family might be as trivial as this:

.. code-block:: python

  #!/usr/bin/env python3

  # standard library modules
  import sys, errno, re, json, ssl
  from urllib import request
  from urllib.error import HTTPError
  from time import sleep

  BASE_URL = "https://www.ebi.ac.uk:443/interpro/api/entry/pfam/PF02171"
  
  def output_list():
    #disable SSL verification to avoid config issues
    context = ssl._create_unverified_context()
  
    next = BASE_URL
    last_page = False
  
    
    attempts = 0
    while next:
      try:
        req = request.Request(next, headers={"Accept": "application/json"})
        res = request.urlopen(req, context=context)
        # If the API times out due a long running query
        if res.status == 408:
          # wait just over a minute
          sleep(61)
          # then continue this loop with the same URL
          continue
        elif res.status == 204:
          #no data so leave loop
          break
        payload = json.loads(res.read().decode())
        next = payload["next"]
        attempts = 0
        if not next:
          last_page = True
      except HTTPError as e:
        if e.code == 408:
          sleep(61)
          continue
        else:
          # If there is a different HTTP error, it wil re-try 3 times before failing
          if attempts < 3:
            attempts += 1
            sleep(61)
            continue
          else:
            sys.stderr.write("LAST URL: " + next)
            raise e
  
      for i, item in enumerate(payload["results"]):
        sys.stdout.write(item["metadata"]["name"]["short"] + "\n")
      # Don't overload the server, give it time before asking for more
      if next:
        sleep(1)
  
  if __name__ == "__main__":
    output_list()
  

This script prints out the short name (Piwi) for the family (`PF02171 <https://www.ebi.ac.uk/interpro/entry/pfam/PF02171/>`_). 
