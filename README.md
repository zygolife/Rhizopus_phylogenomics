Rhizopus phylogenomics
====
Resolving Rhizopus and Mucor phylogenies from whole genome data

Steps
======


1. ```ln -s Phylogenomics_HMMs/HMM ./```
2. ```cd pep; ls *.fasta > ../list; cd ..; ````
3. ```ln -s Phylogenomics/scripts Phylogenomics/jobs .```
4. ```sbatch --array=1-37 jobs/01_hmmsearch.sh``` or 
  * something like this to run in serial ```for n in `seq 1 1 37`; do bash jobs/01_hmmsearch.sh; done```
5. ```sbatch jobs/02_makebesthits.sh``` # will find top hit for each HMM from the protein HMMSEARCHes
6. ```sbatch jobs/03_makeunaln.sh``` # will stage unaligned CDS and AA files in search/$MARKERNAME
