---
layout: post
title: Meta-Analysis of Research
subtitle: Analyze Datasets and Critically Examine Scientific Studies
tags: [homework, discussion]
comments: true
---

# Summary of the Research Paper 

The study I examined was  “Detection of subjects and brain regions related to Alzheimer's disease using 3D MRI scans based on eigenbrain and machine learning,” by Yudong Zhang, Zhengchao Dong, Preetha Phillips, Shuihua Wang, Genlin Ji, Jiquan Yang, and Ti-Fei Yuan. The goal of this study was  to create an algorithm to make accurate diagnosis of Alzheimer's disease (AD) using MRI scans. These researchers proposed and experimented with a unique method: a novel CAD system for brain MRIs based on eigenbrains and machine learning. In this study, the researchers used maximum inter-class variance (ICV) to select key slices from 3D volumetric data, and generated an eigenbrain set for each subject. Then, the most important eigenbrain (MIE) was obtained by Welch's t-test (WTT). Finally, different classification models were used to train the accurate algorithms. All three classification models the researchers included in this study yielded algorithms that were competitive with existing studies. The most accurate was the algorithm trained using a polynomial kernel which reached 92.36 ± 0.94%. The study concluded that the eigenbrain method was effective in AD detection. This is the [link](https://www.frontiersin.org/articles/10.3389/fncom.2015.00066/full#h8) to the article

# Analysis of the Dataset

### Questions I Asked and Answered Myself

*   Which properties are being tracked?

    The OASIS dataset tracks the patient’s brain MRI and PET imaging as well as their dementia and Apolipoprotein E (APOE) status and other characteristics such as age, favored hand, race etc. 

*   Which properties are being left out?

    The properties tracked in this dataset suffice and no important properties are left out. 

*   Which data points make it to the final dataset?

    Although there are many imaging sessions, some images do not have a corresponding numerical data that keep track of dementia and APOE status. For this study, only those images would not be used in training the algorithms. 

*   What incentives are driving people to collect this data?

    The goal of this dataset is to make neuroimaging of the brain freely available to the scientific community, thus sparking future discoveries in basic and clinical neuroscience.

*   How was this data collected?

    The data was collected when patients participated in several ongoing studies in the Washington University Knight Alzheimer Disease Research Center over the course of 15 years.
    
*   Who is funding the collection of this data?

    Although the dataset’s official website did not specify the group or individual funding the collection of this data, I would assume that an ongoing study that lasted as long as 15 years has a stable source of funding. 

*   How accessible is this dataset?

    This data set is open to the public. To access this dataset, one only needs to sign up in a form. 
