.. _evol-filter:

*******************************************************************************
evol filter
*******************************************************************************

Usage
===============================================================================

Running :command:`evol filter -h` displays::

  usage: evol filter [-h] [--quiet] [--examples] (-s | -e | -c) [-F] [-o STR]
                     [-f STR] [-z]
                     msa word [word ...]
  
  positional arguments:
    msa                   MSA filename to be filtered
    word                  word to be compared to sequence label
  
  optional arguments:
    -h, --help            show this help message and exit
    --quiet               suppress info messages to stderr
    --examples            show usage examples and exit
  
  filtering method (required):
    -s, --startswith      sequence label starts with given words
    -e, --endswith        sequence label ends with given words
    -c, --contains        sequence label contains with given words
  
  filter option:
    -F, --full-label      compare full label with word(s)
  
  output options:
    -o STR, --outname STR
                          output filename, default is msa filename with _refined
                          suffix
    -f STR, --format STR  output MSA file format, default is same as input
    -z, --compressed      gzip refined MSA output

Examples
===============================================================================

Running :command:`evol filter --examples` displays::

  Sequence coevolution analysis involves several steps that including
  retrieving data and refining it for calculations.  These steps are
  illustrated below for RnaseA protein family.
  
  Search Pfam database:
  
    $  evol search 2w5i
  
  Download Pfam MSA file:
  
    $  evol fetch RnaseA
  
  Refine MSA file:
  
    $ evol refine RnaseA_full.slx -l RNAS1_BOVIN --seqid 0.98 --rowocc 0.8
  
  Checking occupancy:
  
    $ evol occupancy RnaseA_full.slx -l RNAS1_BOVIN -o col -S
  
  Conservation analysis:
  
    $ evol conserv RnaseA_full_refined.slx
  
  Coevolution analysis:
  
    $ evol coevol RnaseA_full_refined.slx -S -c apc
  
  Rank order analysis:
  
    $ evol rankorder RnaseA_full_refined_mutinfo_corr_apc.txt -p 2w5i_1-121.pdb --seq-sep 3
  
