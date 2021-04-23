*************************************
Cellular Composition Analysis
*************************************

This guide contains a brief discription of MuSiC algorithm used within Dprofiler for estimating cellular compositions of Reference bulk expression data set using the scRNA expression data. 

Introduction
============

We use a Bulk RNASeq deconvolution algorithm that estimate expression profile proportions from bulk RNA gene expression data given an external set of expression profiles.

MuSiC Algorithm
===============

The MuSIC algorithm employs single cell genomic expression profiles to acquire non-negative least squares estimates (Wang et al.). A specific feature of MUSIC allows the proportions of closely related cell types to be correctly estimated. To deal with collinearity, MuSiC employs a tree-guided procedure that recursively zooms in on closely related cell types. Rather than pre-selecting marker genes from scRNA-seq based only on mean expression, MuSIC gives weight to each gene allowing for the use of a larger set of genes in deconvolution. The weighting scheme prioritizes consistent genes across subjects: (i) up-weighing genes with low cross-subject variance (informative genes) and (ii) down-weighing genes with high cross-subject variance (non-informative genes). This requirement on cross-subject consistency is critical for transferring cell type-specific gene expression information from one dataset to another.

.. image:: ../dprofiler_pics2/music.jpg
	:align: center
	:width: 99%

References
==========

1. Anders,S. et al. (2014) HTSeq - A Python framework to work with high-throughput sequencing data.

2. Chang,W. et al. (2016) shiny: Web Application Framework for R.

3. Chang,W. and Wickham,H. (2015) ggvis: Interactive Grammar of Graphics.

4. Giardine,B. et al. (2005) Galaxy: a platform for interactive large-scale genome analysis. Genome Res., 15, 1451–1455.

5. Howe,E.A. et al. (2011) RNA-Seq analysis in MeV. Bioinformatics, 27, 3209–3210.

6. Kallio,M.A. et al. (2011) Chipster: user-friendly analysis software for microarray and other high-throughput data. BMC Genomics, 12, 507.

7. Li,B. and Dewey,C.N. (2011) RSEM: accurate transcript quantification from RNA-Seq data with or without a reference genome. BMC Bioinformatics, 12, 323.

8. Love,M.I. et al. (2014) Moderated estimation of fold change and dispersion for RNA-seq data with DESeq2. Genome Biol., 15, 550.

9. Reese,S.E. et al. (2013) A new statistic for identifying batch effects in high-throughput genomic data that uses guided principal component analysis. Bioinformatics, 29, 2877–2883.

10. Reich,M. et al. (2006) GenePattern 2.0. Nat. Genet., 38, 500–501.

11. Risso,D. et al. (2014) Normalization of RNA-seq data using factor analysis of control genes or samples. Nat. Biotechnol., 32, 896–902.

12. Ritchie,M.E. et al. (2015) limma powers differential expression analyses for RNA-sequencing and microarray studies. Nucleic Acids Res., 43, e47–e47.

13. Trapnell,C. et al. (2012) Differential gene and transcript expression analysis of RNA-seq experiments with TopHat and Cufflinks. Nat. Protoc., 7, 562–578.

14. Vernia,S. et al. (2014) The PPAR$\alpha$-FGF21 hormone axis contributes to metabolic regulation by the hepatic JNK signaling pathway. Cell Metab., 20, 512–525.

15. Murtagh, Fionn and Legendre, Pierre (2014). Ward's hierarchical agglomerative clustering method: which algorithms implement Ward's criterion? Journal of Classification 31 (forthcoming).

16. Johnson et al. (2007) Adjusting batch effects in microarray expression data using empirical Bayes methods.  Biostatistics, 8, 118-127.
