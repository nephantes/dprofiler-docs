******************
Installation Guide
******************

Before you start; you will have to install R and/or RStudio.
You can install Dprofiler from GitHub. Install the required dependencies by running the following commands in R or RStudio. 

**A. Installation instructions from source code**::

    install.packages("devtools") ## If you haven't installed devtools, you can easily install it by using this command 
    library("devtools")
    install_github("UMMS-Biocore/dprofiler")
        
-----

After dprofiler installation, you can load and start dprofiler by following commands::

        library(dprofiler)
        startDprofiler()

Once you run ``startDprofiler()`` shiny will launch a web browser which is ready to use!

For more information about Dprofiler, please visit our **Quick-start Guide** section within documentation.
