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
- The OCLC API requires an API key to authenticate your queries. Your instructor will provide you with an API key for the exercises below. 

>## Creating a query of OCLC WOrldCat Search API  
> We want to write a query to retrieve the MARCXML records for an item. Use the link to documentation above to create your query.
>1. Which 'Operation' should you use to find mulitple records in MARCXML?
>2. What is the base URL for the query? 
>3. Which parameters are required? Which parameters aren't required, but might need to be considered?
>4. Which query index/indices do you need to use?
>5. Write a query returning all records associated with the ISBN _9781442237360_, test your query in a web browser, then share your query in the etherpad. What title did you find? (Hint: turn off _frbrGrouping_)
>6. Write a query returning records associated with the OCLC number _466135850_, test your query in a web browser, then share your query in the etherpad. What title did you find? (Hint: turn off _frbrGrouping_)
>
>>## Solution
>>1. SRU
>>2. http://www.worldcat.org/webservices/catalog/search/sru?query={CQLQuery}
>>3. _Required_: query, wskey. 
>>   _Optional_: all could be useful depending on your goals.
>>4. ISBN, srw.bn	
>>5. Nobody expects the Spanish Inquisition
>>6. Urgh!: a music war 
>{: .solution}
{: .challenge}

## OpenRefine or Shell?
You can complete the last two exercises in OpenRefine or Shell. The next section starts with querying OCLC with OpenRefine; the Shell section is below.


## OpenRefine 

### New GREL Functions
In addition to the functions we've already covered in the [OpenRefine Lesson](https://librarycarpentry.org/lc-open-refine/), these GREL functions will help you complete the exercises in this lesson. You can find the link to the documentation for each function below:
- [parseJson( )](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Other-Functions#parsejsonstring-s)
- [parseXml( ), xmlText( ), select( )](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Other-Functions#jsoup-xml-and-html-parsing-functions)
- [forEach( )](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Controls#foreachexpression-a-variable-v-expression-e)
- [uniques( )](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Array-Functions#uniquesarray-a)
- [if( )](https://github.com/OpenRefine/OpenRefine/wiki/GREL-Controls#ifexpression-o-expression-etrue-expression-efalse)

>## Fetch MARCXML results (OpenRefine)
>We'll start by using the query you wrote in the previous exwrcise, but expand it to query our csv of titles & ISBNs.
> - Create a new project in OpenRefine using the provided data. You should have 2 columns: Title & ISBN.
> - Add a new column called _fetchOCLC_ that contains the full MARCXML record for each title. 
>1. What steps did you take to create column _fetchOCLC_?
>2. How did you change your query to work in OpenRefine?
>
>>## Solution
>>1. & 2. Ask your instructor for the solution 	 
>{: .solution}
{: .challenge} 

Now that we fetched data from our API, we need to parse the resulting XML to pull our information.

>## Parse MARCXML results
> Each MARC record retrieved can contain multiple items from WorldCat associated with the ISBN. We need to parse the XML to pull out data about each item. 
>The steps below will walk through creating a new column that contains every OCLC number associated with each item in our file. 
>1. In the _fetchOCLC_ column, select 'Edit column' -> 'Add column based on this column...'
>2. New column name: _OCLCNumber_
>3. Add the expression (don't click OK yet): `value.parseXml().select("controlfield[tag=001]")`
> - `parseXml()` works like `parseJson()`; it tells OpenRefine we're working with XML
> - We use `select()` to select the XML element we want. `select()` always returns an array.
> - The OCLC number is found in an element called _controlfield_ with an attribute called _tag_ that is equal to _001_.
> <img src="../assets/img/OCLCno.png" height="100" width="592">
> - The preview shows us our results. We should see an array of XML elements that contain the OCLC numbers associated with each ISBN.
>4. Change your expression to: `forEach(value.parseXml().select("controlfield[tag=001]"),v,v.xmlText())`
> - To pull out each number, we need to use a _forEach_ loop (like the Shell _for_ loop). 
> - `forEach()` takes 3 arguements: an array, a variable, and variable.function()
> - `value.parseXml().select("controlfield[tag=001]")` is our array
> - `v` is our variable
> - `v.xmlText()` is our function
> - The results give us an array of OCLC numbers.
>5. If we wanted numbers seperated by the pipe symbol \| instead of an array, what function could we add?
>6. Click OK!
> 
{: .checklist}

>## MORE OCLC in OpenRefine! 
> We worked through the previous example together, this time you're on your own. Figure out how to answer the questions below using the provided data and the OCLC API. 
>1. Create a column with each callNo associated with the ISBN. What expression did you use? (Bonus if you can include only the unique callNos in your results)
>2. Create a column with the number of records returned for each ISBN. Which title returns the most records?
>3. Write and run a query that will return only the OCLC MARCXML records for each item that Yale has a copy (Yale Library holdings). Record your query in the etherpad.
>4. Advacned: Using the results from question 4, add a new column that will contain "TRUE" if Yale has a copy of an item and "FALSE" if Yale doesn't. Copy your expression to etherpad. (hint: try `if()` function)
>
>>## Solution
>>1. `forEach(value.parseXml().select("datafield[tag=050]"),v,v.xmlText()).uniques().join(" | ")`
>>2. ...
>>3. `"http://www.worldcat.org/webservices/catalog/search/sru?wskey={API-KEY}&query=srw.bn=" + value + "+AND+srw.li=YUS&frbrGrouping=off"`
>>4. `if(value.parseXml().select("numberOfRecords")[0].xmlText().toNumber() > 0, "TRUE","FALSE")`
>{: .solution}
{: .challenge}

## Shell

>## Fetch MARCXML results (Shell) 
>
>1. 
>
>>## Solution
>>1. 	 
>{: .solution}
{: .challenge}

>## Fetch MARCXML results (Shell) 
>
>1. 
>
>>## Solution
>>1. 	 
>{: .solution}
{: .challenge}