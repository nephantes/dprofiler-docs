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
