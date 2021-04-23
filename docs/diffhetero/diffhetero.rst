*************************************
Differential Heterogeneity Analysis
*************************************

This guide contains a brief discription of the Differential Heterogeneity Analysis used within Dprofiler. 


Introduction
============

We developed Dprofiler as a platform for easy dissemination of Bulk and scRNA data sets to detecting heterogeneous samples within disease cohort and disease studies. Dprofiler users are allowed to choose two distinct algorithms for scoring the heterogeneity of samples within the user defined differential expression analysis as  well as methods to detect differentially expressed genes. By iteratively removing heterogeneous samples and repeating the differentially expressed analysis, both algorithms converge until there are no more highly heterogeneous samples left in the data sets. The final homogeneous set of conditions are used to calculate the final heterogeneity score of samples. 

An Iterative Differential Analysis Method
=========================================

.. image:: ../dprofiler_pics2/InteractiveSilhouette.png
	:align: center
	:width: 60%
	
The Membership scores of samples are measured by two distinct similarity indices. First of these measures is the Silhouette index that allows the quality of partitioning algorithms once datasets are clustered into meaningful subsets of samples. However, we utilize the silhouette index to detect those samples that do not well clustered or classified into their associated groups or conditions with the same label. We deem those samples as heterogeneous that their expression profiles may point out minor or major differences with respect to the majority of samples within the same group.

Silhouette Measure
==================

Silhouette measure of a sample is calculated given a known partitioning (or classification) of data set and a measure of distance between all samples within the data set. We use Spearman correlation as a distance measure between expression profiles of each sample since it has been shown to be quite robust in many biological data analysis platforms and software tools (citation). The silhouette measure of each sample is calculated by separately measuring the average distance to all samples with the label and the minimum of all averages distances to other clusters with different labels, then these two measures are subtracted and normalized to calculate an index universally between -1 and 1. A silhouette measure of -1 would indicate that the sample is misclustered to its associated group and it is highly likely that its expression profile is more similar to samples of other conditions/groups. A silhouette measure of 1 would indicate a perfect clustering of the sample, and silhouette measure 0 would indicate an ambiguous similarity of expression profiles between at least two conditions. 

Non-negative Least Squares
==========================

The second type of membership score available to Dprofiler users is non-negative least squares (NNLS) regression-based score where the non-negative beta coefficients are provided by the lawson-hanson implementation of NNLS regression. Such regression analysis has been applied to various problems where target profiles were confounded by a mixture of baseline profiles and hence target profiles are detected to exhibit heterogeneous properties. Applications include proteomics, genomics, imaging and economics. We use NNLS to detect the heterogeneous samples whose expression profiles are abundant in sets of biomarkers of multiple conditions within the disease study, hence deemed as heterogeneous. We use the mean expression profiles of all the conditions as an input to the non-negative regression problem where the response variable is the sample we would like to detect its degree of heterogeneity.


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
