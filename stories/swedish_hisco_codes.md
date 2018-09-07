Querying occupational codes in multiple languages
=================================================

```
https://druid.datalegend.net/_api/datasets/dataLegend/jobHoard/services/monitor/sparql
```

```
out = Table
```

```{out = Table}
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX dct: <http://purl.org/dc/terms/>
PREFIX hisco: <https://iisg.amsterdam/hisco/>
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX prov: <http://www.w3.org/ns/prov#>

SELECT distinct ?provenance (count(?provenance) as ?prov_count) ?language
WHERE {
	hisco:jobHoard skos:member ?job .
  	?job skos:prefLabel ?label .
    hisco:category skos:member ?hisco.
    OPTIONAL {hisco:job skos:hiddenLabel ?label} .
    ?job prov:wasDerivedFrom ?provenance .
    BIND(lang(?label) AS ?language) .
  	# FILTER(lang(?label) = "nl") . uncomment to filter for a specific language
} group by ?provenance ?language
ORDER BY ?language
```
(https://nightly.yasgui.triply.cc/#query=PREFIX%20rdf%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0APREFIX%20rdfs%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0APREFIX%20rdf%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0APREFIX%20rdfs%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0APREFIX%20dct%3A%20%3Chttp%3A%2F%2Fpurl.org%2Fdc%2Fterms%2F%3E%0APREFIX%20hisco%3A%20%3Chttps%3A%2F%2Fiisg.amsterdam%2Fhisco%2F%3E%0APREFIX%20skos%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0APREFIX%20prov%3A%20%3Chttp%3A%2F%2Fwww.w3.org%2Fns%2Fprov%23%3E%0A%0ASELECT%20distinct%20%3Fprovenance%20(count(%3Fprovenance)%20as%20%3Fprov_count)%20%3Flanguage%0AWHERE%20%7B%0A%09hisco%3AjobHoard%20skos%3Amember%20%3Fjob%20.%0A%20%20%09%3Fjob%20skos%3AprefLabel%20%3Flabel%20.%0A%20%20%20%20hisco%3Acategory%20skos%3Amember%20%3Fhisco.%0A%20%20%20%20OPTIONAL%20%7Bhisco%3Ajob%20skos%3AhiddenLabel%20%3Flabel%7D%20.%0A%20%20%20%20%3Fjob%20prov%3AwasDerivedFrom%20%3Fprovenance%20.%0A%20%20%20%20BIND(lang(%3Flabel)%20AS%20%3Flanguage)%20.%0A%20%20%09%23%20FILTER(lang(%3Flabel)%20%3D%20%22nl%22)%20.%20uncomment%20to%20filter%20for%20a%20specific%20language%0A%7D%20group%20by%20%3Fprovenance%20%3Flanguage%0AORDER%20BY%20%3Flanguage&endpoint=https%3A%2F%2Fdruid.datalegend.net%2F_api%2Fdatasets%2FdataLegend%2FjobHoard%2Fservices%2Fmonitor%2Fsparql&requestMethod=POST&tabTitle=Query&headers=%7B%7D&contentTypeConstruct=text%2Fturtle%2C*%2F*%3Bq%3D0.9&contentTypeSelect=application%2Fsparql-results%2Bjson%2C*%2F*%3Bq%3D0.9&outputFormat=table)
