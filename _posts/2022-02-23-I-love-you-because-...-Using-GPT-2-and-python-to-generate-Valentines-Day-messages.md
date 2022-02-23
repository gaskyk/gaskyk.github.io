---
layout: single
title:  "I love you because…: Using GPT-2 and python to generate Valentine's Day messages"
date:   2022-02-23 08:38:07 +0000
---


Generative Pre-trained Transformer 2 (GPT-2) is an open-source language model created by OpenAI in February 2019. Amongst many other things, it can generate text that can appear as if a human has written it. I thought it might be fun to see how realistic it is when it completes the sentence &quot;I love you because…&quot;, albeit a bit late for Valentine&#39;s Day this year!

## GPT-2 and GPT-3

OpenAI released the complete version of the GPT-2 language model (with 1.5 billion parameters) in November 2019. GPT-3, with 175 billion parameters was created in 2020 but access is only available through an API that requires a business case for use. As a result, I have focussed on GPT-2 in this blog.

## What I did

I used the pre-trained GPT-2 model as I don&#39;t have a serious application and don&#39;t need my own corpus to be used in training.

### 1 – Install then import the libraries

You need PyTorch to be installed first by going to the [PyTorch website](https://pytorch.org/) and following their instructions. As I was installing this on my personal laptop, I installed the CPU-only version.

The [Hugging Face transformers package](https://huggingface.co/docs/transformers/index) provides the pre-trained GPT-2 model and an intuitive Python package for it. To install transformers, run the following in the command line:

	Pip install transformers

Then in Python run

	From transformers import pipeline

Pipeline takes the complexity away from the tasks at hand.

### 2 – Build the text generation pipeline

Next, we build the pipeline for text generation. GPT-2 is the default model.

	text_generation = pipeline("text-generation")

### 3 – Create the starting text

	prefix_text = "I love you because"

### 4 – Start generating

You can now start generating text! I&#39;ve set the maximum length of the tokens to 25 and set do\_sample to True so that when we re-run the text below, we generate different results.

	generated_text = text_generation(prefix_text, max_length=25, do_sample=True)[0]
	print(generated_text["generated_text"])

You can see that the whole code comes to only a few lines, which demonstrates the power of both the GPT-2 model and the transformers package.

## Results

Here are five random responses given by the model:

- I love you because I know you truly care about us, because you&#39;re the best you can be
- I love you because of you. I&#39;m going to keep working my ass off and be around you for the rest of my
- I love you because you are a wonderful person and God is for us because you are a good person
- I love you because I thought you were in the same boat
- I love you because we are the people that put together our team of directors

OK, maybe those last two aren&#39;t ideal for a Valentine&#39;s Day message, but the first one in particular could pass the [Turing test](https://en.wikipedia.org/wiki/Turing_test) for being indistinguishable from being written by a human.

## Final thoughts

I did this because I wanted to understand more about GPT-2 and how I could implement it in some of my work. I&#39;m really impressed, both by the model itself obviously, but also by how easy the transformers package by Hugging Face made it to get started. The package and model can also do other things in the Natural Language Processing area, including translation, summarisation and question answering, some of which will be really useful in my work.

Thanks to this [Towards Data Science blog](https://towardsdatascience.com/text-generation-with-pretrained-gpt2-using-pytorch-563c7c90700) by Raymond Cheng for the excellent tutorial on using GPT-2.

## Get the code

As ever, my code is available on [Github](https://github.com/gaskyk/gpt_text_generation) and I always welcome comments or suggestions for improvements.