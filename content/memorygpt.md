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

The problem I want to solve is to provide a very accessible approach to using low context-length'd models to their fullest efficiency, which in addition will also probably solve the attention issues arising in LLMs, where the model "conveniently" forgets information due to increased length of information being input.

To note that this might not be a novel approach, and that there might be better solutions already available, in established papers and implementations. This post is to discuss the various approaches one can devise in utilizing a model's context space.

Here is a rough draft of the system I'm proposing:

![Langchain Concept Architecture](/images/langchain_context/concept_arch.png)

To put it in words, the query being provided by the user, on decomposing into tokens for use by the LLM will be associated with a context token set. Visualize a toffee in your hands, it is of two seperate items: one is the toffee itself, and the wrapper in which the toffee was encased. Using that analogy, the context tokens are the ones wrapping around the query token here; the decomposed query will be associated with appropriate information which will help us have the response stay in context.

The response will be validated (in reference of the discussion here: <u>[RAG CONTROL FLOW](https://github.com/mistralai/cookbook/tree/main/third_party/langchain))</u>, and this proposed architecture from the paper is a good view of the validator procedure for reducing hallucinations on the response provided.

![RAG in control](/images/langchain_context/langgraph_adaptive_rag.png)

I obviously had to test the current system a bit, before I develop instruments to aid me in this task. So I naturally turned to ChatGPT with this task - to establish some metric for identifying conceptual similarities between a query text and context text. This is important because we need to make sure the context text is valid in it's own right, and synchronizes with the response for the query raised with the LLM. The better the context defined, the better responses will be.

Here is a simulation of a conversation (we call the process as chat completions in LLM-language) between the user and the LLM about the 1990 Paris Olympics, in which the context gracefully towards art and architecture. This type of context switching is a natural process, and our aim is to test out and identify cohesive means to keep track of this switching of fine-context in the conversation.

| Conversation # | User Input                                          | Assistant Response                                                                                                                                                                | Context Information                                                                                                                                                          |
|-----------------|----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1               | Can you tell me about the 1900 Olympics?          | The 1900 Summer Olympics were held in Paris, France, as part of the 1900 World's Fair. They were notable for being the first Games where women could compete...                   | Topic: 1900 Olympics; Keywords: 1900 Olympics, Paris, women, unusual sports, World's Fair.                                                                                  |
| 2               | Can you tell me more about the live pigeon shooting event? | Live pigeon shooting was a one-time event in the 1900 Olympics. Over 300 birds were killed, deemed unethical, and replaced by clay pigeon shooting.                              | Follow-up query; Keywords: live pigeon shooting, 1900 Olympics, ethical concerns, event replacement.                                                                        |
| 3               | How did the introduction of women’s events in 1900 shape the future of the Olympics? | The inclusion of women’s events in 1900 marked a significant step toward gender equality. Women’s participation expanded over time, shaping the modern inclusive Olympics.         | Follow-up from earlier women’s participation mention; Keywords: women’s events, gender equality, evolution of sports.                                                       |
| 4               | The 1900s were also a time of beautiful art and architecture, weren’t they? | Absolutely! The 1900s saw the rise of Art Nouveau, a style with organic, flowing lines and intricate designs inspired by nature, e.g., Hector Guimard’s Paris Métro entrances.     | Divergence to Art Nouveau; Keywords: Art Nouveau, Hector Guimard, Paris Métro, 1900s architecture.                                                                          |
| 5               | What other cities saw prominent Art Nouveau architecture? | Brussels had Victor Horta, Vienna had Otto Wagner, and Barcelona showcased Antoni Gaudí’s masterpieces, blending Art Nouveau with Catalan influences.                            | Expansion of Art Nouveau topic; Keywords: Art Nouveau, cities, Victor Horta, Otto Wagner, Antoni Gaudí, architectural innovation.                                           |
| 6               | Could you connect Gaudí's works to broader cultural movements of the time? | Gaudí’s works were part of the Modernisme movement, a Catalan take on Art Nouveau blending modernity and tradition. His organic designs reflect a deep connection to nature.       | Follow-up on Gaudí’s contributions; Keywords: Gaudí, Modernisme, Art Nouveau, Catalan identity, cultural movements.                                                         |

A good way to keep track of current context amongst the conversation sequence is to maintain the list of keywords, which are the crucial bits of information that define the information as an atomic unit. So instead of using up more tokens in trying to preserve information, we reduce it to almost a singular unit (once again, best use of the allowed context-lengths, our ultimate goal).

Here is a mindmap of the keywords in progression across the conversation sequence, and it's a way of depicting how the context branches throughout the conversation.

![KEYWORD TREE](/images/langchain_context/simulation_keyword_tree.png)

## References - 
1. [Lost in the Middle: How Language Models Use Long Contexts](https://arxiv.org/pdf/2307.03172)
2. 
