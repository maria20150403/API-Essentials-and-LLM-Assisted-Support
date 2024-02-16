---
title: "Using LLMs for APIs"
teaching: 15
exercises: 5
questions:
- "What is an API?"
- "Why do we need APIs?"
- "How APIs work?"
objectives:
- "Understand the need for an API."
- "Understand the main components of an API."
- "Familiarity using Library APIs."
keypoints:
- "An API is a way for two or more computer programs or components to communicate with each other."
- "HTTP is the protocol originally designed for requesting and receiving Web pages, but now also used as the basis for a variety of APIs. HTTPS is the encrypted version of HTTP."
- "Every page on the world wide web is identified with a URL or Uniform Resource Locator."
- "A request is how you tell a server what you want to see. A response will either give you what you asked for, or tell you why the server can't do that. Both requests and responses have a header, and optionally a body."
- "We can make requests and receive responses, as well as see their headers, using `curl`."
---
We will be exploring the National Center for Biotechnology Information (NCBI) E-utilities API.
 - Documentation: [https://www.ncbi.nlm.nih.gov/books/NBK25499/](https://www.ncbi.nlm.nih.gov/books/NBK25499/)



## Metacognitive Strategies
In line with best practices while collaborating with LLMs, keep a check on your thinking process so that you have better control of it and don't fall prey to the various cognitive biases that maybe triggered due to the collaboration. Remember to Plan, Monitor and Evaluate your thinking.

## Query Construction
One of the ways LLMs like ChatGPT can help you is by constructing queries based on your requirement. However, receiving a perfect API query from ChatGPT depends on its familiarity with the API. Remember, always keep in mind that the response of an Artificially Intelligent agent should be interpreted in the context of its training data.

As a strategy, ask the LLM to construct a simple API query and check against the API documentation. If successful, try to gauge its familiarity with a more complex query. Let's try it out!


>Using the NCBI E-utilities API, 
>>```python
>>import requests
>>import json
>>```
>>{ .solution}
>{: .challenge}

## Help Understanding API Documentation

## Understanding API Responses

## Error Handling

## General Queries Regarding Best Practices