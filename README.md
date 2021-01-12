
# FindVir : a procedure to detect virulence genes in bacterial strains

Briefly, virulence genes were detected by blasting reference sequences (virulence genes) against a NCBI Blast+ protein database containing CDS from genomes of all strains (244) included in DPL paper.

## Installation

git clone https://gccode.ssc-spc.gc.ca/ac_/dpl/gene_detection/virulence_gene_detection.git

conda env create -f ./conda/jupyter_biopython.yml


## Preparation of a database of CDS from all strains

Extraction of the CDS and header naming was done with BioPython (see the Jupyter Notebook)

Preparation of the MS_strains database was done with UNIX and NCBI Blast+ commands.

```shell
# Concatenate all CDS fasta files
cat database/*.fasta > MS_strains.fasta

# Prepare a NCBI Blast+ protein database
makeblastdb -in MS_strains.fasta -input_type fasta -dbtype prot -title MS_strains -out MS_strains
```

## Parsing of the xml blastp outputs

Parsing of the blastp outputs and identification of the strains that contains specific virulence genes has been done with BioPython and is documented in the Jupyter Notebook.


## Detection of enterohaemolysin (ehxA) and porcine attaching and effacing-associated protein (paa)

To detect enterohaemolysin (*ehxA*) and porcine attaching and effacing-associated protein (paa), the NCBI Reference sequence WP_011310119 and GenBank sequence U82533.4 were used respectively.


## Detection of *bfp* genes

CDS from bfp genes encoded on Escherichia coli B171 plasmid pB171 described under the Genbank Accession number AB024946 ( Abraham et al. Year) were used as distinct queries to screen for the *bfp* genes.

## Detection of *eae* sequences

The 143 complete eae sequences referenced in Xiong et al. 2016  were clustered with CD-HIT in divergent sequences showing no more than 90% of similarity

```shell
cd-hit -i intimin.pep -o intimin90 
```

The resulting 11 divergent sequences were used as queries to detect intimin genes.


## Remote repositories

Exact copies of this project exist at two locations :

old-origin	https://github.com/soda460/FindVir.git (fetch)
old-origin	https://github.com/soda460/FindVir.git (push)
origin	https://gccode.ssc-spc.gc.ca/ac_/dpl/gene_detection/virulence_gene_detection.git (fetch)
origin	https://gccode.ssc-spc.gc.ca/ac_/dpl/gene_detection/virulence_gene_detection.git (push)


## Contributors

  * Jean-Simon Brouard, Ph.D.  
Biologist in bioinformatics, Science and Technology Branch  
Agriculture and Agri-Food Canada / Government of Canada  
jean-simon.brouard@canada.ca


  * Dominic Poulin-Laprade, Ph.D.  
Research Scientist, Science and Technology Branch  
Agriculture and Agri-Food Canada / Government of Canada  
Dominic.Poulin-Laprade@Canada.ca



