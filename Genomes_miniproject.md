# Working with genome sequences

### Know your sequences

When you think about sequence data, you'll want to ask yourself:
Which species are the sequences from?
Is this GENOMIC DNA (gDNA), representing all parts of the genome? 
Or is this data from mRNA (cDNA), representing parts of the genome that are being expressed under some condition?

Genomic DNA sequences could be reads that have not yet been assembled into a complete genome, OR they could be reads from individuals from a species whose genome has already been assembled, but with the goal of identifying variation in the population ("resequencing").

Always make sure you're clear on what the sequences you are working with represent.

In this exercise you'll download genome sequences from several species:
* _B burgdorferei_ (Lyme disease bacterium)
* _C elegans_ (lab worm)
* _Parastichopus parvimensis_ (sea cucumber - you already have this one!)

You'll also download a couple of tools from NCBI that allow you to readily download a variety of genomes, genes, and other genomic information.


I.  Create a directory on Discovery for genomic data, with a README file for each genome:

Create a file called README.txt that contains basic information on each genome you add to the directory, including:
*	Size of genome
*	Structure (such as, linear or circular, how many chromosomes, how many plasmids)
*	Estimated number of protein-coding genes
*	Where to access the genome sequence
* At what coverage it was sequenced

Here are the accession numbers for the genome sequences you should use:

B. burgdorferei: GCA_000008685.2_ASM868v2
C. elegans: GCF_000002985.6 


II.  Download the **ncbi_datasets** tools. These are handy for downloading lots of genome data. Log onto Discovery and cd to your “scratch” account:

`cd /scratch/<username>`

Request a computing node.

Download the NCBI command line tools (datasets and dataformat)

`curl -o datasets https://ftp.ncbi.nlm.nih.gov/pub/datasets/command-line/v2/linux-amd64/datasets`

Then:

`curl -o dataformat https://ftp.ncbi.nlm.nih.gov/pub/datasets/command-line/v2/linux-amd64/dataformat`

Make them executable: 

`chmod +x datasets dataformat`

***Use the `ls` command to check that they are there (should see “datasets” and “dataformat” in the directory).***
  

III.  Download the genome sequences to your scratch account, using good practices for how you store the files (in other words, set up folders and subfolders that have a logical structure). 

For downloading genomes you'll want to use the accession number for each genome (for example, GCF000002985.6) by entering:

`./datasets download genome accession <accession-number>`

After the download, use `ls` to see that an NCBI zip file is now in the directory. Unzip it by entering:

`unzip ncbi_dataset.zip`

You’ll see some files being “inflated”. When the command prompt returns, use the `ls` command again and you should see a directory ‘ncbi_dataset’ that contains the unzipped files.

***
When you use ls to see what’s in a “room”, add the -l (lowercase L) flag so that you can distinguish between files and directories. For example, below is what I see as I travel down the subdirectories within my “borrelia_dataset”. I used ls until I got down to what looked like the sequence file (GCF_000008685.2) then I used ls -l and found out it is actually another directory:
[jhenzy@login-00 borrelia_dataset]$ ls
data_bor
[jhenzy@login-00 borrelia_dataset]$ cd data_bor/
[jhenzy@login-00 data_bor]$ ls
assembly_data_report.jsonl  dataset_catalog.json  GCF_000008685.2
[jhenzy@login-00 data_bor]$ ls -l
total 4
-rw------- 1 jhenzy users 2855 Jan 27 13:34 assembly_data_report.jsonl
-rw------- 1 jhenzy users  339 Jan 27 13:34 dataset_catalog.json
drwxr-xr-x 2 jhenzy users 4096 Jan 28 17:55 GCF_000008685.2
[jhenzy@login-00 data_bor]$

This makes it clear that GCF_000008685.2 is a directory and NOT the sequence file. To get to the sequence file, I’ll need to change into that directory:
[jhenzy@login-00 data_cel]$ cd GCF_000002985.6/
[jhenzy@login-00 GCF_000002985.6]$ ls -l
total 99161
-rw------- 1 jhenzy users 101540352 Jan 26 12:13 GCF_000002985.6_WBcel235_genomic.fna

Within the GCF_000008685.2 directory, I see the actual sequence file, GCF_000002985.6_WBcel235_genomic.fna		
***

IV.  Analysis
To analyze the genome sequences, you'll use two programs that are available as modules on Discovery: seqtk and emboss.

You need to **load** the modules into your workspace (scratch) to use them.

`module load emboss`

`module load seqtk`

To see which modules are loaded into your current session:
`module list`

You should see emboss and seqtk among those shown.

When you download your organism's genome sequence, multiple fasta sequences are usually included in one file. You can use the emboss command 'infoseq' to see what a file contains:

infoseq <filename>

One item on your deliverables list is to generate the reverse complement of a genomic sequence from your organism. First you'll need to extract just one fasta sequence from the whole batch. You can use a seqtk command to extract a sequence. First you need to put the sequence identifier (usually the accession number) into a file. You can do this quickly using echo. 

echo '<identifier>'  >  <make-up-a-filename>

For example, it might look like this:

echo 'NC_008524.2' > list.txt

This will create a file called list.txt that contains just one line: NC_008524.2.

Then use the command that tells seqtk to extract that sequence from the larger file and store it in a new file by itself:

seqtk subseq <file-with-many-sequences> list.txt > NC_008524.2.txt

Now we can generate the reverse complement of this sequence, putting it into a new file:

revseq NC_008524.2.txt NC_008524.2.rev

***Remember to keep using tab-complete, and check after commands that the new file is added to your directory by using ls. ***

