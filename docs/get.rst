Get CTSM 
=========

This is where you should start.

NordicESMhub maintains a CTSM repository with all the configuration files for running on machines supported by `Sigma2 <https://www.sigma2.no/>`_. For now we support:

- saga 
- fram 

If your machine is not in the list and you would like us to support it, please contact us.

For compatibility, load git version 2.23.0 or higher on your super computer

::

    git/2.23.0-GCCcore-8.3.0

How to get CTSM (for users)
---------------------------

To get the FATES EMERALD platform version, CLONE from NordicESM hub

::

    git clone -b release-clm5.0 https://github.com/NordicESMhub/ctsm.git ${HOME}/ctsm_fates_emerald
   
In this example we are checking out the release-clm5.0 tag and create a new local branch (recomended).
The destination of the checkout is a directoy (e.g. ctsm_fates_emerald) in our home directory. 

How to get a specific branch
+++++++++++++++++++++++++++++

Change into the created ctsm directory 

::

    cd ${HOME}/ctsm_fates_emerald
    
Check all existing branches

::

    git branch --all

To checkout the FATES EMERALD platform (in this example release 2.0.1) into a new local branch (e.g. new_branch_name)

::

    git checkout release-emerald-platform2.0.1 -b new_branch_name

For later reference, it is usefull to choose new_branch_name according to function and include the version and your username, e.g. username_release-emerald-platform2.0.1.

To fetch the proper externals (CIME, FATES, etc.) run

::

    ./manage_externals/checkout_externals
    
from the main ctsm directory (we are going to call this $CTSM_ROOT from now on).
All should be set by this and you should be able to create your first case.

Which branch do I run?
++++++++++++++++++++++

How to get CTSM (for developers)
--------------------------------

From `ESCOMP-hub <https://github.com/ESCOMP/CTSM>`_ (recommended)?
+++++++++++++++++++++++

This tutorial assumes that you are logged into one of the clusters (fram or saga) at sigma2. For access to those see (future referance to prerequisites section).

Start from your home folder
::
    cd

Clone CTSM from ESCOMP
::
    git clone --origin escomp https://github.com/ESCOMP/CTSM.git CTSM

Change into the new directory
::
    cd CTSM
    
Create a local branch 
::
    git checkout master -b my_branch_name

For later reference, it is usefull to choose my_branch_name according to function and include the version and your username.

To fetch the proper externals (CIME, FATES, etc.) run

::

    ./manage_externals/checkout_externals

Now you need to add machine specifics for the norwegian clusters. This is done by replacing some default configuration files with configuration files that contain details for these clusters. 
:: 
    cd cime/config/cesm/machines
Delete the default files 
::
    rm config_machines.xml config_batch.xml config_compilers.xml
    
Fetch replacementfiles from https://github.com/gunnartl/config_files_sigma2.git
::
    git init
    git remote add origin https://github.com/gunnartl/config_files_sigma2.git
    git pull origin main
    
From NordicESM hub?
+++++++++++++++++++
Follow the steps above, but checkout the fates_emerald_api instead
    
::

    git checkout fates_emerald_api -b new_branch_name

For later reference, it is usefull to choose new_branch_name according to function and include the version and your username, e.g. username_fates_emerald_api.
After checking out the externals, change to cime directory and create your own branch to record all your changes

:: 

    cd externals/cime
    git checkout -b username_cime
    
Change to fates directory and create your own branch to record all your changes

::

    cd externals/fates
    git checkout -b username_fates
  
If you do not create your own branch for "cime" and "fates", running "./manage_externals/checkout_externals", will overwrite your previous "cime" and "fates".
You should be ready to create your first case.


