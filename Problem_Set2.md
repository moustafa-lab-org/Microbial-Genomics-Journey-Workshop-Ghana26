# MGJW Problem Set 2

## Part 1
### Install miniconda
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash ./Miniconda3-latest-Linux-x86_64.sh
source .bashrc
```
* Follow instructions after the bash command and keep confirming and accepting.<br/>
* You can then use the source command to activate conda in your current session or close and reopen the app.<br/>
* [Bioconda](https://bioconda.github.io/) lets you install thousands of software packages related to biomedical research using the conda package manager.
* You will need a one-time set up to set up the channels for bioconda.
```
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
conda config --set channel_priority strict
```
**Now you are ready to install new tools. It is highly recommended to create a new environement for each tool separetely. Why do you think we need new env?**
* Let's install abricate
```
conda create -n abricate -c conda-forge -c bioconda -c defaults abricate
conda activate abricate
abricate --check
```
* Try this command to list all environments installed on your computer (conda info --envs)
* Let's try using FASTQC, you need to activate its environment first (Did you install??). You will use files from the folder that you downloaded for Problem Set 1.
```
conda activate fastqc
cd MGJW/problem_set1/fastq
gunzip *.gz
fastqc genome1_R1.fastq genome1_R2.fastq
```
Let's explore the html file. Windows User may need to copy the file to another directory so they can open the html file in a browser.
`cp /home/Ubuntu_user_name/MGJW/problem_set1/fastq/file.html /mnt/c/Users/Windows_username/Desktop/`
You will notice that the number of reads is really low. Some of our samples may fail quite a few quality metrics used by FastQC. However, this does not mean that our samples should be discarded as this may or may not be a problem for your downstream application.
* Let's check the mockdna sample in the fastq folder from problem set 1. Mash can handle one file for the sample so we will have to concatenate our reads.
```
conda activate mash
cd ~/MGJW/problem_set1/fastq
cat mockdna_R1.fastq mockdna_R2.fastq > mockdna_reads.fastq
gunzip ../RefSeqSketches.msh.gz
mash screen -w -p 8 ../RefSeqSketches.msh mockdna_reads.fastq > mockdna_screen_winning.tab
less mockdna_screen_winning.tab
sort -gr mockdna_screen_winning.tab > mockdna_screen_winning_sorted.tab
less mockdna_screen_winning_sorted.tab
```
* Let's check another sample from problem set 1 and see how this compares to previous results.
```
cd ~/MGJW/problem_set1/fasta
mash screen -w -p 8 ../RefSeqSketches.msh genome2.fasta > genome2_screen_winning.tab
sort -gr genome2_screen_winning.tab > genome2_screen_winning_sorted.tab
less genome2_screen_winning_sorted.tab
```

## Part 2
* `cd ~/MGJW/problem_set1/fasta`
* try `mash dist genome3.fasta genome4.fasta`
* Let's make our own mash database using `mash paste` for the three genomes in the fasta directory (`MGJW/problem_set1/fasta`)
  * `mash sketch -s 1000 -k 21 genome2.fasta`
  * `mash sketch -s 1000 -k 21 genome3.fasta`
  * `mash sketch -s 1000 -k 21 genome4.fasta`
  * `mash paste genomes.msh genome2.fasta.msh genome3.fasta.msh  genome4.fasta.msh`
  * `mash info genomes.msh | head -n 20`
* Save your history of commands in a file called commands_notes_PS2.txt
