Log onto Discovery and cd to your “scratch” account:

> cd /scratch/`<username>`

Download the NCBI command line tools (datasets and dataformat)

> curl -o datasets `https://ftp.ncbi.nlm.nih.gov/pub/datasets/command-line/v2/linux-amd64/datasets`

Then:

> curl -o dataformat `https://ftp.ncbi.nlm.nih.gov/pub/datasets/command-line/v2/linux-amd64/dataformat`

Make them executable: 

> chmod +x datasets dataformat

Use the ls command to check that they are there (should see “datasets” and “dataformat” in the directory).

Now you can download your genome using the accession number for your group’s genome (for example, GCF000002985.6) by entering:

> ./datasets download genome accession <accessionnumber>

After the download, use ls to see that an NCBI zip file is now in the directory. Unzip it by entering:

> unzip ncbi_dataset.zip

You’ll see some files being “inflated”. When the command prompt returns, use the ls command again and you should see a directory ‘ncbi_dataset’ that contains the unzipped files.
