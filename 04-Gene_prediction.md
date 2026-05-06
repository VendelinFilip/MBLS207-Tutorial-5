# 4. Gene prediction
<ol type="a" start="13">
    <li>
        Download the NC_067194 genome in FASTA format. Now use <a href="https://genemark.bme.gatech.edu/genemarks.cgi">GeneMarkS</a> to predict the number of protein-coding genes in this genome. Select “Phage” as sequence type, and “GFF” as output format. The prediction should take only a couple of seconds. How many genes does GeneMarkS predict? How does this compare with the number of genes in the NCBI genome? Why do you think these numbers may differ?
    </li>
    <li>OPTIONAL: Now let's visualize the differences using the genome browser <a href="https://sanger-pathogens.github.io/Artemis/Artemis/">Artemis</a>. Download the UNIX or MacOS version, and uncompress following the website’s instructions. Then, open Artemis.<br>Download the NC_067194 genome in Genbank format, and open it using Artemis. It will display an overview of the CDS features in the crAssphage genome. Move around and explore the genome in all its length. Try zooming in and out for better views, and click on the genes to see the associated features.<br>Now, read the GeneMarkS gene predictions as an additional entry using “Read An Entry…”. You can switch between predictions (NCBI vs GeneMarkS) by clicking on these entries below the main menu. Find CDSs predicted by one genome version but not the other, and discuss how to evaluate which prediction is correct.</li>
</ol>

Today, you have learned about sequence conservation. You have learned to interpret sequence logos and identify conserved (regions in) genes or proteins. You have seen that some proteins of the crAssphage are more conserved than others, and that within a protein, some amino acids are more conserved than others. Finally, you have seen how PSI-BLAST, which makes use of sequence conservation, can be used to perform sensitive sequence similarity searches and find distantly related proteins.

**Box 2. PSI-BLAST uses sequence conservation to search for distant homologs.**

Position Specific Iterated-BLAST (PSI-BLAST) is an algorithm based on blastp, that exploits sequence conservation to detect distantly related protein sequences. First, PSI-BLAST uses an initial blastp search to find a set of good homologs in the database. Based on these hits, PSI-BLAST then creates a multiple sequence alignment and identifies which residues are more conserved and which ones are less conserved. This information is then used to search the database again, where the more conserved positions are given a higher weight, while the less conserved positions are given a lower weight. Thus, by using sequence conservation to identify which residues are important in the specific protein family and which ones may be more variable, PSI-BLAST is often able to find more distant homologs in the database than in the first round (see Figure 1). PSI-BLAST can iterate this cycle of identifying similar sequences, building alignments, and identifying the more/less conserved positions until no new high-scoring sequences are found in the database, and the alignment does not change anymore. When this happens, we say the algorithm has converged. Alternatively, researchers may choose to run a fixed number of iterations, or stop the iterations before convergence when a certain hit has been found, for example a distant homolog in a species of interest.

```mermaid
graph TD
    A[Input protein sequence] --> B[Initial blastp search]
    B --> C[Alignment of good hits]
    C --> D[Blast search where conserved residues are weighted higher than variable residues]
    D --> E{1. No new hits (converged)?<br>2. Enough iterations?<br>3. Target hit of interest found?}
    E -- No --> C
    E -- Yes --> F[Done]
```

**Figure 1. Flow diagram of the steps in Position Specific Iterated-BLAST (PSI-BLAST).**
