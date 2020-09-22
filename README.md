############################
Pfam documentation for users
############################

|docs|

This repository is the source of Pfam documentation hosted on Read The Docs.

Installation
************

.. code-block:: bash

  # download a copy of the document repository
  git clone https://github.com/ProteinsWebTeam/pfam-docs.git
  cd pfam-docs
  # set-up python project dependancies
  python3 -m venv venv
  source ./venv/bin/activate
  pip install -r requirements.txt
  # build the docs (this will have to be repeated on every edit)
  sphinx-build docs build
  # or for a dynamic auto reloading
  sphinx-autobuild docs build
  # view documentation at
  http://localhost:8000/

Contact
*******

If you have any questions or feedback, email us at pfam-help@ebi.ac.uk.
