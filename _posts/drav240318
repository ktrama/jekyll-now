## My findings
In a recent [article](http://rsos.royalsocietypublishing.org/content/5/3/171504), Kolipakam et al. employed a Yule model (a birth-death model with no extinction) for lineage speciation and performed a Bayesian analysis which inferred that the Dravidian family's root age is 4500 years. The authors made the data available online. This allowed me to experiment if other tree priors infer similar dates. In fact, I find that the inferred root ages differ when I use different tree priors such as uniform prior, fixed population size coalescent prior or a more general birth-death prior. To determine the best tree prior I performed a model comparison using [AICM](http://bedford.io/pdfs/papers/baele-path-sampling.pdf) (Akaike Information Criterion through Monte Carlo Markov Chain). I find that the **best model is a coalescent prior that supports a root date that is 5000 years** and agrees quite well with Krishnamurti's estimate that Proto-Dravidian is about the early part of the third millenium. The uniform and birth-death priors support ages of 4600 and 3800 years respectively.

Moreover, if I remove the calibration date of South Dravidian group I, then, the median root age decreases to a lower age of _3570_ years (for coalescent), _2400_ years (for birth-death)  and _2000_ years (for uniform) respectively. **I take this as an evidence** that there might not be enough signal in lexical cognates to infer consistent dates across different tree priors.

The findings regarding the root ages are summarized below:
* The Birth-Death prior (where Yule is a special case) is not the best model for the Dravidian language family sample obtained from the paper. The uniform prior is as good as birth death prior in this case.
* Fixed population size coalescent prior (as used in this post) is the best model for Dravidian data.
* The estimated age of the Dravidian family is highly variable depending on the tree prior and parameter settings.
* The trees reported in this paper have **better agreement** with Krishnamurti's tree (Figure 1 in supplementary material)  than the topology of the best tree (figure 3) reported in the paper.

I present the experiment settings, inferred trees along with dates in the following sections. I find that **none of the inferred trees show dates that correlate with the calibration dates** of **Brahui, Kannada-Tulu, Telugu** used by the authors.

## Summary of previous work
I will summarize the article and claims here. The authors collected [Swadesh word lists](https://en.wikipedia.org/wiki/Swadesh_list) of length 100 for 20 Dravidian languages and assigned cognate judgments. Then, the authors used [BEAST](http://www.beast2.org/) software to infer trees and dates. The authors experimented with a number of settings such as substitution models, weighing the sites (each site is a cognate set) using discrete Gamma distribution and an individual weighting parameter for each concept. The third setting is computationally heavy since it introduces 100 extra parameters that needs to be estimated. I will use a simpler Gamma site rates model that weighs likelihood calculated from sites through a single parameter. The data is available [here](https://zenodo.org/record/1181715). The data consists of both IPA transcribed forms and cognate judgments that are readily available. I generated a [nexus](https://github.com/PhyloStar/dravidian-dating/blob/master/mpi_20_langs/drav.nex) file consisting of binary cognate judgments. 

## Substitution model
I use a GTR model for binary sites which is a [F81 model](https://en.wikipedia.org/wiki/Models_of_DNA_evolution#F81_model_(Felsenstein_1981)) and models the transition probability between state **0** and state **1** over some time **t**. 

## Tree prior
The authors use a Yule tree prior (a special case of birth death tree prior) in their analyses. I will use three different tree priors here. They are uniform, birth-death, and coalescent priors which are discussed below.
### Coalescent prior
The coalescent process is used to model the spread of genes in a population over time. Given two genes, the coalescent tree traces the relationship between two genes over time. The coalescent tree gives the solution to the question regarding how many generations do we have to go back to find the common ancestor of the two genes. 

Although, I am not aware of any direct analogy between gene spread and how cognate sets evolve, it seems that the main reason why coalescent prior is used in linguistic phylogenetics is the ease of implementation as compared to Birth-Death prior. I will explain birth-death prior below. A more general introduction to coalescent theory in the context of Bayesian phylogenetic inference can be found [here](http://www.oxfordscholarship.com/view/10.1093/acprof:oso/9780199602605.001.0001/acprof-9780199602605-chapter-9). The coalescent prior has a population size parameter **N** that is either fixed or variable depending on the model used. For instance,  [Bouckaert et al.](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4112997/)'s Indo-European paper uses a Skyline prior where the population size is allowed to vary in fixed number of intervals that is also used by  [Chang et al.](https://www.linguisticsociety.org/sites/default/files/news/ChangEtAlPreprint.pdf). 


### Uniform prior
[Uniform prior](https://academic.oup.com/sysbio/article/61/6/973/1665823) is developed by Ronquist et al.. The uniform tree prior assumes that the internal node ages are drawn from an uniform distribution and that the root age is conditioned on a prior. The uniform prior is a Phenomenological prior and does not make explicit assumptions about the process that generates the tree.

### Birth death prior
The birth death prior is a different tree prior that models lineage diversification between samples belonging to different species. A lineage or a branch can speciate with rate Lambda (read as Greek letter) and become extinct with rate Mu. Moreover, the probability of a tree generated under birth-death process is also conditioned on the number of species or languages in the sample. In a [standard birth-death tree](https://www.ncbi.nlm.nih.gov/pubmed/9214744) birth-death tree, the all the tips are extant and extinct languages cannot be represented on the tree. For  instance,  Hittite went extinct without leaving a modern descendant. On the other hand, Old English is the ancestor of Modern English and is represented as an internal node with one incoming branch and one outgoing branch that leads to Modern English.

In a recent paper, [Tanja Stadler](https://www.ncbi.nlm.nih.gov/pubmed/20851708) extended the standard birth death tree that can handle the extinct languages such as Hittite or Sanskrit. This model is conditioned on the root age of the tree and also has an extra parameter called Psi which the rate of sampling extinct languages. I will use this tree prior in this paper. Since there are no extinct Dravidian languages in the sample, I will simply fix Psi to **0** and proceed with inference.

The Yule prior used by Kolipakam et al. is a special case of birth-death prior where the death rate is **0**. I find, using a birth-death prior, that the data supports a death rate (mu = 0.0003049) that is greater than zero. 

## Tree calibration
Now, I will discuss about calibration points that are required to date the tree. Kolipakam et al. listed the following topological constraints and calibration points. A topological constraint tells the tree inference software to assign zero probability to any tree that does not respect the constraint.

### Topological Constraints
The topological constraints are listed below. The below constraints are uncontroversial and are derived from comparative Dravidian literature.
* North: Brahui, Kurukh, Malto
* South I: Badga, Betta Kurumba, Kannada, Kodava, Kota, Malayalam, Tamil, Tulu, Toda, Yeruva
* South II: Gondi, Koya, Kuwi, Telugu

### Calibration dates
On the other hand, the calibration points are listed below:
* Root age is between 0-10000 years.
* South I group is 2250 years based on the evidence that the earliest Tamil inscription is found around 250 BCE.
* Tamil-Malayalam split happened between 800-1200 years based on historical evidence.
* Brahui is supposedly 2250 years old. The calibration point is derived due to supposed contact between North Dravidian subgroup and Magadhi Apabrahmsa (a earlier stage of Eastern Indo-Aryan languages) which was spoken between 200-500 CE. I did not understand how this number corresponds to 2250 years. I **will not use this calibration due to the uncertainty** behind the date.
* Telugu is 1400 years old which is derived from the earliest inscription dating back to 620 CE. At least from the BEAST xml file, it seems that Telugu is given a date that is between 1400 to 10000 years which is strange since Telugu is not extinct of which I am a native speaker of. At best, one can say that South II group cannot be younger than 1400 years since this is similar to the calibration date derived for South I group based on Tamil. **I will not use this date also.**
* Kannada-Tulu split is supposed to be 1300 years. This date comes from the first Kananda inscription that is dated to 450 CE. Then, somehow, the authors arrive at a date of 1300 years that is not transparent from the text. **I will not use this date due to the same reason as Telugu.**

Therefore, I will use three topological  constraints and three calibration dates for Root, South I, and Tamil-Malayalam split which are uncontroversial in my analyses. I will use uniform prior for the three calibration dates in all the analyses. For instance, the prior distribution for the root age is a uniform distribution with 0 and 10000 years as bounds.

## MCMC Analysis
I will use [MrBayes](https://arxiv.org/abs/1603.05707) that is available [here](https://github.com/PhyloStar/mrbayes-coal/tree/master/mrbayes-3.2.6). I ran MrBayes for three different tree priors with all the other parameter settings kept invariant. I ran the software for two independent runs with each run consisting of a cold chain and three hot chains which allow the cold chain to explore the tree landscape that might consist of multiple peaks. I ran the chain for 5 million states in the case of coalescent prior and ten million states in the case of birth-death and uniform tree priors and sampled every five hundredth state.  Both the independent runs showed an average standard deviation of split frequencies less than 0.01 in all the cases. I threw away initial 25% of the states as part of burn-in. Then, I summarized the trees using majority consensus method. For relaxed clock settings, I use a Independent Gamma rates model where each branch rate is sampled from a  Gamma distribution.

## Results
The consensus trees are shown below for each tree prior. The root age is 3864 years that is below 4000 years in the case of Birth-death tree. In the case of uniform tree, the root age is about 4618 years. Finally, the coalescent prior shows a root age that is 5000 years. The root ages seem to fluctuate a lot between 3860 to 5000 years for a language family's sample that is small and has small number of cognate sets.

### HPD and Median ages
I will now look at the highest posterior density ([HPD](http://beast.community/glossary.html)) ranges of root ages for each sampled tree. The HPD and median root ages from the sampled trees are presented below. The results show that even the sampled trees show quite different root ages.

Tree Prior| HPD | Median Age| AICM
---|---|---|---
Birth-Death|2445-5993|4042|8361.057
Uniform|2723-7203|4573|8361.936
Coalescent|2821-7524|4964|**8359.807**

The best tree prior can be determined by calculating [AICM](http://bedford.io/pdfs/papers/baele-path-sampling.pdf) (AIC through MCMC) for 100 bootstrap replicates on the posterior samples. The AICM values are given in table and are very close to each other. The best model is the coalescent tree prior that infers a date close to 5000 years.
 
### Birth-Death tree
![Birth-Death consensus tree](https://github.com/PhyloStar/dravidian-dating/blob/master/mpi_20_langs/dravBirthdeath.con.tre.png)

### Uniform tree
![Uniform consensus tree](https://github.com/PhyloStar/dravidian-dating/blob/master/mpi_20_langs/dravUniform.con.tre.png)

### Coalescent tree
![Coalescent consensus tree](https://github.com/PhyloStar/dravidian-dating/blob/master/mpi_20_langs/dravCoal.con.tre.png)

## Conclusion about inferred phylogenies
* All the tree priors infer quite similar tree topologies. This is not surprising due to the small number of languages and relatively less number of cognate sets when compared to families like Indo-European or Austronesian.
* I also attempted to check if any of the phylogenies showed agreeing dates for the three excluded calibration points. 
    * **Telugu** is shown to have a younger date than 1400 years in case of all the priors.
    * **Brahui** does not show any date in the range of 2250 years in case of all the priors.
    * **Tulu** is the first language to split off from South I in all the cases agreeing with what is known in historical linguistics. However, none of the Tulu split dates confirm with the calibration dates derived and employed by Kolipakam et al.

## Supplementary material
* [Script](https://github.com/PhyloStar/dravidian-dating/blob/master/mpi_20_langs/run.mb) for running MrBayes analysis. 
