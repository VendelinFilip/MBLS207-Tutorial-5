# 3. Inferring protein function

Download the Mac/Linux BLAST+ 'tar.gz' compressed file from the NCBI website at https://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/LATEST/. This software will take up 500 Mb when decompressed; make sure this is OK with your computer setup.

```bash
# To install BLAST, first move to your software folder
cd <path-to-MBLS207>
cd software

# Get the downloaded file if it is not there yet.
# Here, we assume it is in your Downloads folder; just
# fill the correct path otherwise.
# The Linux version of this file should work exactly in
# the same manner. Make sure to change the name of this file
# accordingly
mv ~/Downloads/ncbi-blast-2.15.0+-x64-macosx.tar.gz .

# Now you can decompress this file from the command line:
tar -xvzf ncbi-blast-2.15.0+-x64-macosx.tar.gz

# That should be all! In order to check that the software works
# well, try running some of the executables
# using the help (-h, -help) options:
ncbi-blast-2.15.0+/bin/blastp -h
ncbi-blast-2.15.0+/bin/blastp -help

# Try doing this with some of the other tools in the bin folder to
# get a general idea of what they do
```

<ol type="a" start="9">
  <li>
    Open the page for protein KP06_gp75 in RefSeq (<a href="https://www.ncbi.nlm.nih.gov/protein/YP_010509481.1">https://www.ncbi.nlm.nih.gov/protein/YP_010509481.1</a>). What is the functional annotation? What does this mean? (Hint: use the internet to find your answer)
  </li>
  <li>
    We want to know what the possible function of this protein is. To do that, let's first download the database of virus proteins (viral.1.protein.faa.gz) from RefSeq at <a href="https://ftp.ncbi.nlm.nih.gov/refseq/release/viral/">https://ftp.ncbi.nlm.nih.gov/refseq/release/viral/</a>. Then, open the terminal and get the database ready for BLASTing. 
  </li>
</ol>

```bash
# Get to your MBLS207 folder and create a folder for today's tutorial
cd <path-to-MBLS207>
mkdir tutorial05
cd tutorial05

# Now let's move the database here. This line assumes the file is in
# the Downloads folder. Then, uncompress it
mv ~/Downloads/viral.1.protein.faa.tar.gz
gunzip viral.1.protein.faa.gz

# Take a look at the database using 'less' (exit 'less' typing 'q').
# In what format are the sequences there?
less viral.1.protein.faa

# Finally, check how many proteins there are in this file
grep -c ">" viral.1.protein.faa

# In order for BLAST to understand that this file is a database in
# which to search for sequences, it needs to contain some additional
# index files. You can format it by running this:
<path-to-BLAST-bin>/makeblastdb -in viral.1.protein.faa -dbtype prot
```

How many sequences are there in the RefSeq viral database?

Now download the KP06_gp75 sequence in FASTA format. To do that, go to RefSeq page above, and click on FASTA (upper left side of the protein information). Copy the header and sequence into a plain text editor (use ‘nano’ in the terminal, or programs like Notepad or TextEdit), and save this file as “KP06_gp75.faa” (‘faa’ stands for ‘fasta amino acid’) in a folder called “tutorial05” within your MBLS207 folder.

Now use the correct ‘flavour’ of BLAST to search this protein against the virus database, and set “KP06_gp75_vs_viralRefSeq.blastp” as output file name. How many hits do you obtain? How many of these hits are informative? Can you explain what the first hit represents? Can you venture anything about this protein’s function based on these results?

<ol type="a" start="11">
  <li>
    One of the reasons that you got only a few hits when searching for homologs of protein KP06_gp75 in viruses, is that viruses are fast-evolving organisms. This means that their gene and protein sequences are not very well conserved and detecting homologs with standard approaches like BLAST is difficult. One solution is to use Position-Specific Iterated BLAST (PSI-BLAST, see Box 2). Query the sequence of protein KP06_gp75 again the viral database with PSI-BLAST. Use an e-value threshold of 0.001, “KP06_gp75_vs_viralRefSeq.psiblast” as output file name and 2 as the number of iterations. How many more hits do you obtain? Can you speculate further about the function of this protein?
  </li>
  <li>
    Let's give a final try to the functional annotation of this protein. Go to <a href="https://www.ebi.ac.uk/interpro/search/sequence/">https://www.ebi.ac.uk/interpro/search/sequence/</a>, and search this sequence. Do you think the results help interpret something about the function of the protein, or why it is so hard to annotate it? Compare the results with those of <a href="https://www.ncbi.nlm.nih.gov/protein/YP_010509486.1?report=fasta">KP06_gp80</a>.
  </li>
</ol>

[Go to module 4](04-Gene_prediction.md)
