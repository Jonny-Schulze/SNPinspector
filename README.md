# UNDER CONSTRUCTION

# SNPdetector
This Python modul is based on [PySanger by ponnhide](https://github.com/ponnhide/PySanger).
The modul was adapted to allow calling of an ambigous base ("N") on positions with more than one trace signal.

It therefore allows for high throughput analysis of sanger sequencing files (.ab1) for Single Nucleotide Polymorphisms (SNPs) by parallel visual insepction of target loci.

## Intendet Usage
SNPinspector iterates over a list referencing the .ab1 files and extracts the data for the query sequence. The target loci (relative to the query sequence) can be highlighted. The process is strand sensitive.
Combine_plots allows to iterate over the same list to create a single .pdf file with all created single plots from SNPinspector.
