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


## Authentication and identification

Many web APIs restrict access to registered users or applications. This may be
because they are used to control things that are specific to a particular user
account, because different people have different privilege levels and so
different endpoints available, or simply because the API provider wants to
collect statistics on how the API is being used.

Various ways exist for developers to authenticate to an API, including:

## Different methods of Authentication & Authorisation
* Basic Authentication: Username and Password mechanism.
* API Keys: Tokens to identify and validate the user/application.
* OAuth: A standard protocol for token-based authentication and authorization.

One important fact about HTTP is that it is _stateless_: each request is treated
entirely separately, with no memory from one request to the next. This means
that you must present your authentication credentials with every request you
make to the API. (This is in contrast to other protocols like SSH or FTP, where
you authenticate once at the start of a session, and then subsequent messages
can be sent back and forth without the need for re-authentication.)

For example, NASA offers an API that exposes much of the data that they make
public. They require an API key to identify you, but don't require any
authentication beyond this.

Let's try working with the NASA API now. To do this, first we need to generate
our API key by providing our details at [the API home page][nasa-api]. Once that
is done, NASA provide the API key instantly, and send a copy to the email
address you provide. They helpfully also provide an example of an API query to
try, querying the Astronomy Picture of the Day (APOD). This shows us that NASA
expects the API key to be encoded as a query parameter.

~~~
$ curl -i https://api.nasa.gov/planetary/apod?api_key=ejgThfasPCRf4kTd39ar55Aqhxv8cwKBdVOyZ9Rr
~~~
{: .language-bash}

~~~
HTTP/1.1 200 OK
Date: Mon, 15 Mar 2021 00:08:34 GMT
Content-Type: application/json
Content-Length: 1135
Connection: keep-alive
Vary: Accept-Encoding
X-RateLimit-Limit: 2000
X-RateLimit-Remaining: 1998
Access-Control-Allow-Origin: *
Age: 0
Via: http/1.1 api-umbrella (ApacheTrafficServer [cMsSf ])
X-Cache: MISS
Strict-Transport-Security: max-age=31536000; preload

{"copyright":"Mia St\u00e5lnacke","date":"2021-03-14","explanation":"It appeared, momentarily, like a 50-km tall banded flag.  In mid-March of 2015, an energetic Coronal Mass Ejection directed toward a clear magnetic channel to Earth led to one of the more intense geomagnetic storms of recent years. A visual result was wide spread auroras being seen over many countries near Earth's magnetic poles.  Captured over Kiruna, Sweden, the image features an unusually straight auroral curtain with the green color emitted low in the Earth's atmosphere, and red many kilometers higher up. It is unclear where the rare purple aurora originates, but it might involve an unusual blue aurora at an even lower altitude than the green, seen superposed with a much higher red.  Now past Solar Minimum, colorful nights of auroras over Earth are likely to increase.   Follow APOD: Through the Free NASA App","hdurl":"https://apod.nasa.gov/apod/image/2103/AuroraFlag_Stalnacke_6677.jpg","media_type":"image","service_version":"v1","title":"A Flag Shaped Aurora over Sweden","url":"https://apod.nasa.gov/apod/image/2103/AuroraFlag_Stalnacke_960.jpg"}
~~~
{: .output}

We can see that this API gives us JSON output including a links to two versions
of the picture of the day, and then metadata about the picture including its
title, description, and copyright. The headers also give us some information
about our API usage&mdash;our rate limit is 2000 requests per day, and we have
1998 of these remaining (probably because the malware scanner on my email server
tested the link first to make sure it wasn't malicious).

With all of these ways to provide identification and authentication information,
we don't have time to cover each possibility exhaustively. For the vast majority
of APIs, there will exist good developer documentation that provides examples of
how to use the token or other identifier that they provide to connect to their
service, including examples.




## URL Query Strings

Let's break down the given URL Certainly! Let's dissect the given URL `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=nucleotide&id=5&rettype=fasta` to illustrate various API concepts using this specific example:

### Base URL

- **Base URL**: `https://eutils.ncbi.nlm.nih.gov`
  - This part of the URL specifies the protocol (`https`) and the domain (`eutils.ncbi.nlm.nih.gov`), directing the request to the NCBI's E-utilities server.

### Endpoint

- **Endpoint**: `/entrez/eutils/efetch.fcgi`
  - This part of the URL specifies the particular service or function within the API that you want to access. In this case, `efetch.fcgi` is the endpoint that facilitates fetching or retrieving data.

### Resources

- While the term "resources" in a RESTful API context usually refers to a specific type of data or entity (like `/users` or `/posts`), in this URL, the concept is implied through the combination of the endpoint and the query parameters. The resource being accessed here is nucleotide sequence data from NCBI's databases.

### Parameters

Parameters are included in the query string of the URL, which is the part after the `?`, with each key-value pair separated by `&`.

- **`db=nucleotide`**: This parameter specifies the database that the API should search in. Here, `db` stands for "database," and `nucleotide` indicates that the query is targeted at the nucleotide database.
- **`id=5`**: This parameter specifies the unique identifier of the nucleotide sequence you want to retrieve. The `id` here is set to `5`, which would correspond to a specific sequence record in the database.
- **`rettype=fasta`**: This parameter defines the format of the response. `fasta` is a text-based format for representing nucleotide sequences (and protein sequences), indicating that the API should return the data in FASTA format.

### Constructing the API Query

Combining these components, the full URL `https://eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi?db=nucleotide&id=5&rettype=fasta` is constructed to specifically fetch a nucleotide sequence with the ID `5` from the nucleotide database in FASTA format.

### Understanding the Query

By sending a request to this URL, you're asking the NCBI E-utilities service to fetch the data for a nucleotide sequence identified by `id=5` from the `nucleotide` database and return it in FASTA format. This is a common task in bioinformatics, where accessing specific genetic sequences efficiently is crucial for research and analysis.

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