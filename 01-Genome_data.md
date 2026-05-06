## Page 1

Tutorial 5
Sequence conservation and biological function
MBLS207 – Bioinformatics

Viruses have a bad reputation, especially after the Corona pandemic. To most people, they are known for making us sick. However, most viruses by far, even those that live in our bodies, are completely harmless to us. In fact, most viruses do not infect humans, or any animals for that matter, but they infect bacteria. Viruses that infect bacteria are called bacteriophages. Bacteriophages and bacteria have co-existed in balance for billions of years and this balance is very important for planetary ecology.

Discovering new viruses (or even new bacteria) can be a tricky business. Unknown viruses are hard to cultivate (=grow in the lab) and even if they are successfully cultivated, it is hard to figure out how they are related to known viruses from observing their properties and behaviour. Fast and efficient DNA sequencing technologies together with bioinformatic analyses make finding and comparing viruses much easier. For example, after the virus causing the COVID19 pandemic was sequenced, it was clear within a matter of days that this virus was closely related to the virus that caused the SARS epidemic in 2002. But we are not going to work on COVID today.

One of the environments where bacteriophages play an important role is in our digestive system. As you probably know, [our gut is inhabited by billions of bacteria](https://www.google.com). They are important for digesting food, producing vitamins, helping our immune system, and even for our mental health. And everywhere one can find bacteria, one can find bacteriophages. In 2014, Bas Dutilh, a Dutch researcher that works in our department, discovered [a bacteriophage that lives in the guts of more than half of all humans, the crAssphage](https://www.google.com). As usual with newly discovered microbes and viruses, most of the proteins encoded on the crAssphage genome had no known function, and their main finding was that its sequence was present in a lot of different people. In 2019, they used samples from 67 countries to show that crAssphage is present all around the world. They further showed that some primates had crAss-like viruses in their digestive systems as well, indicating that our ancestors have been carrying crAssphage since before the dawn of humankind.

Today, you will explore the crAssphage proteome and identify which proteins are conserved across different crAssphage genomes. Via this conservation analysis, you will also learn how to predict which amino acids in a protein are most important for the function of a protein. Moreover, we will infer protein functions simply using protein sequences, and attempt gene prediction.

---


## Page 2

1. Genome data
a. First, have a look at the genome sequence of the crAssphage. Go to GenBank (https://www.ncbi.nlm.nih.gov/genbank/) and type “crassphage” into the search bar. Sort the results by sequence length, and click on one of the crassphage complete genomes. What kind of virus is the crAssphage? DNA or RNA? Does this entry represent a linear sequence or a circular genome?
b. Do you think that both DNA and RNA viruses can be found using metagenomics? Why?
c. Take a deeper look at the crassphage genome with accession number NC_067194. What kind of information can you find in a GenBank record? How many genes does this crAssphage genome contain?
