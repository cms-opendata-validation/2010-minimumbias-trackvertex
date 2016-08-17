# 2010-minimumbias-trackvertex
Validation code for 2010 MinimumBias dataset, based on track and vertex spectra

You need to work in a Virtual Machine properly contextualized for CMS. Everything is available on the CERN Open Data Portal:
http://opendata.cern.ch/VM/CMS/2010.

In order to run the demoanalyzer_cfg.py to create the ROOT files, you need to create a working area and set up a proper 
CMS environment. 

## Creating the Working area

This step is only needed the first time.

'''
cmsrel CMSSW_4_2_8
''' 

## Cloning the 2010-minimumbias-trackvertex repository from Github

Type this command to change directory:

'''
cd CMSSW_4_2_8/src
'''

For cloning type:
'''
git clone https://github.com/cms-opendata-validation/2010-minimumbias-trackvertex Validation/TrackVertex_2010
'''
