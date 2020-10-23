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

After reading the [OASIS dataset website](https://www.oasis-brains.org/#access) I would regard the OASIS dataset as a good dataset. One the website, there are three different datasets (OASIS-1, 2, and 3) For OASIS-1 and 2, I noticed that all the patients are right-handed. Although preferred hand is not really related to dementia, it can still be a coverage bias. For OASIS-3, a newer dataset, both right-handed and left-handed patients are included. A paper regarding the OASIS-3 dataset can be found [here](https://www.medrxiv.org/content/10.1101/2019.12.13.19014902v1.full.pdf). In the paper, the data in OASIS-3 is interpreted in depth. In a detailed demographics chart, out of a total number of 1098 subjects, 926 subjects were Caucasian, 168 subjects were African-American, and 5 subjects were Asian, which is neither representative of the world population demographics nor the United States population demographics. But on the other hand, the goal of this dataset is to spark studies to tackle dementia and Alzheimer’s Disease. I think the three OASIS datasets achieve that goal. Moreover, after conducting more research on this problem set, I discovered that this dataset is one of the most used datasets in this field.

#Analysis of the Research Paper
This specific study follows the strict scientific method: background (observations, questions, research), hypothesis, experiment, analysis, and conclusion. The researchers who conducted the research and wrote up the paper are professors from well-known universities in China and in the United States. The paper has 12517 views, better than 94% of all articles on the site; 4330 downloads, better than 98% of all articles on the site; and is cited by 66 other articles, better than 98% of all articles on the site. All of the above build towards the credibility of the research paper. 

For this study, there is minimal room for p-hacking. First, the dataset that is used in this study has a large number of subjects. Second, Welch's t-test is implemented on all the key slices on the six eigenbrains. Only the first eigenbrain has all the key slices with p-values less than 0.05. Therefore, the study claims that the first eigenbrain is the most important. The p-values of the other slices in eigenbrain 2 to 5 are significantly larger. The researchers trained algorithms, using three different classification models to train with the OASIS dataset, and obtained a recognition accuracy of 92.36 ± 0.94, very competitive compared to related work. 


Although the study appears strong and has been cited many times, it is certainly possible that the researchers use the training dataset as part of the testing dataset to give the recognition accuracy a boost in order to yield a sensational result. Given that the dataset is so well-known and understood by researchers in this field, the researchers of this study might be able to tweak the dataset to yield the result they wanted in determining the most important eigenbrain. This study also lacks replication studies. However, related studies (with similar models) have obtained similar recognition accuracy. It would be useful if the researchers disclosed the code used in this project for readers or reviewers to look at. But overall, I think this study is trustworthy.