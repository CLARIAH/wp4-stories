Growth and inequality
=====================

```
# endpoint: https://api.druid.datalegend.net/datasets/dataLegend/clio-infra/services/clio-infra/sparql
```

Why are some countries rich and others poor? Because economic growth is a long-term process, history is part of the answer. To help understand long-term economic growth, economic historians have been working on reconstructing historical national accounts. Collecting such data in a comparable way (expressing them in at one level of prices) was started by Angus Maddison. Today it is a collaborative project that continues under his name.

The differences in today's world are very big. A small group of rich countries is up to ten times richer than a lot of poor countries.

```{sparl out = Histogram}
PREFIX cliovocab: <https://iisg.amsterdam/clio/vocab/>
PREfix sdmxdim: <http://purl.org/linked-data/sdmx/2009/dimension#>

SELECT * WHERE {
  ?sub cliovocab:GDP_per_Capita ?gdp_per_country .
  ?sub sdmxdim:refPeriod "2010-01-01"^^xsd:gYear .
}
```
[link](https://druid.datalegend.net/dataLegend/clio-infra/services/clio-infra#query=PREFIX+cliovocab%3A+%3Chttps%3A%2F%2Fiisg.amsterdam%2Fclio%2Fvocab%2F%3E%0APREfix+sdmxdim%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0A%0ASELECT+*+WHERE+%7B%0A++%3Fsub+cliovocab%3AGDP_per_Capita+%3Fgdppc+.%0A++%3Fsub+sdmxdim%3ArefPeriod+%222010-01-01%22%5E%5Exsd%3AgYear+.%0A%7D+&contentTypeConstruct=text%2Fturtle&contentTypeSelect=application%2Fsparql-results%2Bjson&endpoint=https%3A%2F%2Fdruid.datalegend.net%2F_api%2Fdatasets%2FdataLegend%2Fclio-infra%2Fservices%2Fclio-infra%2Fsparql&requestMethod=POST&tabTitle=Query&headers=%7B%7D&outputFormat=gchart&outputSettings=%7B%22chartConfig%22%3A%7B%22options%22%3A%7B%22hAxis%22%3A%7B%22useFormatFromData%22%3Atrue%2C%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%7D%2C%22legacyScatterChartLabels%22%3Atrue%2C%22booleanRole%22%3A%22certainty%22%2C%22histogram%22%3A%7B%22hideBucketItems%22%3Atrue%7D%2C%22vAxes%22%3A%5B%7B%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%2C%22useFormatFromData%22%3Atrue%7D%2C%7B%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%2C%22useFormatFromData%22%3Atrue%7D%5D%2C%22legend%22%3A%22right%22%2C%22width%22%3A600%2C%22height%22%3A371%7D%2C%22state%22%3A%7B%7D%2C%22view%22%3A%7B%22columns%22%3Anull%2C%22rows%22%3Anull%7D%2C%22isDefaultVisualization%22%3Afalse%2C%22chartType%22%3A%22Histogram%22%7D%2C%22motionChartState%22%3Anull%7D)

In 1900 these difference were much smaller:
```{sparl out = Histogram}
PREFIX cliovocab: <https://iisg.amsterdam/clio/vocab/>
PREfix sdmxdim: <http://purl.org/linked-data/sdmx/2009/dimension#>

SELECT * WHERE {
  ?sub cliovocab:GDP_per_Capita ?gdppc .
  ?sub sdmxdim:refPeriod "1900-01-01"^^xsd:gYear .
}
```{sparql out = Histogram}
[link](https://druid.datalegend.net/dataLegend/clio-infra/services/clio-infra#query=PREFIX+cliovocab%3A+%3Chttps%3A%2F%2Fiisg.amsterdam%2Fclio%2Fvocab%2F%3E%0APREfix+sdmxdim%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0A%0ASELECT+*+WHERE+%7B%0A++%3Fsub+cliovocab%3AGDP_per_Capita+%3Fgdppc+.%0A++%3Fsub+sdmxdim%3ArefPeriod+%221900-01-01%22%5E%5Exsd%3AgYear+.%0A%7D%0A&contentTypeConstruct=text%2Fturtle&contentTypeSelect=application%2Fsparql-results%2Bjson&endpoint=https%3A%2F%2Fdruid.datalegend.net%2F_api%2Fdatasets%2FdataLegend%2Fclio-infra%2Fservices%2Fclio-infra%2Fsparql&requestMethod=POST&tabTitle=distr1900&headers=%7B%7D&outputFormat=gchart&outputSettings=%7B%22chartConfig%22%3A%7B%22options%22%3A%7B%22hAxis%22%3A%7B%22useFormatFromData%22%3Atrue%2C%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%7D%2C%22legacyScatterChartLabels%22%3Atrue%2C%22booleanRole%22%3A%22certainty%22%2C%22histogram%22%3A%7B%22hideBucketItems%22%3Atrue%7D%2C%22vAxes%22%3A%5B%7B%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%2C%22useFormatFromData%22%3Atrue%7D%2C%7B%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%2C%22useFormatFromData%22%3Atrue%7D%5D%2C%22legend%22%3A%22right%22%2C%22width%22%3A600%2C%22height%22%3A371%7D%2C%22state%22%3A%7B%7D%2C%22view%22%3A%7B%22columns%22%3Anull%2C%22rows%22%3Anull%7D%2C%22isDefaultVisualization%22%3Afalse%2C%22chartType%22%3A%22Histogram%22%7D%2C%22motionChartState%22%3Anull%7D)

And in 1800 they were smaller still.
```{sparl, out = Histogram}
PREFIX cliovocab: <https://iisg.amsterdam/clio/vocab/>
PREfix sdmxdim: <http://purl.org/linked-data/sdmx/2009/dimension#>

SELECT * WHERE {
  ?sub cliovocab:GDP_per_Capita ?gdppc .
  ?sub sdmxdim:refPeriod "1800-01-01"^^xsd:gYear .
}
```
[link](https://druid.datalegend.net/dataLegend/clio-infra/services/clio-infra#query=PREFIX+cliovocab%3A+%3Chttps%3A%2F%2Fiisg.amsterdam%2Fclio%2Fvocab%2F%3E%0APREfix+sdmxdim%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0A%0ASELECT+*+WHERE+%7B%0A++%3Fsub+cliovocab%3AGDP_per_Capita+%3Fgdppc+.%0A++%3Fsub+sdmxdim%3ArefPeriod+%221800-01-01%22%5E%5Exsd%3AgYear+.%0A%7D%0A&contentTypeConstruct=text%2Fturtle&contentTypeSelect=application%2Fsparql-results%2Bjson&endpoint=https%3A%2F%2Fdruid.datalegend.net%2F_api%2Fdatasets%2FdataLegend%2Fclio-infra%2Fservices%2Fclio-infra%2Fsparql&requestMethod=POST&tabTitle=distr1800&headers=%7B%7D&outputFormat=gchart&outputSettings=%7B%22chartConfig%22%3A%7B%22options%22%3A%7B%22hAxis%22%3A%7B%22useFormatFromData%22%3Atrue%2C%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%7D%2C%22legacyScatterChartLabels%22%3Atrue%2C%22booleanRole%22%3A%22certainty%22%2C%22histogram%22%3A%7B%22hideBucketItems%22%3Atrue%7D%2C%22vAxes%22%3A%5B%7B%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%2C%22useFormatFromData%22%3Atrue%7D%2C%7B%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%2C%22useFormatFromData%22%3Atrue%7D%5D%2C%22legend%22%3A%22right%22%2C%22width%22%3A600%2C%22height%22%3A371%7D%2C%22state%22%3A%7B%7D%2C%22view%22%3A%7B%22columns%22%3Anull%2C%22rows%22%3Anull%7D%2C%22isDefaultVisualization%22%3Afalse%2C%22chartType%22%3A%22Histogram%22%7D%2C%22motionChartState%22%3Anull%7D)

Locations on map: Africa and Asia very poor
now mostly Africa
```{sparql out = map}
PREFIX skos: <http://www.w3.org/2004/02/skos/core#>
PREFIX geo: <http://www.opengis.net/ont/geosparql#>
PREFIX cliovocab: <https://iisg.amsterdam/clio/vocab/>
PREFIX sdmxdim: <http://purl.org/linked-data/sdmx/2009/dimension#>
SELECT ?gdp ?gdpindex ?wktColor ?wkt WHERE {
  ?refarea skos:exactMatch / geo:hasGeometry / geo:asWKT ?wkt .
  ?sub cliovocab:GDP_per_Capita ?gdp .
  ?sub sdmxdim:refArea ?refarea .
  ?sub sdmxdim:refPeriod "2010-01-01"^^xsd:gYear .
  bind(?gdp / 40000 as ?gdpindex ) .
  bind(concat('viridis,', str(?gdpindex)) as ?wktColor)
}
```
[link](https://druid.datalegend.net/dataLegend/clio-infra/services/clio-infra#query=PREFIX+skos%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2004%2F02%2Fskos%2Fcore%23%3E%0APREFIX+geo%3A+%3Chttp%3A%2F%2Fwww.opengis.net%2Font%2Fgeosparql%23%3E%0APREFIX+cliovocab%3A+%3Chttps%3A%2F%2Fiisg.amsterdam%2Fclio%2Fvocab%2F%3E%0APREFIX+sdmxdim%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0ASELECT+%3Fgdp+%3Fgdpindex+%3FwktColor+%3Fwkt+WHERE+%7B%0A++%3Frefarea+skos%3AexactMatch+%2F+geo%3AhasGeometry+%2F+geo%3AasWKT+%3Fwkt+.%0A++%3Fsub+cliovocab%3AGDP_per_Capita+%3Fgdp+.%0A++%3Fsub+sdmxdim%3ArefArea+%3Frefarea+.%0A++%3Fsub+sdmxdim%3ArefPeriod+%222010-01-01%22%5E%5Exsd%3AgYear+.%0A++bind(%3Fgdp+%2F+40000+as+%3Fgdpindex+)+.%0A++bind(concat('viridis%2C'%2C+str(%3Fgdpindex))+as+%3FwktColor)%0A%7D%0A&contentTypeConstruct=text%2Fturtle&contentTypeSelect=application%2Fsparql-results%2Bjson&endpoint=https%3A%2F%2Fdruid.datalegend.net%2F_api%2Fdatasets%2FdataLegend%2Fclio-infra%2Fservices%2Fclio-infra%2Fsparql&requestMethod=POST&tabTitle=mapit&headers=%7B%7D&outputFormat=leaflet)

Old-school growth theory (Rostow) suggested "take-of", some moment where modern economic growth began, e.g. growth
china's industrialistion is a good example. In an ideal world there would be dates on the x-axis but the gYear bug strikes again...
```{sparql out LineChart}
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX cliovocab: <https://iisg.amsterdam/clio/vocab/>
PREFIX sdmxdim: <http://purl.org/linked-data/sdmx/2009/dimension#>
prefix clioctr: <https://iisg.amsterdam/clio/code/country/>

SELECT ?year ?gdp WHERE {
  ?sub cliovocab:GDP_per_Capita ?gdp .
  ?sub sdmxdim:refPeriod ?year .
  ?sub sdmxdim:refArea / cliovocab:ccode ?ccode .
  values ?ccode {clioctr:156}
}
order by ?year
```
[link](https://druid.datalegend.net/dataLegend/clio-infra/services/clio-infra#query=PREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0APREFIX+cliovocab%3A+%3Chttps%3A%2F%2Fiisg.amsterdam%2Fclio%2Fvocab%2F%3E%0APREFIX+sdmxdim%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0Aprefix+clioctr%3A+%3Chttps%3A%2F%2Fiisg.amsterdam%2Fclio%2Fcode%2Fcountry%2F%3E%0A%0ASELECT+%3Fyear+%3Fgdp+WHERE+%7B%0A++%3Fsub+cliovocab%3AGDP_per_Capita+%3Fgdp+.%0A++%3Fsub+sdmxdim%3ArefPeriod+%3Fyear+.%0A++%3Fsub+sdmxdim%3ArefArea+%2F+cliovocab%3Accode+%3Fccode+.%0A++values+%3Fccode+%7Bclioctr%3A156%7D%0A%7D+%0Aorder+by+%3Fyear&contentTypeConstruct=text%2Fturtle&contentTypeSelect=application%2Fsparql-results%2Bjson&endpoint=https%3A%2F%2Fdruid.datalegend.net%2F_api%2Fdatasets%2FdataLegend%2Fclio-infra%2Fservices%2Fclio-infra%2Fsparql&requestMethod=POST&tabTitle=takeoff_china&headers=%7B%7D&outputFormat=gchart&outputSettings=%7B%22chartConfig%22%3A%7B%22options%22%3A%7B%22hAxis%22%3A%7B%22useFormatFromData%22%3Atrue%2C%22viewWindow%22%3Anull%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%2C%22viewWindowMode%22%3Anull%7D%2C%22legacyScatterChartLabels%22%3Atrue%2C%22vAxes%22%3A%5B%7B%22useFormatFromData%22%3Atrue%2C%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%7D%2C%7B%22useFormatFromData%22%3Atrue%2C%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%7D%5D%2C%22curveType%22%3A%22%22%2C%22booleanRole%22%3A%22certainty%22%2C%22lineWidth%22%3A2%2C%22legend%22%3A%22right%22%2C%22width%22%3A600%2C%22height%22%3A371%7D%2C%22state%22%3A%7B%7D%2C%22view%22%3A%7B%22columns%22%3A%5B%7B%22calc%22%3A%22emptyString%22%2C%22sourceColumn%22%3A0%2C%22type%22%3A%22string%22%7D%2C0%2C1%5D%2C%22rows%22%3Anull%7D%2C%22isDefaultVisualization%22%3Afalse%2C%22chartType%22%3A%22LineChart%22%7D%2C%22motionChartState%22%3Anull%7D)

Today we know that this is incorrect for the first industrialising countries. They were richer before industrialisation than many of today's developing countries.

```{sparql out = LineChart}
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX cliovocab: <https://iisg.amsterdam/clio/vocab/>
PREFIX sdmxdim: <http://purl.org/linked-data/sdmx/2009/dimension#>
prefix clioctr: <https://iisg.amsterdam/clio/code/country/>

SELECT ?year ?gdp_gbr ?gdp_nld ?gdp_uga WHERE {
  ?gbr cliovocab:GDP_per_Capita ?gdp_gbr ;
     sdmxdim:refPeriod ?year ;
     sdmxdim:refArea / cliovocab:ccode clioctr:826 .

  ?nld cliovocab:GDP_per_Capita ?gdp_nld ;
     sdmxdim:refPeriod ?year ;
     sdmxdim:refArea / cliovocab:ccode clioctr:528 .

  {optional{
      ?uga cliovocab:GDP_per_Capita ?gdp_uga ;
     sdmxdim:refPeriod ?year ;
     sdmxdim:refArea / cliovocab:ccode clioctr:800
    }}
}
```
[link](https://druid.datalegend.net/dataLegend/clio-infra/services/clio-infra#query=PREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0APREFIX+cliovocab%3A+%3Chttps%3A%2F%2Fiisg.amsterdam%2Fclio%2Fvocab%2F%3E%0APREFIX+sdmxdim%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0Aprefix+clioctr%3A+%3Chttps%3A%2F%2Fiisg.amsterdam%2Fclio%2Fcode%2Fcountry%2F%3E%0A%0ASELECT+%3Fyear+%3Fgdp_gbr+%3Fgdp_nld+%3Fgdp_uga+WHERE+%7B%0A++%3Fgbr+cliovocab%3AGDP_per_Capita+%3Fgdp_gbr+%3B%0A%09+sdmxdim%3ArefPeriod+%3Fyear+%3B%0A%09+sdmxdim%3ArefArea+%2F+cliovocab%3Accode+clioctr%3A826+.%0A++%0A++%3Fnld+cliovocab%3AGDP_per_Capita+%3Fgdp_nld+%3B%0A%09+sdmxdim%3ArefPeriod+%3Fyear+%3B%0A%09+sdmxdim%3ArefArea+%2F+cliovocab%3Accode+clioctr%3A528+.%0A++%0A++%7Boptional%7B%0A++++++%3Fuga+cliovocab%3AGDP_per_Capita+%3Fgdp_uga+%3B%0A%09+sdmxdim%3ArefPeriod+%3Fyear+%3B%0A%09+sdmxdim%3ArefArea+%2F+cliovocab%3Accode+clioctr%3A800%0A++++%7D%7D%0A%7D+%0A&contentTypeConstruct=text%2Fturtle&contentTypeSelect=application%2Fsparql-results%2Bjson&endpoint=https%3A%2F%2Fdruid.datalegend.net%2F_api%2Fdatasets%2FdataLegend%2Fclio-infra%2Fservices%2Fclio-infra%2Fsparql&requestMethod=POST&tabTitle=compare&headers=%7B%7D&outputFormat=gchart&outputSettings=%7B%22chartConfig%22%3A%7B%22options%22%3A%7B%22hAxis%22%3A%7B%22useFormatFromData%22%3Atrue%2C%22viewWindow%22%3Anull%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%2C%22viewWindowMode%22%3Anull%7D%2C%22legacyScatterChartLabels%22%3Atrue%2C%22vAxes%22%3A%5B%7B%22useFormatFromData%22%3Atrue%2C%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%7D%2C%7B%22useFormatFromData%22%3Atrue%2C%22viewWindow%22%3A%7B%22max%22%3Anull%2C%22min%22%3Anull%7D%2C%22minValue%22%3Anull%2C%22maxValue%22%3Anull%7D%5D%2C%22curveType%22%3A%22%22%2C%22booleanRole%22%3A%22certainty%22%2C%22lineWidth%22%3A2%2C%22legend%22%3A%22right%22%2C%22width%22%3A600%2C%22height%22%3A371%7D%2C%22state%22%3A%7B%7D%2C%22view%22%3A%7B%22columns%22%3A%5B%7B%22calc%22%3A%22emptyString%22%2C%22sourceColumn%22%3A0%2C%22type%22%3A%22string%22%7D%2C0%2C1%2C2%2C3%5D%2C%22rows%22%3Anull%7D%2C%22isDefaultVisualization%22%3Afalse%2C%22chartType%22%3A%22LineChart%22%7D%2C%22motionChartState%22%3Anull%7D)

Maddison's data should be used with some care. Besides more detailed issues about e.g. price indics applicability of a concept like GDP and, there is the fact that for a lot of countries, we lack good historical data. Such data was originally imputed and some of those values have survived. Best case scenario is that they are using proxies, but often they are just assumptions about income levels in such countries. Great care should for instance be take with all values of exactly "X00"

```{out = Table}
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX cliovocab: <https://iisg.amsterdam/clio/vocab/>
PREFIX sdmxdim: <http://purl.org/linked-data/sdmx/2009/dimension#>
SELECT * WHERE {
  ?sub cliovocab:GDP_per_Capita ?gdp .
  ?sub sdmxdim:refPeriod ?year
  filter(bif:mod(?gdp, 100)= 0) .
}
order by ?year
```
[link](https://druid.datalegend.net/dataLegend/clio-infra/services/clio-infra#query=PREFIX+rdf%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F1999%2F02%2F22-rdf-syntax-ns%23%3E%0APREFIX+rdfs%3A+%3Chttp%3A%2F%2Fwww.w3.org%2F2000%2F01%2Frdf-schema%23%3E%0APREFIX+cliovocab%3A+%3Chttps%3A%2F%2Fiisg.amsterdam%2Fclio%2Fvocab%2F%3E%0APREFIX+sdmxdim%3A+%3Chttp%3A%2F%2Fpurl.org%2Flinked-data%2Fsdmx%2F2009%2Fdimension%23%3E%0ASELECT+*+WHERE+%7B%0A++%3Fsub+cliovocab%3AGDP_per_Capita+%3Fgdp+.%0A++%3Fsub+sdmxdim%3ArefPeriod+%3Fyear%0A++filter(bif%3Amod(%3Fgdp%2C+100)%3D+0)+.%0A%7D+%0Aorder+by+%3Fyear&contentTypeConstruct=text%2Fturtle&contentTypeSelect=application%2Fsparql-results%2Bjson&endpoint=https%3A%2F%2Fdruid.datalegend.net%2F_api%2Fdatasets%2FdataLegend%2Fclio-infra%2Fservices%2Fclio-infra%2Fsparql&requestMethod=POST&tabTitle=100s&headers=%7B%7D&outputFormat=table)

Unfortunately, some of those are non-imputed values after all. These things are not precisely recorded in the dataset itself because ⁄⁄REASONS UNKNOWN.
