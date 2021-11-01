*************************************
Computational Profiling
*************************************

This guide contains a brief discription of the Computational Profiling Analysis used within Dprofiler. 


Introduction
============

Dprofiler provides methods for calculating membership scores to be used to profiling samples associated to phenotypic profiles of interest with the submitted dataset. By iteratively removing samples with low scores and repeatatively testing for differentially expressed genes, computational profiling analysis of Dprofiler converges if there are no more low-scored samples left in the data set. The final list of samples with high membership scores establish homogeneous (pure) reference profiles of these phenotypic groups, and they are used to calculate the final score to establish the profile of each individual sample:

* Conducts a DE analysis (DESeq2, EdgeR or Limma) given remaining samples within the data.
* Estimates the membership scores (based on either Silhouette and NNLS) of all samples given expression profiles limited to differentially expressed genes
* Removes samples with low membership scores.
* Repeats until no more samples have to be removed from the data.


The Membership scores of samples are measured by two distinct similarity measures and methods. First of these measures is the Silhouette index that allows quality control of partitioning algorithms once datasets are clustered into meaningful subsets of samples. However, we utilize the silhouette index to detect those samples that do not well clustered or classified into their associated groups or conditions with the same label. The second method is based on a linear regression method whose coefficients are regularized to non-negative values as to calculate the
percentage of input variables. Such a method allows us to model expression profile of each submitted sample given mean expression profiles of phenotypes/conditions where coefficient are associated to scores, representing the similarity between the condition and the submitted sample. 

.. image:: ../dprofiler_pics2/InteractiveSilhouette.png
	:align: center
	:width: 60%
	
|

Silhouette Measure
==================

`Silhouette measure <https://en.wikipedia.org/wiki/Silhouette_(clustering)>`_ of a sample is calculated given a known partitioning (or classification) of data set and a measure of distance between all samples within the data set. We use Spearman correlation as a distance measure between expression profiles of each sample since it has been shown to be quite robust in many biological data analysis platforms and software tools (citation). The silhouette measure of each sample is calculated by separately measuring the average distance to all samples with the label and the minimum of all averages distances to other clusters with different labels, then these two measures are subtracted and normalized to calculate an index universally between -1 and 1. A silhouette measure of -1 would indicate that the sample is misclustered to its associated group and it is highly likely that its expression profile is more similar to samples of other conditions/groups. A silhouette measure of 1 would indicate a perfect clustering of the sample, and silhouette measure 0 would indicate an ambiguous similarity of expression profiles between at least two conditions. We normalize silhouette measure of each submitted sample between (0,1) to establish the membership score.  

Non-negative Least Squares
==========================

The second type of membership score available to Dprofiler users is `non-negative least squares <https://en.wikipedia.org/wiki/Non-negative_least_squares>`_ (NNLS) regression-based score where the non-negative beta coefficients are provided by the lawson-hanson implementation of NNLS regression. Such regression analysis has been applied to various problems where target profiles were confounded by a mixture of baseline profiles and hence target profiles are detected to exhibit heterogeneous properties. Applications include proteomics, genomics, imaging and economics. We use NNLS to detect the heterogeneous samples whose expression profiles are abundant in sets of biomarkers of multiple conditions within the disease study, hence deemed as heterogeneous. We use the mean expression profiles of all the conditions as an input to the non-negative regression problem where the response variable is the sample we would like to detect its degree of heterogeneity. We use the estimated coefficients are the membership scores. 
