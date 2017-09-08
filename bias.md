[Back to Conversation AI Research Overview](index.md)

This page introduces the concepts of unintended bias in machine learning and the fairness challenges to making machine learning help online conversations at scale. If you want to know more about the machine learning terms used in this page, have a quick read of [our introduction to ML](ml_intro.md).

## Unintended Bias in Machine Learning

The goal of every machine learning model is to be biased: but in the way you want it to, for example to recognise kittens a model is kitten-biased. But machine learning models are often biased in unintended ways too. You can find [a quick introduction to ML and human bias on YouTube](https://youtu.be/59bMh59JQDo). Unintended bias tends to come from skewed or incomplete training data. In text classification, this typically happens because of:

 * *Gaps in the training data*: for example, there are few outright threats of violence posted to wikipedia comments. Thus machine learning algorithms trained on only wikipedia comments will not be good at identifying them.

 * *A biased annotator population*: for example, if the population of people creating the training data is skewed toward a particular political orientation, then one might imagine that the annotators will not consider attacks on their political opponents as toxic.

We want our models support conversations being more inclusive and allow more points of views to be shared. But unintended biases might lead to application inadvertently doing the opposite. An interactive visualization that explore the risks and impact of bias can be found at the site of [Attacking discrimination with smarter machine learning](https://research.google.com/bigpicture/attacking-discrimination-in-ml/). Many good further resources are maintained on the [FAT ML community resoure page](http://www.fatml.org/resources/relevant-scholarship).

## Are the models biased? in what ways?

So the real question about our models is not whether they have unintended biases, but in what ways are they biased, how much, and what impact does the unintended bias then have? But even the concept of unintended bias is not easy to define:

 * What dataset do you use? For text classification there are an infinite number of examples out there, so you have to choose. Finding bias might just mean that you chose a biased test set, and that actually the model is fair in the errors it makes, but you've only looked at some of them. 
 
 * There are several different concepts for what it means for a machine learning model to be fair, which are not necessarily compatible, as demonstrated in [Inherent Trade-Offs in the Fair Determination of Risk Scores](https://arxiv.org/abs/1609.05807).

 * Carrying out a particular analysis that fails to find bias does not mean it is not there. Maybe other methods or additional data might still find bias. There is no conclusive test for a model not having an unintended bias.

For our text classification problems, a natural notion of unintended bias is that the model treats different groups of people differently, for instance by failing to recognize toxic attacks targeting a particular communities. A natural starting point here is to consider groups who are frequently targeted (e.g. [protected classes](https://en.wikipedia.org/wiki/Protected_class)).

A second form of unintended bias we want to avoid is with respect to the topic: we want to support conversations on any topic. We consider our model topic-biased when it over or under triggers significantly more when being evaluated on conversations concerning that topic.

## Why is identifying bias in models difficult?

Identifying bias in the annotators who creating the training data is challenging because we typically know little about the annotators, and even less about whether the wider population would make the same judgements. One also has to respect the annotator's privacy, limit the amount of questions asked, but still try to identify if one subset of annotators judgements differ from the wider population. A frequent proposal is to start with basic demographic information, but even getting accurate demographic information from crowdsourcing platforms is difficult: annotator demographic are rarely known at the outset, necessitating annotators self reporting via surveys.

Even if the crowdworkers are perfectly representative of the wide population in their judgements, the raw data they are rating may be insufficient and thus suggest false correlations. For example, if all comments that mention sexuality are in fact examples of personal attacks, then the training of a machine learning algorithm will likely result in a model that believes any discussion of sexuality is itself toxic. Depending on how such a machine learning model is applied, it might then inadvertently prohibit constructive and important conversations on that topic. This challenge is compounded by the difficulty of even defining the concept of ‘topic’, which is itself a topic of significant focus in machine learning research. And like identifying bias that might stem from crowdworkers not being representative of the wider population, failure to find a bias related to a topic only means that the method used to find it failed.

Finally, the challenges of topic and crowdworker selection biases may intersect: how toxic a comment is perceived by annotators may depend on both the annotator and the topic.

## What can we do about it?

Understanding and mitigating unintended bias requires analysis and scrutiny from an many perspectives. This is one of the key motivations for [opening access to an API that hosts models](https://www.perspectiveapi.com/) and creating public datasets like [our Wikipedia datasets](https://meta.wikimedia.org/wiki/Research:Detox/Data_Release). These tools support others researchers to join the effort to understand and address bias in machine learning.

Unintended bias in our models is an active area of research and we welcome 
[involvement in the WikiDetox Wiki pages](https://meta.wikimedia.org/wiki/Research:Detox) and via
[Conversation AI research projects on github](https://conversationai.github.io/).
You can find more about the tools and analysis methods we are exploring to migite
unintended bias in our 
[unintended ml bias anlysis github project](https://github.com/conversationai/conversationai-bias-analysis).
