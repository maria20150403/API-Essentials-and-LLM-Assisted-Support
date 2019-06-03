---
title: "API Queries in Shell"
teaching: 10
exercises: 10
questions:
- "How do I fetch data from API's using the Unix shell?"
- "How do I process API responses to get plain text, usable by standardf Unix shell tools?"
objectives:
- "Understand how to fetch data from APIs using the Unix shell"
- "Choose and operate tools to convert API response to plain text"
keypoints:
- "You can request and process data from APIs using Unix shell tools"
- "JSON or XML results can be parsed to plain text, to be consumed by standard Unix shell tools"
---

## Fetching data from the web

With a [URL query](https://joshuadull.github.io/APIs-for-Libraries/03-Creating-url-queries/index.html) in hand, the [Unix shell](https://librarycarpentry.org/lc-shell/) provides a powerful commandline driven interface for processing and interacting with large amounts of text data.  As the response from many APIs will be in a text-based format, such as JSON or XML, various shell tools will provide us with the functionality  to acquire data and process the response, allowing for easy use of the large existing set of Unix tools.


## Shell Tools  
Building on the skill from [Unix shell](https://librarycarpentry.org/lc-shell/) lesson, we add the following commandline programs for working with APIs

- ```curl```   - A command line tool for transferring data from URLs
- ```jq```  - A commandline JSON processor
- ```xmllint```  - A command line XML parser

## API ```Get``` Requests  
```$ curl  ```

Using the Voyager API

```$ curl https://libapp.library.yale.edu/VoySearch/GetBibItem?isxn=9780415704953 ```
{: .bash}  

The API response can be written to a file using the angled bracket ```>``` followed by a file name:

```$ curl https://libapp.library.yale.edu/VoySearch/GetBibItem?isxn=9780415704953 > file.txt ```   

Alternatively, the output can be piped to another command for futher action:

```$ curl https://libapp.library.yale.edu/VoySearch/GetBibItem?isxn=9780415704953 | wc -l ```

This example uses the ```wc`` command with the ```-l``` option to count the number of lines in the response.   



## JSON Processing

The ```jq``` command 

#### Formatting Output

``` $ curl https://libapp.library.yale.edu/VoySearch/GetBibItem?isxn=9780415704953  | jq '.'```



## XML Processing

Converting response from Voyager API to text, select element



## 
Pipe to other shell tools, create csv, loop?

