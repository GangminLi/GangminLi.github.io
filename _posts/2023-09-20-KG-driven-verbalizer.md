---
title: "Injecting Commonsense Knowledge into Prompt Learning for Zero-Shot Text Classification"
style: app
date: 2023-09-20 10:12:20

author_profile: true
toc: true
toc_label: "Page Content"


tags:
  - AI models
  - Prompt Engineering
  - Text clasification
  - Knowledge graph
  - Classification
  - Verbakizer
  - Zero-shot training


header:
  teaser: "/assets/posts/KG-verbalizer/ProtoVer.jpg"
---
![publication](/assets/posts/KG-verbalizer/publication.jpg)
![Langague](/assets/posts/KG-verbalizer/injection.jpg)


# What is it about?
In this paper, we propose the KG-driven verbalizer, a novel approach to bridge the gap between the label word space and the class label space based on their in-between semantic relatedness. Our verbalizer is not handcrafted or trained, but automatically built and embedding-based. Commonsense knowledge is integrated into our approach because the semantic similarity is measured in a hybrid vector space that is an ensemble of word2vec, GloVe and ConceptNet-PPMI. We test the validness of our approach in the task of zero-shot text classification upon a humanitarian aid-related tweet dataset. Satisfactory results are achieved, which proves the effectiveness of the KG-driven verbalizer.

[![Read the artical](/assets/posts/KG-verbalizer/read.jpg)](https://dl.acm.org/doi/10.1145/3587716.3587787)


# Why is it important?

The combination of pre-training and fine-tuning has become a general paradigm for handling Natural Language Processing (NLP)tasks. This approach needs two preconditions large training datasets and high configuration of the training environment. it is not applicable in scenarios like classification under low data resources. Insufficient labelled data or even unseen classes. Ver-balizer, supports pre-trained Language Models (PLMs) with task-specific prompts can effectively solve the problem. We propose a KG-driven verbalizer that leverages commonsense knowledge to con-struct the embedding-based correspondence between label words and classes. Specifically, we transform the in-between projection into semantic relevance in the commonsense-injected embedding space. For zero-shot text classification, experimental results exhibit the effectiveness of our KG-driven verbalizer on HumAID dataset compared with other baselines.

# Perspectives

![perspective](/assets/posts/KG-verbalizer/perspective.jpg)



<p>
{% include  share.html %}
</p>

<span style="color:#9e9696"><i> Last updated: 20/09/2023</i> </span>

<p>
{% include  license.html %}
</p>