+++
title = 'Netmarc: Personal Indexes on the Internet'
date = 2024-08-26T20:34:40+05:30
draft = false
description = "A build using Vanilla React, Bootstrap, Krutrim Cloud, Python and Bing Azure API"
image = "/images/netmarc_small.png"
imageBig = "/images/netmarc_big.png"
categories = ["projects","reactjs","azure"]
authors = ["Raghul R"]
avatar = "/images/avatar.webp"

+++

**Explore the project live: [https://netmarc.vercel.app/](https://netmarc.vercel.app/)**

NetMarc is a powerful, customizable tool designed to tailor your search experience based on your needs. Whether you're a student, a developer, a business professional, or just browsing the web, NetMarc provides a focused and efficient way to find the information you need. 

![BingSearch-Netmarc](/images/netmarc_3.png)

### The Tech Stack

* **Frontend (Vercel):** The user interface is built with **ReactJS**, a popular JavaScript library known for its component-based architecture and efficient rendering. Hosting on Vercel ensures fast loading times and a seamless user experience.
* **Backend (Render):** The backend logic is powered by a **Python** server using the **Gunicorn** WSGI HTTP server, hosted on Render for reliable and scalable performance.
* **Search API:**  NetMarc leverages the **Azure Bing API** to provide comprehensive and relevant search results.
* **Trust Score Integration:**  Website trustworthiness is assessed using **ScamAdviser**, providing users with an extra layer of security and confidence in their search results.
* **AI Text Generation:**  For intelligent text generation and conversational capabilities, NetMarc utilizes the **Mistral 7B** language model, accessible through **Krutrim Cloud models**.

![Profile-Netmarc](/images/netmarc_1.png)

### Personalized Search with App Profiles

One of NetMarc's key features is its ability to personalize search results based on user-selected profiles. These profiles cater to specific user needs, ensuring that relevant information is prioritized:

* **General Use:** This profile provides a standard, unfiltered search experience.
* **Academic:** Tailored for researchers and students, this profile prioritizes results from academic resources like Google Scholar, JSTOR, PubMed, and more.
* **Programmer:** Designed for developers, this profile elevates results from platforms like Stack Overflow, GitHub, GitLab, and other coding communities.
* **Business:** Perfect for business professionals, this profile prioritizes results from financial news sources like Bloomberg, Forbes, The Wall Street Journal, and business-oriented platforms like LinkedIn.

This profile-driven approach is implemented through a domain filtering mechanism on the backend:

```python
domain_list = {
    'General Use': [], # No filtering for General Use
    'Academic': ['scholar.google.com', 'jstor.org', 'springer.com', 'researchgate.net', 'academia.edu', 'arxiv.org', 'pubmed.ncbi.nlm.nih.gov', 'ieee.org', 'cambridge.org', 'edx.org', 'coursera.org'],
    'Programmer': ['stackoverflow.com', 'github.com', 'gitlab.com', 'dev.to', 'hackerrank.com', 'leetcode.com', 'medium.com', 'daily.dev', 'reddit.com', 'freecodecamp.org', 'dzone.com'],
    'Business': ['bloomberg.com', 'forbes.com', 'wsj.com', 'ft.com', 'marketwatch.com', 'nasdaq.com', 'businessinsider.com', 'hbr.org', 'inc.com', 'economist.com', 'linkedin.com', 'cnbc.com']
}
```

By prioritizing results from these domains based on the selected profile, NetMarc delivers a more focused and relevant search experience.

![AI-Netmarc](/images/netmarc_2.png)

### Beyond Search: AI-Powered Conversations

NetMarc goes beyond traditional search by integrating AI-powered text generation. Leveraging the Mistral 7B language model, NetMarc enables users to:

* **Engage in general conversations:** Ask questions, explore topics, and receive insightful responses.
* **"Chat" with websites:** Summarize content, extract key information, and interact with web pages in a conversational manner.

This functionality opens up exciting possibilities for research, information gathering, and even content creation.

### This might be the true future of personalized search!

NetMarc represents a significant step towards a more intelligent and personalized search experience. By combining a powerful tech stack with innovative features like profile-based filtering and AI-powered conversations, NetMarc empowers users to find information more efficiently and engage with the web in a more meaningful manner. 
