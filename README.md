# 2010-minimumbias-trackvertex
Validation code for 2010 MinimumBias dataset, based on track and vertex spectra

It is based on the original code in [http://opendata.cern.ch/record/462] on the CERN Open Data portal (Geiser, Achim; Dutta, Irene; Hirvonsalo, Harri; Sheeran, Bridget; (2016). Validation code for 2010 MinimumBias dataset, based on track and vertex spectra. CERN Open Data Portal. DOI:10.7483/OPENDATA.CMS.GBZR.7F2A ) and modified here for direct download from github.


You need to work in a Virtual Machine properly contextualized for CMS. Everything is available on the CERN Open Data Portal:
http://opendata.cern.ch/VM/CMS/2010.

In order to run the demoanalyzer_cfg.py to create the ROOT files, you need to create a working area and set up a proper 
CMS environment. 

## Creating the Working area
This step is only needed the first time.
```
cmsrel CMSSW_4_2_8
```
## Cloning the 2010-minimumbias-trackvertex repository from Github
Type this command to change directory:
```
cd CMSSW_4_2_8/src
```
For cloning type:
```
git clone https://github.com/cms-opendata-validation/2010-minimumbias-trackvertex Validation/TrackVertex_2010
```
## Setting up the CMS environment
```
cd Validation/TrackVertex_2010
cmsenv
```
## Compiling and Running
```
scram b
cmsRun demoanalyzer_cfg.py
```

After analysis, MinBias00val.root file should be created. 
Then, is necessary to change input and also output files in demoanalyzer_cfg.py, to save these changes and to rerun program.
In the datasets directory in the repository from github are index files with names:

```
CMS_Run2010B_MinimumBias_AOD_Apr21ReReco-v1_0000_file_index.txt
CMS_Run2010B_MinimumBias_AOD_Apr21ReReco-v1_0001_file_index.txt
CMS_Run2010B_MinimumBias_AOD_Apr21ReReco-v1_0002_file_index.txt
CMS_Run2010B_MinimumBias_AOD_Apr21ReReco-v1_0003_file_index.txt
CMS_Run2010B_MinimumBias_AOD_Apr21ReReco-v1_0004_file_index.txt
CMS_Run2010B_MinimumBias_AOD_Apr21ReReco-v1_0005_file_index.txt
CMS_Run2010B_MinimumBias_AOD_Apr21ReReco-v1_0006_file_index.txt
```
These index files are the same as you can find in the open data portal record http://opendata.cern.ch/record/8 , they are copied here for convenience and also for details of the analysis you can read comments in the analysis code TrackVertexAnalyzer.cc .
It necessary to note that whole analysis can take around 16 hours!

When you rerun all seven index files you should have seven root files with names:
```
MinBias00val.root
MinBias01val.root
MinBias02val.root
MinBias03val.root
MinBias04val.root
MinBias05val.root
MinBias06val.root
```

The last thing what you should do is to merge these seven root files into one root file.
You do this as follow. In the downloaded repository is also file with name mergeMinBias.C .
Type command for opening ROOT program:
```
root
```
In this program just type command:
```
.x mergeMinBias.C
```
This merging creates a root file called MinBiasAllval.root .
To look at this output, write down command in ROOT program:
```
new TBrowser
```
and navigate to relevant file. 
The most interesting histograms are the inclusive track pt spectra: 2.6pt, 2.4pt... - ...0.4pt, 0.2pt  corresponding to the |eta| ranges 2.6-2.4, 2.4-2.2, ... , 0.4-0.2, 0.2-0.0
