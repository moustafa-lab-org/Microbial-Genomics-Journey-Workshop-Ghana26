# MGJW Problem Set 6

## Part 1
### Download needed files
* To follow the steps here, you need to download this file using `wget -O problem_set6.tar.gz "https://www.dropbox.com/scl/fi/7lkh22v67qixd5mu67nag/problem_set6.tar.gz?rlkey=i7zbjnookvnptqqljalosmzcc&st=qawfs649&dl=1"`
* Make sure the file is inside MGJW `mv problem_set6.tar.gz /data/MGJW` if not there.
* `mkdir problem_set6`
* Unarchive the file `tar -xf problem_set6.tar.gz -C ./problem_set6`

### Snippy
Let's produce a core snp alignment for multiple Staphylococcus aureus genomes. These genomes are from the North American and South American parallel epidemics of USA300. We will need to use [Snippy](https://github.com/tseemann/snippy) which finds SNPs between a reference genome and your NGS sequence reads or assembled genomes. We will use `V2200_PEB.fna.gz` as a reference. To simplify running the 4 isolate sequences (contigs) against the same reference, we can use the [snippy-multi](https://github.com/tseemann/snippy#using-snippy-multi). This script requires a tab separated input file as follows, and can handle paired-end reads, single-end reads, and assembled contigs. We will a homemade script `snippy_convert_list_input_tab.py` to produce the tab-separated file that `snippy-multi` needs.

```
cd /data/MGJW/problem_set6/genomes
ls > ../files_list.txt
cd ..
chmod +x snippy_convert_list_input_tab.py
./snippy_convert_list_input_tab.py files_list.txt snippy_tab_list.txt
snippy-multi snippy_tab_list.txt --ref V2200_PEB.fna > runme.sh
chmod +x runme.sh
./runme.sh
```

## Part 2 for Session 7 Readiness
* [Roary](https://github.com/sanger-pathogens/Roary)
```
roary -h
```
