---
title: "Technical: Eroded Subcortical White Matter mask"
date: "2024-07-03"
categories: 
  - "technical"
  - "work"
---

Software: [MRtrix](http://mrtrix.readthedocs.io), [FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/)

If you've ever wondered how to get a nice mask for the eroded subcortical white matter region, and use it as a reference region in your SUVR analyses, then read on. This is considered by many to be the holy grail of longitudinal PET SUVR reference regions.

I recently had to do it myself when processing the [A05 data](https://doi.org/10.1093/brain/awz090) from AVID (an Eli Lilly subsidiary) --- so that we could validate results found with [ADNI](http://adni.loni.usc.edu/)'s SUVR data.

Prerequisites: an SUVR image using any reference region, and masks for Left and Right Cerebral White Matter (FreeSurfer aparc+aseg region numbers 2 and 41). To obtain these, I ran the [AmyPET](https://github.com/AMYPAD/AmyPET) centiloid pipeline, tweaked for FreeSurfer ROIs by Pawel Markiewicz and myself. This required FreeSurfer outputs (I used [this container](https://e-dads.github.io/tools/#freesurfer-711-bids-app-container) for version 7.1.1) and produces a static SUVR image for both whole cerebellum and cerebellar gray matter reference regions.

All that's left is to calculate the mean SUVR (for either of those reference regions) within the eroded subcortical white matter ROI. Various papers have used such a reference region, showing that it's the best for longitudinal studies in both amyloid and tau PET:

- [Landau et al., 2015](https://doi.org/10.2967/jnumed.114.148981)
- [Chen et al., 2015](https://doi.org/10.2967/jnumed.114.149732)
- [Lowe, et al., 2018](https://doi.org/10.2967/jnumed.117.204271)

Here's how I generated the eroded subcortical white matter mask, following ADNI's approach to eroding cerebral white matter. This is from [Landau et al., 2015](https://doi.org/10.2967/jnumed.114.148981) and is described in ADNI's document [UCBERKELEY_AV1451_Methods_11.15.2021.pdf](https://ida.loni.usc.edu/download/files/study/c579d960-27e8-4c6f-964c-eefca4ca513b/file/adni/UCBERKELEY_AV1451_Methods_11.15.2021.pdf):

### Step 0: Create the (non-eroded) subcortical white matter ROI

For convenience:
```
topf=.
mask=${topf}/mask_freesurfer_regions_2_41.nii.gz
mask_smoothed=$(dirname $mask)/$(basename $mask .nii.gz)-smoothed.nii.gz
mask_eroded=$(dirname $mask_smoothed)/$(basename $mask_smoothed .nii.gz)-eroded.nii.gz
suvr_image=${topf}/suvr.nii.gz
```

If you have FreeSurfer `recon-all` output, these masks can be extracted from `mri/aparc+aseg.mgz`. 
Here I use `mri_binarize` on FreeSurfer's example subject `bert`:
```
freesurfer_dir=/Applications/freesurfer/7.4.1
subj=bert
${freesurfer_dir}/bin/mri_binarize --i ${freesurfer_dir}/subjects/${subj}/mri/aparc+aseg.mgz --match 2 41 --o ${mask}
```

### Step 1: Smooth the FreeSurfer WM mask

ADNI uses 8mm-isotropic FWHM smoothing, which I implemented in [MRtrix](http://mrtrix.readthedocs.io):

```
fwhm=8
mrfilter -fwhm $fwhm $mask smooth $mask_smoothed
```

### Step 2: Threshold at 0.7

```
thresh=0.7
mrthreshold -abs $thresh $mask_smoothed $mask_eroded
# Have a look
mrview $suvr_image --overlay.load $mask_eroded
```

### Step 3: Calculate Holy Grail SUVR

Uses `fslstats`:
```
# Mean only
fslstats $suvr_image -k $mask_eroded -m
```
