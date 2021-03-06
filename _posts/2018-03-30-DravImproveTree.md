---
layout: post
title: Sound change characters improves the quality of Dravidian trees
categories: Dravidian
tags: [BI]
---

In this post, I will focus on improving the inferred Dravidian tree. Until now, Dravidian trees are inferred using binary characters that model loss or gain of cognates. In terms of historical linguistics, loss or gain of cognates is **lexical replacement** whereas, historical linguists also consider phonological divergence within cognate words. For instance, within cognates, sound change is an important aspect that can be used to calculate likelihood of the tree. Moreover, this step would use more information in a wordlist to estimate the likelihood of a tree. I will use a method introduced by [Gerhard Jäger](http://www.sfs.uni-tuebingen.de/~gjaeger/) in his [Global-scale phylogenetic linguistic inference from lexical resources](https://arxiv.org/pdf/1802.06079.pdf) paper.

Performing inference with sound change information improves both the quality of the tree by 20% in terms of GQD. Qualitatively, the tree shows the North Dravidian split clearly and also shows South-Dravidian I and II together and also Central group (without Kolami) as a separate group. The hallmark of the tree is that it agrees largely in many aspects with both Krishnamurti and Glottolog. Moreover, the branches are present in more than 50% of the 7500 trees inferred in both the runs. 

Moreover, the inference also lowers the upper boundary of the HPD interval of the root age to 5300 years and places the median root age at 3700 years lowering the previous age estimate by 800 years.

## Quality of the inferred trees

In a previous post, I used different tree priors to infer trees.  I evaluated those inferred trees against gold standard and report the Generalized Quartet Distances (GQD) below. Note that these results are only with cognate sets. I only reported the GQD value for Birth-Death trees since I perform experiments with Birth-Death tree. Moreover, the scores for coalescent and uniform trees are very similar the numbers reported below.

Tree| GQD| No. of Trees
---|---|---
Birth-Death| 0.2685± 0.0275| 10001

As mentioned previously, the quartet distances are quite high and not within the observed range of Indo-European or Austronesian. How to improve the quality? One way is to add sound change information such that the inferred tree quality improves.

## Concept-SoundClass characters

In this method, a character is a Concept-Soundclass pair where each character is a pair consisting of concept and sound. For each language, a Concept-Soundclass pair is undefined (**?**) if there is no lexical item for that concept in the language. The character has a value of 1 if the sound class is present in the concept and 0 if the sound class is not present in the concept. The rationale for this approach is described in Jäger (2018) which I will quote here:

>The Old English word for **dog** was *hund*, i.e., `hund` in ASJP transcription. It belongs to the automatically inferred cognate class dog_149. The Modern English word for that concept is *dog/dag*, which belongs to class dog_150. This amounts to two mutations of cognate-class characters between Old English and Modern English, 0 -> 1 for *dog_150* and 1 -> 0 for *dog_149*. The same historic process is also tracked by the sound-concept characters; it corresponds to seven mutations: 0 -> 1 for **dog:d, dog:a and dog:g**, and 1 -> 0 for **dog:h, dog:u, dog:n and dog:d**.


A sound class is defined as mapping from fine grained phonemes (IPA) to coarse grained phoneme set (ASJP, SCA, Dolgopolsky) such that transition between phonemes belonging to the same sound class is more common than between different sound classes. A discussion on sound classes is given [here](http://media.leidenuniv.nl/legacy/console19-proceedings-list.pdf). In this post, I will use ASJP alphabet that is available [here](https://en.wikipedia.org/wiki/Automated_Similarity_Judgment_Program#ASJPcode). I used [LingPy](https://github.com/lingpy/lingpy) to convert the IPA forms to ASJP forms and then transformed ASJP forms to binary characters as described above.

##  Results

This step yields an extra 1798 characters that I will analyze as a separate partition. Therefore, I have two partitions, one partition is made up of cognates and the other partition is made up of characters that model sound change. I employed a birth-death tree prior and four-category discrete gamma distribution to weight the sites within each partition. I use a F81 model of substitution within each partition. As before, I ran two independent MCMC runs for 5 million iterations and summarized a run using majority consensus tree. The result is here:

[tree](https://github.com/ktrama/ktrama.github.io/blob/master/_files/dravPartition.con.tre.pdf)

I evaluated the posterior sample of trees using GQD. The average GQD decreases to **0.2154±0.0199** which is about 19.77% improvement over the birth death tree that is inferred only with cognate classes.

The median root age is 3700 years with 95% HPD interval ranging from 2446 years to 5346 years whereas the authors of the paper report a age range of 3000-6500 years.

I will now describe how the subgrouping quality improved over both the published tree and the birth death tree I reported [previously](https://github.com/ktrama/ktrama.github.io/blob/master/_files/dravBirthdeath.con.tre.pdf).

### Comparison
I compare the majority consensus tree with gold standard tree (Glottolog tree) and find the following improvements.

* North Dravidian subgroup is the first to split off.
* Gondi-Koya come out as siblings which never comes out right.
* South Dravidian II group comes up right agreeing with the gold standard tree.
* Betta-Kurumba comes out along with Kodagu as given by Krishnamurti
* Kannada comes out right after Tulu.

All the major splits occur with high probabilities in the posterior sample.

### Shortcomings
* Badaga, Kannada, Yeruva comes out seprately in the tree and not together which causes the South Dravidian I group to be not in agreement with Glottolog tree.
* Kolami does not come out together with the Central group

The tree I posted here is much better than the published tree and comes out closer to the glottolog tree.

### Outlook

I could have constrained Central group also. However, I did not choose to do so since, I am interested in following Kolipakam et al. as closely as possible. I do not know of any reason why the authors did not constrain Central Dravidian. In any case, if I constrained the whole tree then the root age changes very much dependending on the oldest calibration point.

