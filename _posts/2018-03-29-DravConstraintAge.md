---
layout: post
title: Is one calibration point enough to push the root age of a family?
categories: Dravidian
tags: [BI]
---

In a previous blog post [1](https://ktrama.github.io/DravAgeRange/) I experimented and found that there is not much signal in the lexical data to infer the right tree and that the root age keeps fluctuating with choice of tree prior. The tree prior choice is not relevant in terms of AICM but makes difference in median ages of the family. The consensus tree inferred in my analysis is **closer to the tree found in Dravidian comparative literature** than the published tree. Moreover, none of my trees show support for three calibration points posited by the authors which relate to the terminal taxa (Brahui, Telugu, Kannada-Tulu).

I performed a non-dating study in [2](https://ktrama.github.io/DravGQD/) I tested if the tree inferred from lexical cognates is as good as gold standard tree by not performing any dating. In other words, I only verified the accuracy of the topology of the inferred trees. I will do the opposite in this post. I will not infer topology but fix the topology and infer ages on the topology.

The experiments are very restricted in nature. I will constrain the tree search to infer the same tree as Glottolog Tree (figure 2 in supplementary material of [article](http://rsos.royalsocietypublishing.org/content/5/3/171504)). In such a case, the inference consists of sampling tree ages (and polytomies in gold standard tree) and model parameters such as birth rate, death rate, substitution model parameters, and clock parameters.

I will demonstrate that a single calibration point of South Dravidian I subgroup can increase the median root age by more than 1000 years. I will add the following constraints:

```
north = Brahui Kurukh Malto;
maltoKurukh = Kurukh Malto;
central = Ollari_Gadba Parji Kolami;
gadabaParji = Ollari_Gadba Parji;
south1 = Badga Toda Kota Betta_Kurumba Tamil Malayalam Yeruva Kodava Tulu Kannada;
exclTulu = Badga Toda Kota Betta_Kurumba Tamil Malayalam Yeruva Kodava Kannada;
exclTuluLeft = Badga Yeruva Betta_Kurumba Kannada;
kannadaDial = Yeruva Betta_Kurumba Kannada;
exclTuluRight = Kota Toda Kodava Tamil Malayalam;
exclTuluRightKota = Toda Kodava Tamil Malayalam;
exclTuluRightKotaToda = Kodava Tamil Malayalam;
TamMal = Malayalam Tamil;
south2 = Gondi Koya Kuwi Telugu;
gondiKoya = Gondi Koya;
south = Badga Toda Kota Betta_Kurumba Tamil Malayalam Yeruva Kodava Tulu Kannada Gondi Koya Kuwi Telugu;
```
The above set of constraints are equivalent to the Glottolog tree and is also very similar to the Krishnamurti's tree. I will add two calibration points TamMal which is Tamil-Malayalam divergence date drawn from a bounded uniform distribution. South1 date comes from the Article of Kolipakam et al. which essentially is a lower bound on the age of South Dravidian I subgroup. Note that South Dravidian I date is the oldest calibration date among the calibration dates used in the published study. In contrast, in a older [post](https://ktrama.github.io/DravLSI/), I used the date that the root age of Dravidian has to be at least 3500 years which comes from Krishnamurti and is linked to contact between Rigvedic speakers and Dravidian speakers.

```
TamMal = uniform(800,1200)
south1 = uniform(2250,10000)
```

I ran two independent runs with four chains in each run. One chain is cold and the other three chains are hot in the MCMC. The chains are run for 10 million states and I sampled at every 1000th state and report the results.

The consensus tree for this particular analysis is given [here](https://github.com/ktrama/ktrama.github.io/blob/master/_files/dravFixedGlottConsSouth1.con.tre.pdf)

The median root age is about 4214 years and is quite close to what the authors inferred. As before, I am using a birth-death prior and I infer a non-zero death rate from the data. 

In the next step, I will remove the South Dravidian I calibration date and rerun the whole analysis. Every other parameter's priors are kept constant. What happens now? The consensus tree is given [here](https://github.com/ktrama/ktrama.github.io/blob/master/_files/dravFixedGlott.con.tre.pdf)

The median root age is 3068 years in this tree. **Suddenly, the whole tree is shifted right on time scale showing a lower root age.**

Is there any parallel in biology for this kind of shifts in dates? The answer is **yes**. A [paper](https://academic.oup.com/sysbio/article/61/6/973/1665823) by Ronquist et al. shows how dates can shift due to different dating strategies. I will quote what the authors say here:

```
First, the calibration data must be associated with fixed nodes in the tree, despite the fact that we do not know any
of the nodes with absolute certainty. This may result in artifacts in the dating analysis, such as exaggerated
confidence in the tree topology and the resulting age estimates. To avoid constraining the tree, one can attach
the calibration information to the most recent common ancestor of some named terminal taxa instead. If there
is topological uncertainty, however, this results in the calibration information floating around in the tree in a
manner that is unlikely to reflect the uncertainty in the placement of the calibration fossil.
```
Is there any explanation for the observation regarding the large shift in ages? I think that the amount of change in cognates does not correlate with the time passed since the first attestation of Tamil inscription. In other words, there is not enough change in lexical cognates to support the calibration point independently.
