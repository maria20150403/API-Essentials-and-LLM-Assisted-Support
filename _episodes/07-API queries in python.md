---
title: "API queries in python"
teaching: 15
exercises: 5
questions:
- "What is the difference between authentication and authorization?"
- "What are API keys?"
- "How do we obtain an API key?"
objectives:
- "Understand the purpose of authentication and authorisation."
- "Understand the different methods of authentication."
- "Be able to obtain and use an API key to access data."
keypoints:
- "Authentication ensures that only authorised entities can access the API."
- "Authorisation ensures they can only access what they're permitted to."
---


~~~
$ curl -X GET "https://data.csiro.au/dap/api/v2/featuredCollections" 
~~~
{: .language-bash}

~~~
[
  {
    "collectionId": 60850,
    "fedoraId": "csiro:52394",
    "collectionTitle": "Annual woody vegetation and canopy cover grids for Tasmania",
    "description": "This collection provides annual woody vegetation (> 10 % canopy cover, > 2 m height) and canopy cover (0 – 100%) grids for Tasmania with a spatial resolution of 10 m. This dataset was developed to improve the availability of information suitable for farm-scale analyses of tree cover using publicly available, non-commercial remote sensing data. It enables fine-scale analyses of woody vegetation and canopy cover trends in natural and modified ecosystems across Tasmania between 2017 and 2023.",
    "imageLink": "https://www.csiro.au/~/media/DAP/800pxCoolTemperateRainforestCreepyCrawleyNatureTrailTasmaniaMarch2015.jpg",
    "imageTitle": "MarshallSimon, Wikipedia",
    "imageAltText": "Bryophyte Communities in Cool Temperate Rainforest",
    "publishedDate": "2023-10-23",
    "contributors": [
      "Stephen Stewart"
    ]
  },
  {
    "collectionId": 58498,
    "fedoraId": "csiro:55990",
    "collectionTitle": "Estimated spatial distribution for Australia's terrestrial threatened species",
    "description": "This data set contains spatial layers of the estimated historical distribution for 1518 Australian terrestrial species listed as Critically Endangered, Endangered or Vulnerable as of July 2022. Each species’ historical distribution was derived from broad habitat preferences. Habitat preferences were identified by intersecting occurrence records with fine resolution (100 m) spatial layers of pre-clearing (pre-1750) vegetation types, bioclimatic regions and elevation. The historical distribution was then calculated by selecting areas of preferred habitat, falling within observed altitudinal limits, from the pre-clearing vegetation extent. Spatial layers representing the currently occupied portion of the estimated historical distribution are also provided.",
    "imageLink": "https://www.csiro.au/~/media/DAP/800px-Eucalyptus_salubris_or_Gimlet_gum.jpg",
    "imageTitle": "Keren Gila, Wikipedia",
    "imageAltText": "Eucalyptus salubris or Gimlet gum",
    "publishedDate": "2023-03-30",
    "contributors": [
      "Kate Giljohann",
      "Karel Mokany",
      "Simon Ferrier",
      "Tom Harwood",
      "Chris Ware"
    ]
  },
  {
    "collectionId": 60623,
    "fedoraId": "csiro:60522",
    "collectionTitle": "Modelled deer density and impact on vegetation across the Melbourne drainage and waterway extent, Victoria",
    "description": "This collection contains spatial predictions of deer density and deer impact on vegetation across the Melbourne drainage and waterway extent. Deer density is quantified in units of faecal pellets/m². Deer impacts on vegetation (whole plants) are quantified as a percentage, based on foliage browsed, stem damage or rubbing damage. The median response modelled for each variable is provided, alongside the 5ᵗʰ and 95ᵗʰ quantiles to characterise uncertainty in the predictions.\n\nPlease refer to the published manuscript under related links for further details (TBD). ",
    "imageLink": "https://www.csiro.au/~/media/DAP/deer.jpg",
    "imageTitle": " Rexness, Wikipedia",
    "imageAltText": "Red Deer Grazing",
    "publishedDate": "2023-10-04",
    "contributors": [
      "Melissa Fedrigo",
      "Ami Bennett",
      "Stephen Stewart",
      "David Forsyth",
      "Joe Greet"
    ]
  },
  {
    "collectionId": 60456,
    "fedoraId": "csiro:60456",
    "collectionTitle": "Aggregated Data: Australian Species Occurrences 1900-2022",
    "description": "Aggregated Australian species occurrence data from 1900 to the present using a suite of facets of most importance for environmental assessments. Occurrence records were aggregated and organised by the Atlas of Living Australia (ALA, https://ala.org.au/) and include survey and monitoring data collected and managed by the Integrated Marine Observing System (IMOS, https://imos.org.au/) and the Terrestrial Ecosystem Research Network (TERN, https://tern.org.au/).\n\nData from these infrastructures and other sources have been organised here as a national public-access dataset.\n\nThis dataset serves as a standardised snapshot of Australian biodiversity occurrence data from which many indicator datasets can more readily be derived (see Has Derivation entries below).\n\nThe primary asset is AggregatedData_AustralianSpeciesOccurrences_1.1.2023-06-13.csv. This contains all faceted data records for the period and supported facets related to time, space, taxonomy and conservation significance.\n\nSix derived assets (SummaryData-ProtectionStatusAustralianMarineSpeciesOccurrences-1.1.2023-06-13.csv, SummaryData-ProtectionStatusAustralianTerrestrialSpeciesOccurrences-1.1.2023-06-13.csv, SummaryData-IntroducedSpeciesOccurrencesByMarineEcoregion-1.1.2023-06-13.csv, SummaryData-IntroducedSpeciesOccurrencesByTerrestrialEcoregion-1.1.2023-06-13.csv, SummaryData-ThreatenedSpeciesOccurrencesByMarineEcoregion-1.1.2023-06-13.csv, SummaryData-ThreatenedSpeciesOccurrencesByTerrestrialEcoregion-1.1.2023-06-13.csv) demonstrate uses supported by the faceted data. Each is a pivot of the aggregated dataset.\n\nThe data-sources.csv file includes information on the source datasets within the Atlas of Living Australia that contributed to this asset. README.txt documents the columns in each data file.\n\nGrouping records from this dataset supports comparisons between the number of occurrence records for different regions and/or time periods and/or categories of species and occurrence data. Grouped counts of this kind may serve as useful indications of variation and change across the dimensions compared. Note however that such counts may not accurately reflect real differences in biodiversity. It is important to consider confounding factors (particularly variations in recording effort over time). Grouping all records by a single facet (e.g. IBRA region) may help to expose such factors.\n\nThese data are versioned at 12-month intervals. Previous versions will be linked below under Previous Version. The latest version can always be accessed at https://ecoassets.org.au/data/aggregated-data-australian-species-occurrences/.\n\nNotes\n\nGRIIS 1.6 includes a number of vertebrate species listed because some individuals have been translocated or (re-)introduced beyond their remaining ranges for conservation purposes. It is unhelpful for the current analysis to treat these as introduced species. These species were removed from the version of the GRIIS list used in this analysis. In future versions of GRIIS, these species will be documented as native species that have been translocated/reintroduced.",
    "imageLink": "https://blog.csiro.au/wp-content/uploads/2017/04/Rainbow_Lorikeet_Trichoglossus_moluccanus_at_Adelaide_Airport_1-tinkered.jpg",
    "imageTitle": "CSIRO",
    "imageAltText": "Rainbow Lorikeet",
    "publishedDate": "2023-09-26",
    "contributors": [
      "Donald Hobern",
      "Shandiya Balasubramaniam",
      "Atlas of Living Australia",
      "Terrestrial Ecosystem Research Network (TERN)",
      "IMOS",
      "Australian Research Data Commons"
    ]
  }
]

~~~
{: .output}



