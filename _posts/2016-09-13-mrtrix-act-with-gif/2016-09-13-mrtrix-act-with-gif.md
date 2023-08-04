---
title: "Technical: MRtrix ACT using GIF parcellation"
date: "2016-09-13"
categories: 
  - "technical"
  - "work"
---

Software: MRtrix 3 (0.3.15) Pipeline: Anatomically Constrained Tractography (ACT)

Here in [CMIC](http://www.ucl.ac.uk/cmic) we analyse a lot of structural MR images using Jorge Cardoso's [Geodesic Information Flows](http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=7086081) (GIF) algorithm, which utilises the [Neuromorphometrics](http://neuromorphometrics.org:8080/nvm/download.html) parcellation. Jorge and colleagues currently offer a web service that will segment and parcellate your structural MRI using GIF: [NiftyWeb](http://cmictig.cs.ucl.ac.uk/niftyweb/program.php?p=GIF).

I wanted to do some AC tractography and connectomics with [MRtrix](http://www.mrtrix.org/) based on [this tutorial](http://mrtrix.readthedocs.io/en/latest/tutorials/hcp_connectome.html), but using a GIF-based parcellation rather than FreeSurfer. Following the hints at the bottom of [this ACT tutorial](http://mrtrix.readthedocs.io/en/latest/workflows/act.html), I succeeded. Keep reading to find out how.

#### Making MRtrix ACT work using GIF segmentation/parcellation, rather than FreeSurfer

_Definitions_: `$MRTRIX` – path to your mrtrix3 installation `$GIFDB` – path to relevant GIF-specific files for ACT (if you're lucky enough to have the GIF source code, you can generate these yourself, but I provide them below)

##### 1\. Calling `5ttgen` to generate 5TT.mif

This creates a Five Tissue Type file (Cortical/Subcortical GM; WM; CSF; Pathological tissue). When using the `freesurfer` argument, this refers to the following script: `$MRTRIX/scripts/src/_5ttgen/freesurfer.py`, which relies upon configuration files in the `$MRTRIX/scripts/data` folder: – `FreeSurferACT.txt` – `FreeSurferACT_sgm_amyg_hipp.txt`

###### How to modify this process for GIF

- I wrote a MATLAB/Octave script `GIFColourLUT_generator.m` (not supplied here) to create the necessary config files: `$MRTRIX/scripts/data/[GIF2ACT.txt](http://neiloxtoby.com/work/wp-content/uploads/2016/09/GIF2ACT.txt)` `$MRTRIX/scripts/data/[GIF2ACT_sgm_amyg_hipp.txt](http://neiloxtoby.com/work/wp-content/uploads/2016/09/GIF2ACT_sgm_amyg_hipp.txt)` `$GIFDB/[GIFcolourLUT.txt](http://neiloxtoby.com/work/wp-content/uploads/2016/09/GIFColourLUT.txt)`
- I manually edited `$MRTRIX/scripts/src/_5ttgen/freesurfer.py` and saved it as `$MRTRIX/scripts/src/_5ttgen/[gif.py](http://neiloxtoby.com/work/wp-content/uploads/2016/09/gif.py_.txt)`
- I added `export GIFDB_HOME=$GIFDB` to my bash profile (reminiscent of `FREESURFER_HOME`)

##### 2\. Connectome Lookup Table (LUT)

This step simply renumbers the ROIs, such that the numbers in the image no longer correspond to entries in the colour lookup table (the Neuromorphometrics ROI numbers), but to rows and columns of the connectome.

- Create GIF version of the connectome LUT as: `$MRTRIX/src/connectome/tables/[gif_default.txt](http://neiloxtoby.com/work/wp-content/uploads/2016/09/gif_default.txt)` (mrtix v0.3.15) `$MRTRIX/src/connectome/config/[gif_default.txt](http://neiloxtoby.com/work/wp-content/uploads/2016/09/gif_default.txt)` (mrtix v0.3.14)

##### 3\. Rerun the HCP connectome tutorial using GIF

I leave this as an exercise for you.

You'll need a GIF-processed T1 image, so you should submit the structural MR image (`T1w_acpc_dc_restore_brain_GIF_Parcellation.nii.gz`) to the [NiftyWeb GIF parcellation service](http://cmictig.cs.ucl.ac.uk/niftyweb/program.php?p=GIF) and save the resulting parcellated file in an appropriate location.

#### Differences if you want to use non-HCP data, such as ADNI

ADNI is single-shell diffusion data, so you need to modify the pipeline at the appropriate points. I have tested this out on _processed data_ from ADNI (contact me if you don't know how to download processed images from [LONI](https://ida.loni.usc.edu)). I found that the diffusion and structural images were misaligned by a linear translation, so I shifted them to the same origin using MRtrix:

\[code language="bash"\] mrinfo -transform ${T1\_}.mif | cat >> ${T1\_}\_transform.txt mrtransform -replace ${T1\_}\_transform.txt ${DTI\_}.mif ${DTI\_}\_trans.mif mrview ${T1\_}.mif -overlay.load ${DTI\_}\_trans.mif -overlay.opacity 0.3 \[/code\]
