
# Bowtie2 
- Bowtie는 alignment툴이다.
- 빠르고 효율적인 short read aligner이다. 
- 이들은 large genome에 short DNA sequence(reads)의 많은 set들을 빠르게 aligning하는 것을 목표로 설계되었다. 
- Bowtie는 Burrows - Wheeler index와 함께 reference genome을 index 하며, aligning Output Format은 standart SAM format이다. 
- 따라서, SAM format을 이용할 수 있는 SAMtools와 같은 SNP 그리고 indel caller 등의 다양한 tool들을 함께 사용될 수 있다.
(RNA-Seq read들을 위한 빠른 splice junction mapper인 TopHat, RNA-Seq read들로부터 transcriptome assembly 그리고 isoform quantitiation을 하는 tool인 Cufflinks, large-scale resequencing data를 위한 cloud-computing software tool인 Crossbow, large RNA-seq datasets에서 다양한 gene expression을 계산하기 위한 cloud computing tool인 Myrna)


## Alignment 

- Bowtie는 alignment를 하기 위해서 read set 그리고 index가 필요하다.
- 



