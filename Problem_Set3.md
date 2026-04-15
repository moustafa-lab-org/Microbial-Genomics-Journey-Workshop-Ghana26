# MGJW Problem Set 3

## Note for file extensions (multiple possible extensions, but same file)
FASTA file Extensions: .fasta, .fna, .fa<br/>
FASTQ file Extensions: .fastq, .fq

## Part 1
**In my instructions, I do not necessarily instruct you to change directory to MGJW or any other one, use the skills you learnt in the Unix command session to do that. Also, I may not instruct to activate the conda env in some cases.**

### skesa

**You can skip this download step if you already donwloaded it for session 3.**<br/>
Let's assemble a genome. To follow the steps here, you need to download the files available [here](https://www.dropbox.com/scl/fo/8ni4qic39mb3ojapgci1x/h?dl=0&rlkey=p6gyncbcees8754go5s8votvu).
```
conda activate shovill
shovill --trim --assembler skesa --outdir out_S56 --R1 S56_R1.fastq --R2 S56_R2.fastq
conda activate mash
mash screen -w -p 8 ../../problem_set1/RefSeqSketches.msh contigs.fa > S56_screen_winning_contigs.tab
sort -gr S56_screen_winning_contigs.tab > S56_screen_winning_contigs_sorted.tab
less S56_screen_winning_contigs_sorted.tab | head -n 10
```
You will see that this assembled genome is very fragmented (around 3000 contigs). From Mash, you will be able to see that this genome is P. aeruginosa.

## Part 2

## checkm
* Let's try checkm! Go to NCBI and download the reference genome file for Pseudomonas aeruginosa (PAO1).

>Optionally, you can download the reference genome for P. aeruginosa (PAO1) right from the command line using ncbi-datasets. If you haven't previously installed ncbi-datasets, you can install it in a fresh environment using the following commands:
```
conda create --name ncbi-datasets
conda activate ncbi-datasets
conda install -c conda-forge ncbi-datasets-cli
```
To download the PAO1 reference genome, you can run this command:
```
datasets download genome taxon 'Pseudomonas aeruginosa' --reference
```
Once downloaded, unzip the file and retrieve the genome. Now you can proceed with using checkm! Think about the command 

* What is the L50 and L90 for genome4.fasta from problem_set1?

## busco
[Busco by Erin Theiller](BUSCO.md)

Let's assess contamination in some genome assemblies using single-copy orthologs! Notice on the same genome, we can check different taxonomical levels (bacteria_odb10, clostridiales_odb10, pseudomonadales_odb10).
```
conda activate busco
busco -i ~/MGJW/problem_set3/out_S56/contigs.fa -l bacteria_odb10 -o busco_op -m genome
busco -i ~/MGJW/problem_set1/fasta/genome4.fasta -l bacteria_odb10 -o busco_op2 -m genome
busco -i ~/MGJW/problem_set1/fasta/genome4.fasta -l clostridiales_odb10 -o busco_op3 -m genome
busco -i ~/MGJW/problem_set3/out_S56/contigs.fa -l pseudomonadales_odb10 -o busco_op4 -m genome
```
* What do you think of genome4.fasta vs contigs.fa?
* Which genome has better metrics?
* Why do you think this genome assembly is better?


## Reproducibility
[Reproducibility by Daniel P. Morreale](Reproducability.md)
