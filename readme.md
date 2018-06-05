# Contigtree
A Python script for extracting & assembling selected segments of a Minia contig tree.

The [Minia _de-novo_ assembler](https://github.com/GATB/minia) produces a FASTA file of contigs where each contig's header line indicates which contigs are adjacent on the 5' and 3' ends.

This tool provides an easy way to isolate a section of the graph around a specific target (or targets) without needing to convert the file to a GFA. 

Usage: `python3 contigtree.py <contigs.fa> <depth> <targets>`

A suitable depth is 2-4. The contig sequences are printed to stdout in FASTA format while the tree is printed to stderr. Contigtree uses python3 core modules only and mmaps the `contigs.fa` file from disk to minimize RAM usage.