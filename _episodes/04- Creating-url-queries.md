---
title: "Creating URL Queries"
teaching:  20
exercises: 20
questions:
- "What are URL query strings?"
- "How can you make API requests?"
- "How do you interperet API documentation?"
objectives:
- "Explain URL query strings"
- "Explain how to create API queries"
- "Explain how to read and interperet API documentation"
keypoints:
- "REST APIs use query stings to make requests"
- "URL queries are found all across the web"
---

## URL Query Strings

Let's break down the given URL `https://www.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=nucleotide&id=NC_000852&rettype=fasta&retmode=text` to illustrate the concepts of constructing an API query using endpoints, resources, parameters, and headers.

### Endpoint and Base URL

- **Base URL**: `https://www.ncbi.nlm.nih.gov`
  - This is the root address for the NCBI (National Center for Biotechnology Information) website, which hosts various services and databases.
- **Endpoint**: `/entrez/eutils/efetch.fcgi`
  - This is the specific path to the eFetch utility within the NCBI E-utilities suite, designed to retrieve a variety of data from NCBI's databases.

### Resource

- In this URL, the resource isn't explicitly named in a RESTful manner (like `/users` or `/books` in more REST-oriented APIs). However, the resource we're interested in (nucleotide sequences from a database) is implied by the combination of the endpoint and the query parameters.

### Parameters

Parameters are appended to the URL after the `?` mark, with each key-value pair separated by an `&`.

- **`db=nucleotide`**: This parameter specifies the database from which the data should be fetched. In this case, `db` stands for "database," and `nucleotide` indicates that the nucleotide database is being queried.
- **`id=NC_000852`**: This parameter specifies the unique identifier of the resource being requested. `id` is the key, and `NC_000852` is the value, which is an accession number for a specific nucleotide sequence.
- **`rettype=fasta`**: This parameter defines the return type of the data. `fasta` indicates that the data should be returned in the FASTA format, which is a text-based format for representing nucleotide sequences.
- **`retmode=text`**: This parameter specifies the return mode, indicating that the response should be in plain text format.

### Headers

- While headers are not visible in the URL, when making the request (e.g., using `curl` or in a web browser), there would be HTTP headers sent along with the request. Common headers might include `Accept` to specify the type of response the client can process (e.g., `Accept: text/plain`) or `User-Agent` to identify the client making the request.
- In a simple browser request like this one, headers are set by the browser itself. In more complex API interactions, especially when using tools like `curl` or programming languages to make the request, you might manually set additional headers for purposes like authentication.

### Constructing the Query

The construction of the API query in this example involves starting with the base URL, appending the endpoint that specifies the eFetch utility, and then adding the parameters that define the exact data request. The complete URL `https://www.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=nucleotide&id=NC_000852&rettype=fasta&retmode=text` represents a well-constructed API query that tells the NCBI server exactly what data is being requested, from which database, in what format, and how it should be returned.

By breaking down this URL, you can see how the different components of an API query—endpoint, resources, and parameters—work together to specify and retrieve data from a web-based API.


### YouTube

 **[https://www.youtube.com/watch?v=s7wmiS2mSXY&t=1m45s](https://www.youtube.com/watch?v=s7wmiS2mSXY&t=1m45s)**
![youtube URL](../assets/img/youtubeAPI.png)

## Reading Documentation

- Look through the params
    - What types of search parameters are available?
    - Do they match what you need?
    - What is the Endpoint (Base URL)?
- Look for sample requests & responses
    - What kind of data does it return?
    - Is it what you’re looking for?
- Look for restrictions
    - Is it free?
    - Does it require a key or permissions?
    - Do they impose a limit?


## Creating a Query
- National Weather Service API
    - Documentation: [https://www.ncbi.nlm.nih.gov/books/NBK25499/](https://www.ncbi.nlm.nih.gov/books/NBK25499/)
    - Endpoint/Base URL: https://eutils.ncbi.nlm.nih.gov/entrez/eutils/einfo.fcgi
    
    

>## Let’s create a query 
> Run this query: https://api.weather.gov/stations?limit=10&state=CT
>1. What do the results show?
>2. What is the Station Identifier for Tweed-New Haven Airport?
>3. Write a query that returns all active weather alerts for California. (Hint: use 'area' not 'state')
>
>>## Solution
>>1. Shows 10 currently-active weather stations in Connecticut and includes metadata about each station.
>>2. KHVN
>>3. https://api.weather.gov/alerts?active=1&area=CA or https://api.weather.gov/alerts/active?area=CA or https://api.weather.gov/alerts/active/area/CA
>{: .solution}
{: .challenge}