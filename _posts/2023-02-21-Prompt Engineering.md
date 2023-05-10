---
title: "Prompt Engineering"
style:  app
date: 2023-02-21 10:12:20

author_profile: true
toc: true
toc_label: "Page Content"


tags:
  - Prompt Engineering
  - OpenAI
  - GPT3
  - AI
  - NLP

  

header:
  teaser: "/assets/posts/openai/pe.jpg"
---
![Langague](/assets/posts/prompt/brooks.jpg)

## Introduction

Prompt engineering refers to the process of designing user interfaces or systems in a way that prompts or guides users towards taking specific actions or making certain decisions. This can be achieved through various design elements such as colors, layout, language, and the placement of buttons or menus.

Prompt engineering is a concept in artificial intelligence, particularly natural language processing (NLP). In prompt engineering, the description of the task is embedded in the input, e.g., as a question instead of it being implicitly given. Prompt engineering typically works by converting one or more tasks to a prompt-based dataset and training a language model with what has been called "prompt-based learning" or just "prompt learning". Prompt engineering may work from a large "frozen" pretrained language model and where only the representation of the prompt is learned (i.e., optimized), using methods such as "prefix-tuning" or "prompt tuning".

Fundementally, it is a clever or efficent way of creating an input that AI models can understand and perform the tasks you desired.

## Prompt Engineering in GPT-3

Different language models are created to do different NLP and ML tasks such as classification, summarization, translation, question answering, etc. Basically, a statistical language model(Language Model) uses a probability distribution over word sequences assigns a probability P to the entire series given a sequence of length m. The language model gives context for distinguishing between phonetically identical words and phrases. Each year a number of new language models are evolving by creating a new benchmark. The number of parameters is also increasing in each model. GPT-3 adds **175 billion parameters** to the GPT-2 design, as well as altered initialization, pre-normalization, and configurable tokenization. It displays strong performance on a variety of NLP tasks and benchmarks in three different scenarios: zero-shot, one-shot, and few-shot. Among that one-shot learning and few-shot learning, the user needs to provide some expected input and output of the specific use-case to the API. After that, the user needs to provide a sample trigger to generate the required output. This trigger is called the prompt in GPT-3.  In GPT-3’s API, a ‘prompt‘ is a parameter that is provided to the API so that it is able to identify the context of the problem to be solved. Depending on how the prompt is written, the returned text will attempt to match the pattern accordingly. The below graph shows the accuracy of GPT-3 with prompt and without prompt in the models with different numbers of parameters. From this chart, we can clearly identify the importance prompt based modeling in GPT-3.
![GPT3 few shot learner](/assets/posts/prompt/gpt3-triger.jpeg)
*https://medium.com/analytics-vidhya/openai-gpt-3-language-models-are-few-shot-learners-82531b3d3122*

Create different prompt is called **"Prompt Engineering"**. Prompt engineering is an interesting way to interact with GPT-3 and creating clever text-based scripts that make GPT-3 perform the tasks you desire. The process is more like to coach athletes: you tell them what they should do and hopefully you’ll get the result you want. And just like in sports, you won’t always get the desired result from GPT-3.

## How to create prompts for different tasks?

From creating original stories to doing intricate text analysis, GPT-3 can do it all. Because they can accomplish so many things, you must be specific in your instructions. A excellent prompt generally relies on showing rather than telling. 

Prompt creation follows three main guidelines:

- **Show and tell:** Make your intentions obvious by using instructions, examples, or a combination of the two. If you want the model to rank a list of items in alphabetical order or to classify a paragraph by sentiment, show it that's what you want.

- **Provide quality data:** Make sure there are enough samples if you’re trying to develop a classifier or get the model to follow a pattern.  The model is usually smart enough to see through basic spelling mistakes and give you a response, but it also might assume this is intentional and it can affect the response.

- **Check your settings:** The top_p and temperature settings determine how predictable the model is in providing a response. If you're asking it for a response where there's only one right answer, then you'd want to set these lower. If you're looking for more diverse responses, then you might want to set them higher. The number one mistake people use with these settings is assuming that they're "cleverness" or "creativity" controls.

## Prompt engineering use GPT3 playground
Let us use GPT3 playground to show how prompt engineeering can be done for text classification task. 
**Prompt**

``` 
TThe following is a list of persons. tell me what are they famous in:
Aamir khan, Elon musk, Virat Kohli, Rahul gandhi, Andrey kurkov, yaoming, Chritan Ronaldo

Aamir Khan - Actor
Elon Musk - Entrepreneur
Virat Kohli - Cricketer
Rahul Gandhi - Politician
Andrey Kurkov - Author
Yaoming - Basketball Player
Cristiano Ronaldo - Football Player

```
It's worth noticing the features in this example:
Use plain language to describe your inputs and outputs. We use plain language for the input "list of persons" and the expected output "they famous in" As a best practice, start with plain language descriptions. While you can often use shorthand or keys to indicate the input and output, it's best to start by being as descriptive as possible and then working backwards to remove extra words and see if performance stays consistent. This is the perfect example of zero-shot classification. That is system is classifying the names based on its own trained world knowledge. We are not providing any sample examples to train the system.

let us see example of few-shot learning.  We need to extract some entities from a passage. So we are feeding some examples to the system and training the system to learn from those few examples. The ### token is used to differentiate between different training examples. Finally, the testing sentence will be given and the system will be able to extract the entities from the text. We can modify/alter the outputs by changing the configurations like temperature, Top p..etc showing at the right side panel of the window. 

*GPT-3 Playground image*
 ```
 [text]: Fred is a serial entrepreneur, Co-founder, and CEO of the platform.sh, previously co-founded commerce guys, a leading drupal e-commerce provider. his mission is to guarantee that we continue on an ambitious journey to transform how cloud computing is used and perceived profoundly. we keep our feet well on the ground continuing the rapid growth we have enjoyed up until now.
[name]: Fred
[position]: co-founder and CEO
[company]: platform.sh 
###
[text]: SpaceX is an aerospace manufacturer and space transport services company headquartered in California. It was founded in 2002 by entrepreneur and investor Elon Musk with the goal of reducing space transportation costs and enabling the colonization of Mars.
[name]: Elon Musk
[Position]: Entrepreneur and investor
[company]: SpaceX
###
[text]: Mark Zuckerberg is one of the founders of Facebook, a company from the United States.
[name]: Mark Zuckerberg
[Position]:  co-founder
[company]: Facebook
###
[text]: David Melvin is an investment and financial services professional at CITIC CLSA with over 30 years of experience in investment banking and private equity. he is currently a senior advisor of CITIC CLSA. 
```
here is the output:
![GPT-3 Playground image](/assets/posts/prompt/gpt3-playground_1.png)
  
## Build your own prompt engineering platform
We can try to do prompt engineering use openA API. A convinient way is use OpenAI Python Library.  The OpenAI Python library provides convenient access to the OpenAI API from applications written in the Python language. It includes a pre-defined set of classes for API resources that initialize themselves dynamically from API responses which makes it compatible with a wide range of versions of the OpenAI API.

here are the basic steps:

- Signup into the openAI platform to get an API key.
- Use openAI python wrapper library
- setup environment parameters
- add your training data 
- Call OpenAI API 

## Summary
From creating original stories to doing intricate text analysis, openAI GPT-3 can do it all. Because they can accomplish so many things, you must be specific in your instructions. Various NLP tasks such as text classification, text summarization, sentence completion, etc can be done using GPT-3 by prompting. An excellent prompt generally relies on showing rather than telling. 

Prompt creation follows three main guidelines:

**Show and tell, Provide Quality data,** and **Change settings.** 

Along with that, we can get the outputs in three ways

- Zero-shot learning: Where no examples are given for training.

- One-shot learning: Here only one example is provided for the training purpose

- Few-shot learning: Where we can provide a few examples to train the model along with the prompt.

GPT-3 is not open source yet and is only available via the openAI API. Here some examples in the GPT-3 basic playground terminal which is provided on the openAI website, rather than any programming language wrapper of openAI are illustrated. GPT-3.as a single model can perform multiple types of Natural Language Processing jobs. It operates on the basis of prompts, and a strong prompt can help the model provide the best results.  hope this article has helped you learn more about GPT-3 prompts and how to create your own. Please share any problems you experience while creating the prompts, as well as any thoughts, suggestions, or comments.

For details of GPT3, see [OpenAI](https://openai.com/api/)

<p>
{% include  share.html %}
</p>

<span style="color:#9e9696"><i> Last updated: 21/02/2023</i> </span>

<p>
{% include  license.html %}
</p>