---
title: "Exercise: OCLC WorldCat Search API"
teaching: 5
exercises: 20
questions:
- "What are the different OCLC APIs and how are they different?"
- "What can you query using the WorldCat Search API"
objectives:
- "Explore creating queries using the WorldCat Search API"
- "Use the WorldCat API to enhance existing bibliographic data"
- "Accomplish the exercises using the Shell or OpenRefine"
keypoints:
- ""
---

## Using OCLC's WorldCat Search API
OCLC provides access to there WorldCat database via their Search API. This API will let you search by keywords or by various identifirers (ISBN, ISSN, OCLC, etc.) and retireve the record for each item. It will even let you find which libraries hold copies of each item. 
- [Dcumentation](https://www.oclc.org/developer/develop/web-services/worldcat-search-api/bibliographic-resource.en.html)
- [More on Library Locations](https://www.oclc.org/developer/develop/web-services/worldcat-search-api/library-locations.en.html)

>## Creating a query of OCLC WOrldCat Search API  
>We have a list of items with ISBN numbers. We want to write a query to retrieve the MARCXML records for an item. Use the link to documentation above to create your query.
>1. Which 'Operation' should you use to find mulitple records in MARCXML?
>2. What is the base URL for the query? 
>3. Which parameters are required? Which parameters aren't required, but might need to be considered?
>4. Which query index/indices do you need to use?
>5. Finally, write your query using the ISBN 9781442237360, test your query in a web browser, then share your query in the etherpad. (Hint: turn frbrGrouping off)
>
>>## Solution
>>1. SRU
>>2. http://www.worldcat.org/webservices/catalog/search/sru?query={CQLQuery}
>>3. _Required_: query, wskey. 
>>   _Optional_: all could be useful depending on your goals.
>>4. ISBN, srw.bn	
>>5. Check the etherpad for answers 
>{: .solution}
{: .challenge}

## OpenRefine or Shell?
You can complete the last two exercises in OpenRefine or the Shell. The next section gives some hints for using each in case you get lost.


### OpenRefine: New GREL Functions
In addition to the functions we've already covered in the [OpenRefine Lesson](https://librarycarpentry.org/lc-open-refine/), these GREL functions will help you complete the exercises in this lesson. You can find the link to the documentation for each function below:
- [parseJson()](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Other-Functions#parsejsonstring-s)
- [parseXml(), xmlText(), select()](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Other-Functions#jsoup-xml-and-html-parsing-functions)
- [forEach()](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Controls#foreachexpression-a-variable-v-expression-e)
- [uniques()](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Array-Functions#uniquesarray-a)
- [if()](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Controls#ifexpression-o-expression-etrue-expression-efalse)

### Shell


>## Fetch MARCXML results (OpenRefine)
>We'll start by using the query you wrote in the previous exwrcise, but expand it to query our list of ISBNs.
> - Create a new project in OpenRefine using the provided data. You should have 2 columns: Title & ISBN.
> - Add a new column called _fetchOCLC_ that contains the full MARCXML record for each title. 
>1. What steps did you take to create column _fetchOCLC_?
>2. How did you change your query to work in OpenRefine?
>
>>## Solution
>>1.
>>2.  	 
>{: .solution}
{: .challenge} 

>## Parse MARCXML results (Shell) 
>
>1. 
>
>>## Solution
>>1. 	 
>{: .solution}
{: .challenge}

