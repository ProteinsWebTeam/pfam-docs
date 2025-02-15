********
FTP Site
********

The Pfam `FTP site <http://ftp.ebi.ac.uk/pub/databases/Pfam>`_ is organised into the following structure: 

- :ref:`antifam`
- :ref:`rosettafold`
- :ref:`tools`
- :ref:`current_release`
- :ref:`mappings`
- :ref:`papers`
- :ref:`releases`

The most important directory is probably the :ref:`current_release` directory. It contains the flat-files for the current release.

.. _antifam:

AntiFam
=======
The **AntiFam** directory contains the different releases of the 
`AntiFam database <https://www.ebi.ac.uk/research/bateman/software/antifam-tool-identify-spurious-proteins>`_, identifying spurious proteins.

.. _rosettafold:

RoseTTAfold_aln
===============
The **RoseTTAfold_aln** directory contains the alignments used by RoseTTAfold to predict their structural models using Pfam.

.. _tools:

Tools
=====
The **Tools** directory contains code for running *pfam_scan.pl*. 

The README file in this directory contains detailed information on 
how to install and run the script. Note that we have gone for a modular design for the script, enabling the functionally on the script 
to be easily incorporated into other Perl scripts. The *ChangeLog* file lists the versions and changes to the current version of 
*pfam_scan.pl* (and modules). 

There is also an archived version of *pfam_scan.pl* that works with HMMER2. This is no longer supported. 

There is also Perl code for predicting active sites found in the ActSitePred directory, the functionality of which has been rolled 
into the latest version of *pfam_scan.pl*.

.. _current_release:

current_release
===============
This directory contains the flat-files for the current release. Some of these files may be very large (of the order of several hundred megabytes). 
Please check the sizes on the FTP site before trying to download them over a slow connection. 
The files, most of which are compressed using gzip, are:

`Pfam-A.clans.tsv.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.clans.tsv.gz>`_
    A tab separated file containing Pfam-A family and clan information for all Pfam-A families 
`Pfam-A.dead.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.dead.gz>`_
    Listing of families that have been deleted from the database 
`Pfam-A.fasta.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.fasta.gz>`_
    A 90% non-redundant set of fasta formatted sequence for each Pfam-A family. The sequences are only the regions hit by the 
    model and not full length protein sequences. 
`Pfam-A.full.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.full.gz>`_
    The full alignments of the curated families, searched against pfamseq/UniProtKB reference proteomes (prior to Pfam 29.0, 
    this file contained matches against the whole of UniProtKB). 
`Pfam-A.full.uniprot.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.full.uniprot.gz>`_
    The full alignments of the curated families, searched against UniProtKB. 
`Pfam-A.hmm.dat.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.hmm.dat.gz>`_
    A data file that contains information about each Pfam-A family 
`Pfam-A.hmm.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.hmm.gz>`_
    The Pfam HMM library for Pfam-A families 
`Pfam-A.regions.tsv.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.regions.tsv.gz>`_
    A tab separated file containing UniProtKB reference proteome sequences and Pfam-A family information 
`Pfam-A.regions.uniprot.tsv.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.regions.uniprot.tsv.gz>`_
   A tab separated file containing UniProtKB sequences and Pfam-A family information
`Pfam-A.seed.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-A.seed.gz>`_
    The SEED alignments of the curated families.
    Please note that from Pfam 36.0 onwards we do not process PDB data. Hence secondary structure annotations aren't available in the SEED alignments anymore. However, `PDBe provides mappings to Pfam <https://ftp.ebi.ac.uk/pub/databases/msd/sifts/flatfiles/tsv/pdb_pfam_mapping.tsv.gz>`_ which might be of interest. 
`Pfam-C.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/Pfam-C.gz>`_
    A file that contains the information about clans and the Pfam-A membership 
`active_site.dat.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/active_site.dat.gz>`_
    Tar-ball of data required for the predictions of active sites by Pfam scan. 
`database_files <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/database_files>`_
    Directory contains two files per table from the MySQL database. The .sql.gz file contains the table structure, the .txt.gz 
    files contains the content of the table as a tab delimited file with field enclosed by a single quote ('). 
`diff.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/diff.gz>`_
    Stores the change status of entries between this release and last. 
`md5_checksums <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/md5_checksums>`_
    A file containing the MD5 checksum for each release file
`pdbmap.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/pdbmap.gz>`_
    Mapping between PDB structures and Pfam domains. 
`pfamseq.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/pfamseq.gz>`_
    A fasta version of Pfam's underlying sequence database 
`relnotes.txt <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/relnotes.txt>`_
    Release notes 
`swisspfam.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/swisspfam.gz>`_
    ASCII representation of the domain structure of UniProt proteins according to Pfam 
`uniprot_sprot.dat.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/uniprot_sprot.dat.gz>`_
    Data files from UniProt containing SwissProt annotations. 
`uniprot_trembl.dat.gz <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/uniprot_trembl.dat.gz>`_
    Data files from UniProt containing TrEMBL annotations. 
`userman.txt <https://ftp.ebi.ac.uk/pub/databases/Pfam/current_release/userman.txt>`_
    File containing information about the flatfile format 

.. _mappings:

mappings
========
The **mapping** directory contains the mapping between PDB structures and Pfam entries.

.. _papers:

papers
======
The **papers** directory contains each NAR database issue article describing Pfam. For a detailed description of the latest changes 
to Pfam, please consult (and cite) these papers.

.. _releases:

releases
========
The **releases** directory contains all the flat files and database dumps (where appropriate) for all version of Pfam to-date. 
The files in more recent releases are the same as described for the current release, but in older releases the contents do change.
