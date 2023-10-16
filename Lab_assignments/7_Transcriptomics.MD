### Transcriptome assembly

Today we will be doing a *de novo* transcriptome assembly. Similar to the other week, we are going to compare a couple of different metrics!

Background information: You suddenly found yourself as a newt (you got better), and you want to assemble your transcriptome! This seems like a totally fine thing to do, and there isn't any sort of ethical issues with assembling your own genomic data. 

Usually, you will get quite a bit of sequence data in order to do any transcriptomic type project (often hundreds of millions of reads). For the purposes of this lab, I've downloaded data from this paper by Glass et al. (https://www.biorxiv.org/content/10.1101/653238v1.abstract) and randomly subsampled down to a dataset that we can work with for the confines of our lab time. To do this I used the `seqtk sample` command. `seqtk` is an extraordinarily useful series of scripts for those of us working with genomic data. I can't recommend it enough.


For lab today we will be taking two different approaches to transcriptome assembly. In both we will be removing sequencing adaptors, error correcting reads, and then assembling a transcriptome. One will use a pretty common transcriptome assembler, Trinity (website: https://github.com/trinityrnaseq/trinityrnaseq/wiki). For the other assembly, we will use the SPAdes. This lab has a number of steps, and uses quite a few software packages.

## Software install

Tip: Make separate environments for different assemblers.

First, install Trinity via conda:

```bash
conda install -c bioconda trinity
```

Second, install SPAdes. Do you still have your spades installed from the other week> Great, then you are done.

Third, install compleasm. Oh good, you are already done since you installed it the other week.

Lastly, install Transrate.

```bash
conda install -c bioconda transrate
```


Now we will download our newt data!

```bash
mkdir newt
cd newt
wget https://raw.githubusercontent.com/AdamStuckert/Gen711/master/Lab/Files/Taricha_granulosa_subsampled.1.fq
wget https://raw.githubusercontent.com/AdamStuckert/Gen711/master/Lab/Files/Taricha_granulosa_subsampled.2.fq
```

Verify that you have both datasets and that they are approximately the same size with `ls -lht`. Next, I'd like you to count the total number of reads for both the forward and reverse datasets. 

**Question 1:** how many reads are in each dataset, and what command did you use to count them? Hint: you can use the format of fastq files to your advantage here. Hint #2: We have not talked about `regular expression` yet, but it is a very powerful way to manipulate data for your purposes. The `^` symbol refers to the start of a line, so you can combine that with some search term to find the answer you want (specify it in quotes like this `"^"` with whatever search string you are using inside those same quotes.

Back to the regularly scheduled lab. First we will run Trimmomatic to trim off adaptor sequences.

```bash
trimmomatic PE -threads 5 -baseout Taricha_granulosa_subsampled.TRIM.fastq Taricha_granulosa_subsampled.1.fq Taricha_granulosa_subsampled.2.fq LEADING:3 TRAILING:3 ILLUMINACLIP:${MAKEDIR}/barcodes/barcodes.fa:2:30:10:8:TRUE MINLEN:25
```

Finally, we will run Trinity to assemble our transcriptome! Trinity runs in 3 parts (inchworm, chrysalis, butterfly), and will take a little bit of time to run.

```bash
Trinity --SS_lib_type RF --no_version_check --bypass_java_version_check --no_normalize_reads --seqType fq --output trinity/ --max_memory 15G --left Taricha_granulosa_subsampled.TRIM_1P.fastq  --right Taricha_granulosa_subsampled.TRIM_2P.fastq  --CPU 5 --inchworm_cpu 5 --full_cleanup
```

Good work! You've now assembled your first transcriptome! Lets take a look at the assembly quality using the two programs we talked about in class: Transrate and BUSCO. First we will use Transrate.  

**Question 2:** What does Transrate tell us about our transcriptome?

```bash
transrate -o transrate -a trinity.Trinity.fasta --left Taricha_granulosa_subsampled.TRIM_1P.fastq  --right Taricha_granulosa_subsampled.TRIM_2P.fastq -t 9
```

**Question 3:** What is the assembly score and the optimal assembly score for this transcriptome? You might have to kick around in the output files to find the answer you want! 
 
Now, we will look at BUSCO scores. **Question 4:** Why do we use BUSCO and what does it tell us about our transcriptome?


First we need to download a BUSCO database and decompress it.

```bash
wget http://busco.ezlab.org/v2/datasets/metazoa_odb9.tar.gz
tar -xzvf metazoa_odb9.tar.gz
```

Next we run BUSCO, pointing it to the metazoa lineage dataset that we just downloaded and decompressed.

```bash
run_BUSCO.py --lineage metazoa_odb9 -i trinity.Trinity.fasta -m transcriptome --cpu 9 -o busco_trinity 
```

When we run BUSCO we point it to a lineage dataset. This lineage dataset should generally be as taxa specific as possible. There are some exceptions to this, such as if you are doing work that crosses the BUSCO taxa groups (e.g., if you are comparing transcriptomes across all Metazoa it would be inappropriate to run BUSCO using the tetrapoda lineage dataset for a dog and the aves lineage dataset for a chicken). To reduce the overall time for lab, we will use the Metazoa lineage dataset, which has many fewer shared single copy genes than the more specific Tetrapoda (which we would otherwise use with a newt).

You've now run BUSCO on your assembled transcriptome. **Question 5:** What is the proportion of each of the following in your assembly?
	1. Complete, single copy genes
	2. Complete, duplicated genes
	3. Fragmented genes
	4. Missing genes


Next, we will move on to another approach to transcriptome assembly using SPAdes. 


```
$HOME/Oyster_River_Protocol/oyster.mk \
STRAND=RF \
MEM=15 \
CPU=9 \   
READ1=Taricha_granulosa_subsampled.1.fq \
READ2=Taricha_granulosa_subsampled.2.fq \
RUNOUT=newt
```

Ok, so jetstream is interpreting these all as separate lines. So to make your life easier, you can just paste this into a text editor (NOT Word!!) and then make it a single line. Paste that in. Or just type it all! It will give you the full life experience :)

**Question 6:** how do the BUSCO scores compare between the assemblies?

**Question 7:** how do the transrate scores compare between the assemblies?

**Question 8:** Given this information, which assembly do you think is better and why?

**Question 9:** What is different about these two approaches to transcriptome assembly? You may need to look at the ORP code to figure this out!
