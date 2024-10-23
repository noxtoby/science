---
layout: archive
title: "Available projects"
permalink: /student-projects/
excerpt: "Currently available student research projects"
author_profile: true
date: "2024-10-23"
---

Here are some [POND](http://pond.cs.ucl.ac.uk) (disease progression modelling) student projects I have available. Contact me for more information.

* * *

ARIA detection for Alzheimer's disease
======

with Prof. Frederik Barkhof (UCL Hawkes Institute, UCL Queen Square Institute of Neurology, Amsterdam UMC)

Amyloid-Related Imaging Abnormalities (ARIA) are side-effects of the latest disease-modifying therapies in Alzheimer's disease. There is global interest in developing AI-based solutions for detection (diagnosis) and prediction of ARIA, with the goals of improving safety and efficiency of clinical trials, and for deployment in clinical decision support as these new drugs reach the frontline of healthcare. 

This project aims to train a useful “AI model” for detecting and/or predicting ARIA. Training data would consist of MRI data from multiple studies that has been organised by the POND group. The Testing data we have in mind is from the [Bapineuzimab](https://www.alzforum.org/therapeutics/bapineuzumab) clinical trials, for which the primary supervisor has remote access via the [YODA project](https://yoda.yale.edu/).

Further reading:

- [Sperling et al., Alzheimer's & Dementia (2011)](https://doi.org/10.1016/j.jalz.2011.05.2351)
- [icobrain aria](https://icometrix.com/services/icobrain-aria): [Sima, et al., JAMA Network Open (2024)](https://doi.org/10.1001/jamanetworkopen.2023.55800)

* * *

Subtype and Stage Inference (SuStaIn) for the real world
======

with Zuzana Walker (UCL Psychiatry) and the [UCL CODEC](https://ucl-codec.github.io) team.

[SuStaIn](https://ucl-pond.github.io/pySuStaIn/) ([Young et al., 2018](https://doi.org/10.1038/s41467-018-05892-0)) is a merging of data-driven disease progression modelling (https://rdcu.be/dvstu) and unsupervised machine learning to uniquely unravel the heterogeneity of chronic diseases in both space and time. Research studies on SuStaIn in dementia-causing neurodegenerative diseases to date have been unimodal (for example, input features derived from a single modality of medical imaging), but real-world dementia healthcare involves multiple modalities.

In this project, the student will use multimodal imaging features designed to be suitable for a typical dementia care pathway in the NHS. This will include processing some data (using existing pipelines) and performing some feature selection, then training a healthcare-ready SuStaIn model. Training data comes from observational clinical research studies available to the POND group. Testing data will include real-world healthcare data from the Essex Memory Clinic.


* * *

DEM: Differential Equation Models — long-term biomarker trajectories from short-term data
======

Reconstruction of biomarker trajectories ideally requires dense longitudinal data collected over the full time-course of a chronic disease. Such data is not available due to the prohibitive expense and complexity of collection, which means that we must resort to alternative methods. In neurodegenerative diseases such as Alzheimer's, the availability of short-term longitudinal data of a few years permits estimation of an individual's rate of change over that time span, e.g., via linear regression. These short-interval longitudinal observations can be interpreted as noisy samples (segments) from an average biomarker trajectory. Instead of attempting to align the raw data segments, e.g., (Donohue et al., Alzheimer's & Dementia 2014), the differential equation modelling approach (Villemagne et al., The Lancet Neurology 2013; Oxtoby et al., LNCS 2014) generates a cross-section of differential data and a model fit: biomarker rate-of-change as a function of biomarker value, i.e., a differential equation model (DEM). For sufficient coverage across a range of biomarker values tracking disease progression, the fitted function can be integrated to produce a trajectory.

Such trajectories have been estimated in dominantly-inherited Alzheimer's disease using a univariate nonparametric Bayesian DEM (Oxtoby et al., Brain 2018), resulting in state of the art predictive utility.

This project extends nonparametric DEM to the nontrivial multivariate case, and applies to sporadic Alzheimer's disease.

* * *

Power calculations for Data-Driven Disease Progression Models
======

The event based model (EBM) is a generative statistical model for estimating a sequence of cumulative abnormality in a progressive process like a neurodegenerative disease. Invented at UCL in 2011, the EBM is widely used in clinical Neurology and other applications, becoming a popular tool in the arsenal of quantitative researchers worldwide. This has seen it included in prospective studies and grant applications, which typically require a statistical analysis plan including a traditional power/sample size calculation. 

This project will investigate sample size calculations for the EBM in both simulation and theory. For example, performing a thorough numerical simulation study to deliver a comprehensive picture of the statistical power of the EBM, in particular how it depends on various characteristics of the data including effect size / disease signal, sample size, sequence length (number of biomarkers).

The challenge is that the EBM posterior is analytically intractable, so we may have to resort to simulation.

1. Simulate biomarker ground truth data for N events from M samples/individuals.
  - Sigmoidal trajectories: gradient, midpoint (, etc.?).
  - Noise levels: controls (natural variation), patients (measurement noise + other sources of variation, e.g., subtypes)
2. Sample M patients (also controls, probably same sample size). 
3. Fit EBM.
4. Sample sequences from the posterior (directly from the MCMC).
5. Calculate Kendall's tau between ML sequence and posterior samples => distribution of tau.

* * * 

Kernel Density Estimation mixture models and Data-Driven Disease Progression Models
======

**Background**

- Mixture modelling is a flexible unsupervised/semi-supervised ML method used for clustering (among other things)
- The event based model (EBM) is a generative statistical model for estimating a sequence of cumulative abnormality in a progressive process like a neurodegenerative disease. Invented at UCL in 2011, the EBM is widely used in clinical Neurology and other applications, becoming a popular tool in the arsenal of quantitative researchers worldwide.

- The kernel density estimation (KDE) EBM uses KDE mixture modelling to quantify event probabilities and likelihoods. That is, the components of the mixture model are "nonparametric" KDE distributions. This is particularly well-suited to disease progression models that include features having skewed (non-Gaussian) distributions, such as cognitive test scores. But this "nonparametric" mixture modelling methodology holds promise for use beyond disease progression modelling.

There are three methodological innovations of interest to KDE MM:

1. Adaptive Gaussian kernel bandwidth that produces a sensible mixture model in the context of disease progression modelling.
2. Non-Gaussian kernels.
3. Bayesian MM.

This project will investigate one or all of the above, assessing performance against simulated ground truth data and on real-world data from neurodegenerative diseases such as Alzheimer's and Parkinson's.

* * *

MLAH: Machine Learning Accelerated Histopathology
======

with Prof. Tammaryn Lashley (UCL Queen Square Institute Of Neurology Brain bank) <br/>
and Assoc. Prof. Andre Altmann (UCL Hawkes Institute)

**Background:**

- Histopathology is the gold standard for diagnosing neurodegenerative diseases (including the many dementias)
- It's currently a time-consuming, semi-quantitative, manual procedure
- PlaqueBox ([paper](https://www.nature.com/articles/s41467-019-10212-1), [code](https://github.com/keiserlab/plaquebox-paper/)) is a recently-developed deep learning tool for classifying two types of dementia-related pathology

**Project questions:**

- Can we automate differential diagnosis of dementias in historical QSBB data using _machine learning + segmentation_ ideas like in PlaqueBox?
- Can we extend this to also quantify the amount of pathology, and map its location?
- Can we extend this to detect more pathologies of interest?

**Suitable students will have keen interests in:**

- Machine learning & Medical Image Computing: segmentation, saliency mapping, multiclass classification, hacking code, deep learning
- Neurodegenerative diseases like Alzheimer's disease
- Having fun while doing multidisciplinary research

This project aims to revolutionise neuropathology by developing and validating an automated toolbox using machine learning (including deep learning) and medical image computing (including disease progression modelling). This will contribute to a line of work aiming to improve our understanding of the heterogeneity in dementias by linking knowledge from _in vivo_ brain scans with knowledge from _post mortem_ histopathology. 

Clinical Neurologists diagnose probable dementias based on symptoms and brain scans. However, gold standard diagnosis occurs in the _post mortem_ brain where Neuropathologists classify dementias and other brain disorders from microscopy images of brain samples (slices). This includes identifying and quantifying pathologic accumulation of proteins, typically via immunohistochemistry staining where dye-carrying antibodies bind to target proteins.

In the current neuropathology workflow, brain tissue is sliced thinly (7µm), stained/fixed, then imaged and processed in a semi-automated way using classic methods such as filtering and edge-detection to highlight potential elements of interest. Expert manual quantification focusses on relevant regions of interest. Limitations include poor throughput (only a small region of the slide can be scored), interrater variability, variable quality (some pathologies are not reliably distinguishable), low precision (protein location is ignored).

* * *

MRI Precious: Deidentifying MRI using defacing algorithms — one algorithm to rule them all?
======

with Zuzana Walker (UCL Psychiatry), <br/>
Dave Cash (UCL Queen Square Dementia Research Centre), <br/>
Geoff Parker (UCL Hawkes Institute)

**Background:**

- ML research on brain disorders benefits from large datasets of brain scans
- Ethical and legal sharing of medical data is impeded by Personal Data — including faces on MRI
- Defacing algorithms exist, but it is not known how these influence downstream neuroimaging and ML analyses

**Project Questions:**

- Do existing defacing algorithms affect quantitative neuroimaging analyses (brain volumetry) and ML analyses (novel disease progression modelling; and deep learning)? If so, how?
- Can we devise a novel defacing algorithm that does better? Or at least, the requirements.

**Suitable students will have keen interests in:**

- Medical Image Computing, in particular involving MRI and neurodegenerative diseases like Alzheimer's disease
- Facial recognition
- ML for societal benefit
- Having fun while doing multidisciplinary research

* * *

Model comparison for clustering algorithms: how to choose the number of clusters
======

Model comparison is an unsolved problem, but there are existing approaches that perform well under many circumstances. This project aims to help in situations where model comparison doesn't provide convincing/conclusive evidence that one model is superior to another — in particular, for clustering algorithms.

In the context of disease progression modelling, clustering has been employed to estimate multiple disease progression sequences such as in the Subtype and Stage Inference algorithm, SuStaIn (Young, et al, Nature Communications 2018). SuStaIn analyses currently decide the number of subtypes using cross-validation via the cross-validation information criterion (CVIC) and test set log-likelihood. This project aims to augment/replace this with ideas based on information content, e.g., are the subtype progression patterns significantly different from each other (in a statistical sense)? Does the Nth subtype add information to the N-1 subtypes model? And other important questions.

* * *

Machine Learning to Characterise Heterogeneity of Cognitive Decline in Autopsy-confirmed Dementias
======

This project is a collaboration with researchers at the [UCSD ADRC](https://neurosciences.ucsd.edu/centers-programs/adrc/index.html) and the UCL Queen Square Institute of Neurology Dementia Research Centre.

Dementia is typically associated with abnormal memory. But there is a spectrum of cognitive, functional, psychological, and psychiatric symptoms experienced across multiple dementias. Alzheimer's disease is the primary cause of dementia, with others including vascular dementia, frontotemporal dementia, dementia with Lewy bodies, and Parkinon's disease dementia. Gold standard diagnosis occurs _post mortem_ (autopsy), with probable diagnosis possible in living patients.

This project will leverage disease progression modelling methods and expertise developed in the UCL POND group, and autopsy-confirmed data from the UCSD ADRC. Additional data may be analysed from the UCL DRC and the Amsterdam UMC Dementia Cohort.

The primary aim is to map out the sequence(s) of cognitive decline within and across dementias, with scope for the student to develop new methods. This has the potential to impact upon the way clinical trials are run in dementia-causing diseases --- a multi-billion dollar industry potentially benefitting hundreds of millions of people.

* * *

From Analogue to Digital Radiology in a memory clinic: learning a mapping from analog film to digital images
======

Work with the [UCL CODEC](https://ucl-codec.github.io) team, a joint NHS-UCL collaboration on memory clinic image computing.

We have a collection of old analog brain scan film (CT and MRI) from deceased former patients at the NHS Essex Memory Clinic, and some accompanying radiological reports generated from expert human assessment of the analogue film. Some analogue scans also have digital DICOMs from which we can train a model to learn the physical-to-digital mapping — this is the primary aim of this project (we might take inspiration from [Michael Ebner](https://doi.org/10.1016/j.neuroimage.2017.09.056)'s method and [code](https://github.com/gift-surg/VolumetricReconstructionFromPrintedFilms)).

The remaining analogue scans will be digitised using the trained model. Finally, quantitative neuroradiology reports will be generated from the digitised scans (perhaps in collaboration with the Quantitative Neuroradiology Initiative at UCL ([QNI](http://qni.cs.ucl.ac.uk/): e.g., [Goodkin, _et al._, 2019](https://pubmed.ncbi.nlm.nih.gov/31368776/), [Pemberton, _et al._, 2019](https://pubmed.ncbi.nlm.nih.gov/34476511/)), then compared with the human-generated reports.

* * *

Scan in Harmony: harmonisation of brain images from different scanners
======

Work with the [UCL CODEC](https://ucl-codec.github.io) team, a joint NHS-UCL collaboration on memory clinic image computing.

It is well known among experts that MRI scanners add non-random noise (bias) into brain scans. This confounds studies of brain ageing and [data-driven disease progression modelling](https://rdcu.be/dvstu), which typically leverage large multisite datasets that use many different scanners, such as [ADNI](https://adni.loni.usc.edu).

A recent study from the Mayo Clinic in the USA ([Gebre, et al., NeuroImage 2023](https://doi.org/10.1016/j.neuroimage.2023.119912)) compared existing methods for harmonisation on a unique dataset and found none of the methods to be satisfactory. They included statistical approaches based on "regressing out" confounding variation, a basic image processing approach using image intensity, and deep learning models.

This project aims to develop a novel harmonisation method that outperforms existing approaches for producing image-derived phenotypes (such as cortical thickness) relevant to disease progression modelling.


* * *

Vascular pathology and Parkinson's disease
======

with Sarah Al-Bachari and others at the [UCL Queen Square Institute of Neurology](https://www.ucl.ac.uk/ion/ucl-queen-square-institute-neurology).

Parkinson's disease (PD) is the second most common neurodegenerative disorder yet there are no disease modifying therapies available. PD is now rapidly being appreciated as a syndrome (collection of symptoms), encompassing significant heterogeneity in clinical measures and rates of progression, reflective of its complex and poorly understood biological basis, including effects of co-pathologies.

Vascular abnormality has been demonstrated in PD, with evidence that vascular pathology is associated with disease progression, greater motor disability, and cognitive decline. It is not yet known whether vascular abnormality is an integral part of disease pathophysiology or more related to comorbidity.

This project will involve analysing multimodal MRI and clinical symptom data to understand vascular pathology in PD cases and controls. Subsequently, advanced disease progression modelling approaches and large datasets will be employed to unravel the heterogeneity of vascular pathology in PD, e.g., using [SuStaIn](https://ucl-pond.github.io/pySuStaIn/) and [ENIGMA-PD](https://enigma.ini.usc.edu/ongoing/enigma-parkinsons/) data.

