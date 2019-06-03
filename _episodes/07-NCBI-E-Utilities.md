---
title: "Excercise: NCBI E-utilities"
teaching: 
- "5"
exercises: 
- "15"
questions:
- "How can we use the Entrez Programming Utilities (E-utilities) to search across the Entrez Molecular Sequence Database System?"
objectives:
- "Introduce the Entrez Molecular Sequence Database System (Entrez) and the databases it includes."
- "Provide sources for documentation and more information about using the E-utilities."
- "Develop API calls answer research questions using data pulled from Entrez through the E-utilities." 
keypoints:
- "By linking to the NCBI Entrez system through the E-utilities, you can make complicated data requests across a huge dataset."
---

## Entrez Molecular Sequence Database System (Entrez)

Entrez is a molecular biology database system that provides integrated access to nucleotide and protein sequence data, genomic mapping informaiton, 3D structure data, PubMed MEDLINE, and more. This system is produced by the National Center for Biotechnology Information (NCBI). 

Entrez is NCBI's primary text search and retreival system that integrates the PubMed database of biomedical literature with 38 other literature and molecular databases

The web based search interface for these NCBI databases is avaiable to the public [here, through the U.S. National Library of Medicine](http://www.ncbi.nlm.nih.gov/Entrez/).

#### Databases included in Entrez
[You can find a full list of Entrez databases listed here](https://www.ncbi.nlm.nih.gov/books/NBK3837/).

## Entrez Programming Utilities (E-utilities)
The E-utilities are made up of 9 programs that provide access to Entrez. You can find a list of these 9 programs in the table below. The information shown in this table was taken from [Eric Sayers A General Introduction to the E-utilities](https://www.ncbi.nlm.nih.gov/books/NBK25497/).

| E-utilities | Query string | Use |
| ------ | ------ | ------ |
| EInfo | eutils.ncbi.nlm.nih.gov/entrez/eutils/einfo.fcgi | Provides the number of records indexed in each field of a given database, the date of the last update of the database, and the available links from the database to other Entrez databases. |
| ESearch | eutils.ncbi.nlm.nih.gov/entrez/eutils/esearch.fcgi | Responds to a text query with the list of matching UIDs in a given database (for later use in ESummary, EFetch or ELink), along with the term translations of the query. |
| EPost | eutils.ncbi.nlm.nih.gov/entrez/eutils/epost.fcgi | Accepts a list of UIDs from a given database, stores the set on the History Server, and responds with a query key and web environment for the uploaded dataset. |
| ESummary | eutils.ncbi.nlm.nih.gov/entrez/eutils/esummary.fcgi | Responds to a list of UIDs from a given database with the corresponding document summaries. |
| EFetch | eutils.ncbi.nlm.nih.gov/entrez/eutils/efetch.fcgi | Responds to a list of UIDs in a given database with the corresponding data records in a specified format. |
| ELink | eutils.ncbi.nlm.nih.gov/entrez/eutils/elink.fcgi | Responds to a list of UIDs in a given database with either a list of related UIDs (and relevancy scores) in the same database or a list of linked UIDs in another Entrez database; checks for the existence of a specified link from a list of one or more UIDs; creates a hyperlink to the primary LinkOut provider for a specific UID and database, or lists LinkOut URLs and attributes for multiple UIDs. |
| EGQuery | eutils.ncbi.nlm.nih.gov/entrez/eutils/egquery.fcgi | Responds to a text query with the number of records matching the query in each Entrez database. |
| ESpell | eutils.ncbi.nlm.nih.gov/entrez/eutils/espell.fcgi | Retrieves spelling suggestions for a text query in a given database. | 
| ECitMatch | eutils.ncbi.nlm.nih.gov/entrez/eutils/ecitmatch.cgi | Retrieves PubMed IDs (PMIDs) corresponding to a set of input citation strings. |

#### E-utilities Documentation
- [Entrez Programming Utilities Help](https://www.ncbi.nlm.nih.gov/books/NBK25501/) 

>##
>
>1. Perform a global Entrez search to determine racial/ethnic representation across the databases
> NIH racial and ethnic categories include American Indian or Alaska Native, Asian, Black or African American, Hispanic or Latino, Native Hawaiian or Other Pacific Islander, and White. (See NOT-OD-15-089)[https://grants.nih.gov/grants/guide/notice-files/not-od-15-089.html] for more details. 
>>## Solution
>> Here are the following API calls that would provide you with summary data
>>1. https://eutils.ncbi.nlm.nih.gov/gquery?term=african+AND+black&retmode=xml
>>2. https://eutils.ncbi.nlm.nih.gov/gquery?term=white&retmode=xml

>{: .solution}
{: .challenge}




