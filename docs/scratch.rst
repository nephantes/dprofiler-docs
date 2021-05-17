.. Dprofiler documentation master file, created by
   sphinx-quickstart on Tue Sep 13 14:28:12 2016.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Welcome to Dprofiler's documentation!
=====================================

What is Dprofiler ?

There is no doubt that biosamples collected from diverse sources of experimental and technical conditions result in **heterogeneous patterns** of expression profiles associated with phenotypic groups of a disease cohort. These samples could also be described as **outliers** of phenotypic groups of interest, exhibiting **extreme alterations and differentiations in expression patterns**. Also, It is highly likely that a phenotypic group of few samples would include a subpopulation of samples with homogeneous expression levels as opposed to a few samples with considerably variable gene or protein abundances. Such heterogeneity or outlying behaviour within studies may occur by mislabeling samples, unexpected technical, experimental or biological variations.

To detect such heterogeneities and outliers within disease cohorts and datasets, we have developed Dprofiler. 

.. image:: /dprofiler_pics2/InteractiveSilhouette.png
  :align: center
  :width: 60%

This novel application allows easy dissemination of Bulk and scRNA data sets to detect heterogeneous samples within submitted disease cohorts and disease studies. Dprofiler evaluates bulk RNA samples, detect anomalies within each sample of a bulk dataset and further explore causes of such heterogeneous patterns via external single cell scRNA data sets and other bulk RNA data sets. 

Users are allowed to choose from a variety of algorithms for **scoring the heterogeneity** of samples within the user-defined differential expression analysis as well as methods to detect differentially expressed genes. These scores are universally interpretable, and indicate the level of heterogeneity of each sample. By iteratively removing heterogeneous samples and repeating the differentially expressed analysis, both algorithms converge until there are no more highly heterogeneous samples left in the data sets. The final homogeneous set of conditions are used to calculate the final heterogeneity score of samples.

Contents:

.. toctree::
   :maxdepth: 2

   quickstart/quickstart
   local/local
   diffhetero/diffhetero
   cellcomp/cellcomp
   deseq/deseq
   references/references

