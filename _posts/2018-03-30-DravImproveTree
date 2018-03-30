---
layout: post
title: Improving the quality of inferred Dravidian tree
categories: Dravidian
tags: [BI]
---

In this post, I will focus on improving the inferred Dravidian tree. Until now, the binary characters are modeling on loss or gain of cognates. In terms of historical linguistics, loss or gain of cognates is **lexical replacement** whereas, historical linguists also consider phonological divergence within cognate words. For instance, within cognates, sound change is an important aspect that can be used in calculating likelihood of a tree. Moreover, this step would increase the amount of information used to estimate the likelihood of a tree. I will use a method introduced by Gerhard Jäger in his [Global-scale phylogenetic linguistic inference from lexical resources](https://arxiv.org/pdf/1802.06079.pdf) paper.

In this method, a character is a Concept-Soundclass pair where each character is a pair consisting of concept and sound. For each language, a Concept-Soundclass pair is undefined (**?**) if there is no lexical item for that concept in the language. The character has a value of 1 if the sound class is present in the concept and 0 if the sound class is not present in the concept. The rationale for this approach is described in Jäger (2018) which I will quote here:

```
The Old English word for **dog** was *hund*, i.e., `hund` in ASJP transcription. It belongs to the automatically inferred cognate class dog_149. The Modern English word for that concept is dog/dag, which belongs to class dog_150. This amounts to two mutations of cognate-class characters between Old English and Modern English, 0 -> 1 for dog_150 and 1 -> 0 for dog_149.
The same historic process is also tracked by the sound-concept characters; it corresponds to seven mutations: 0 -> 1 for dog:d, dog:a and dog:g, and 1 -> 0 for dog:h, dog:u, dog:n and dog:d.
```

A sound class can be defined as mapping from fine grained phonemes (IPA) to coarse grained phoneme set (ASJP, SCA, Dolgopolsky) such that transition between phonemes belonging to the same sound class is more common than between different sound classes. A discussion on sound classes is given [here](http://media.leidenuniv.nl/legacy/console19-proceedings-list.pdf). In this post, I will use ASJP alphabet that is available [here](https://en.wikipedia.org/wiki/Automated_Similarity_Judgment_Program#ASJPcode). I used [LingPy](https://github.com/lingpy/lingpy) to convert the IPA forms to ASJP forms and then transformed ASJP forms to characters as described above.
