# Contigtree
A Python script for extracting & assembling selected segments of a Minia contig tree.

The [Minia _de-novo_ assembler](https://github.com/GATB/minia) produces a FASTA file of contigs where each contig's header line indicates which contigs are adjacent on the 5' and 3' ends.

This tool provides an easy way to isolate a section of the graph around a specific target (or targets) without needing to convert the file to a GFA. 

Usage: `python3 contigtree.py <contigs.fa> <depth> <targets>`

A suitable depth is 2-4. The contig sequences are printed to stdout in FASTA format while the tree is printed to stderr. Contigtree uses python3 core modules only and mmaps the `contigs.fa` file from disk to minimize RAM usage.

Example:
```
$ python3 ~/contigtree/contigtree.py minia.contigs.fa 4 963205 
===================== Tree forwards from 963205 to depth 4 =====================
|->963205
          |->273719
                    |->5513749
                              |->1163354(r)
                                        |->10050961
                                        |->10472585
          |->7751509(r)
                    |->1328540(r)
                              |->2098886(r)
                                        |->6629975(r)
                              |->7219254(r)
                                        |->3776338(r)
===================== Tree reverse from 963205 to depth 4 ======================
|->963205(r)
          |->6629975
                    |->963339(r)
                              |->6629975
                                        |->963339(r)
                                        |->2098886
                    |->2098886
                              |->1328540
                                        |->7751509
                                        |->8441592

============================== Unique contigs: 17 ==============================
>963205_len_3680
TCATTTTATGTTTCAGGTTCAGGGGGAGGTGTGGGAGGTTTTTTAAAGCAAGTAAAACCTCTACAAATGTGGTATGGCTG
ATTATGATCCTCTAGATCAGATCTGCGAAGATACGGCCACGGGTGCTCTTGATCCTGTGGCT...
```
An (r) next to the contig name indicates it is in reverse-complement orientation.
