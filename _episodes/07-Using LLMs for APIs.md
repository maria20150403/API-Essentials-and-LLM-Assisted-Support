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
LLMs like ChatGPT can understand and generate text based on patterns learned from their training data. If an API's query parameters or the concept of valid input values have been discussed in the data the model was trained on, ChatGPT might be able to provide general guidance based on that information.

However, LLMs do not have real-time access to external databases or the internet, and they cannot interact with APIs directly to fetch or verify current data. Their knowledge is based on the information available up to their last training cut-off, which means they might not have data on newly developed APIs or recent changes to existing ones.

Hence, their responses should be taken with caution and it is always best to consult the official API documentation for the most accurate and up-to-date information.

## Metacognitive Strategies
In line with best practices while collaborating with LLMs, keep a check on your thinking process so that you have better control of it and don't fall prey to cognitive biases that maybe triggered due to the collaboration. Remember to Plan, Monitor and Evaluate your thinking.

## Query Construction
One of the ways LLMs like ChatGPT can help you is by constructing queries based on your requirement. However, receiving a perfect API query from ChatGPT depends on its familiarity with the API. Remember, always keep in mind that the response of an Artificially Intelligent agent should be interpreted in the context of its training data.

As a strategy, ask the LLM to construct a simple API query and check against the API documentation. If successful, try to gauge its familiarity with a more complex query. Let's try it out!


>Let's explore the National Center for Biotechnology Information (NCBI) E-utilities API.
>- Documentation: [https://www.ncbi.nlm.nih.gov/books/NBK25499/](https://www.ncbi.nlm.nih.gov/books/NBK25499/)
> Using this API, create an API query to 
>>```python
>>import requests
>>import json
>>```
>{ .solution}
{: .challenge}

## Help Understanding API Documentation
Some API documentations lack clarity on the types and ranges of valid inputs expected for parameters. Often, query parameters are not intuitive and the documentation may not include example queries, making it challenging to construct complex queries due to ambiguities. However, Large Language Models (LLMs) like ChatGPT, trained on extensive web data, can accurately interpret specific query parameters and offer insights into valid input values and their ranges.

Let's have a look at the FBI Crime Data API documentation: https://cde.ucr.cjis.gov/LATEST/webapp/#/pages/docApi



## Understanding API Responses
You can also paste in a block of JSON response from an API request to ChatGPT and ask it to describe it for you.

## Error Handling
Sometimes you can receive error codes from an API request. LLMs like ChatGPT can help you understand and resolve these errors.


## General Queries Regarding Best Practices
As a very simple yet helpful use-case of LLMs is to enquire about best practices when using API keys aor APIs in general.