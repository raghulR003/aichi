+++
title = 'MemoryGPT - Agentic Approach to building a GPT-esque application'
date = 2024-12-10T22:48:58+05:30
draft = false
description = "The post is about efficiently utilizing context length in LLMs and addressing limitations on the same and I aim to solve issues arise with information impedance and catastrophic information loss. This post will track all the work I perform towards it."
image = "/images/langchain_context/concept_arch.png"
imageBig = "/images/langchain_context.jpg"
categories = ["langchain","llm","langgraph","ai"]
authors = ["Raghul"]
avatar = "/images/avatar.webp"
+++

## Inception - 

The problem I want to solve is to provide a very accessible approach to using low context-length'd models to their fullest efficiency, which in addition will also probably solve the attention issues arising in LLMs, where the model "convieniently" forgets information due to increased length of information being input.

To note that this might not be a novel approach, and that there might be better solutions already available, in established papers and implementations. This post is to discuss the various approaches one can devise in utilizing a model's context space.

Here is a rough draft of the system I'm proposing:

![Langchain Concept Architecture](/images/langchain_context/concept_arch.png)

## References - 
[Lost in the Middle: How Language Models Use Long Contexts](https://arxiv.org/pdf/2307.03172)
