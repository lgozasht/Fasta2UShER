# ARTIC-2-UShER

Converts standard multiple sequence alignment output from the SARS-CoV-2 ARTIC Network protocol (see https://artic.network/ncov-2019) into a merged VCF viable for input to UShER (Ultrafast Sample Placement on Existing Trees). ARTIC-2-UShER also considers missing data in SARS-CoV-2 genomic sequences and filters variants at problematic sites (see https://virological.org/t/issues-with-sars-cov-2-sequencing-data/473/12 and https://www.biorxiv.org/content/biorxiv/early/2020/06/09/2020.06.08.141127.full.pdf). 

### Input

ARTIC Network multiple sequence alignment output file(s)

### Options

**-inpath**: Path to directory containing ONLY multiple sequence alignment files in fasta format (make sure no other files exist in this directory).

**-outfile**: Output VCF file name

### Output

Merged VCF without problematic sites and with missing data for a particular sample denoted as "." in the corresponding genotype column.

For example:
Three files (containing sample1, sample2 and sample3) served as input to ARTIC-2-UShER.py. For a given site 68, if sample1 matched the reference, sample2 possessed the alternate allele, and sample3 possessed missing data ("N"), the corresponding line in the output vcf would read as follows:

#CHROM    POS     ID	    REF     ALT     QUAL    FILTER    INFO    FORMAT    Sample1    Sample2    Sample3

MN908947.3	68	   .	     A	     T	     .	      .	      AC=1      GT	       0	        1          .