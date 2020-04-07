# viroseqs


### viroseqs db was obtained by installing ProphET and then converting the nucleotide tmp files into an abricate formatted database
  
 https://github.com/jaumlrc/ProphET  

#### I use this to detect phage genes in bacterial assemblies using abricate  
   
### Notes:
1. I removed some seemingly redundant sequences.  These had the same accession but different lengths, I kept the longer of the two
2. There is probably a more appropriate way to format this database for abricate.  
3. There were over 60,000 sequences in the original database, I ran cd-hit on the originals (default settings) to cluster and reduce the size. I think there are 40,000 sequences in there now

### How to setup this database for use with abricate:
1. Download and unzip the viroseqs_90.fasta.gz file from this repo.  
2. Ceate a 'viroseqs' directory where abricate looks for databases.  Can run the `abricate --help` command to find this path. It should be listed in the DATABASES section, next to the --datadir option.  
3. Move the decompressed fasta into this new directory with the name `sequences`.  
4. Run `abricate --setupdb`.  

### For example, this is how I configured it on my system:  
`cd ~/reference/`  
`git clone https://github.com/Jtrachsel/viroseqs.git`  
`cd viroseqs`  
`gunzip viroseqs_90.fasta.gz `  
`cd /home/julian.trachsel/miniconda3/db # wherever your abricate install looks for dbs`  
`mkdir viroseqs`  
`cp ~/reference/viroseqs/viroseqs_90.fasta ./viroseqs/sequences`  
`abricate --setupdb`  
