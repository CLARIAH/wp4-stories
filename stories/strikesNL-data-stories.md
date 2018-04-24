# Strikes: collective action in times of economic progress?

```
# endpoint: https://api.druid.datalegend.net/datasets/dataLegend/strikes/services/strikes/sparql
```

An often heard claim in the social sciences is that strikes occur most often,
not during crises, but in the prosperous years after. As this is counter intuitive,
it sounds like an interesting problem. One reason that might explain this
phenomenon is that people only strike when they dare to. In economic prosperous
times the job market has a shortage, and employees can demand more favourable
conditions. Another argument is that of relative deprivation. When a more
prosperous era starts, not everyone will benefit at the same time and degree.
Thus people may become unhappy, when they see others already benefitting from
the improved conditions and as a result they will strike for equal benefits.

To see whether these arguments makes sense, we turn to the Netherlands, in the
period 1970-1985. The Netherlands was struck by two crises after which more
prosperous periods followed.

Figure 1 below shows the total number of strikes in the Netherlands and the
GDP per capita. [NB: GDP per capita not in query as there is no data on it]

```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX gg: <http://www.gemeentegeschiedenis.nl/gg-schema#>
PREFIX strikes: <https://iisg.amsterdam/vocab/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT ?year (COUNT(?strike) as ?strikes) {
  ?strike strikes:date ?sdate .
  BIND (substr (STR(?sdate),1,4) as ?year)
  FILTER (?sdate >= '1972-01-01'^^xsd:date && ?sdate < '1985-01-01'^^xsd:date)
}
ORDER BY ?year
```
There's no apparent correlation between GDP and the number of strikes. But to be
fair, we have regarded strikes all to be the same (e.g. same type, same number
of persons involved, equal length and same industry). One way to distinguish
between types is to study the different number of strikes by industry.
```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX gg: <http://www.gemeentegeschiedenis.nl/gg-schema#>
PREFIX strikes: <https://iisg.amsterdam/vocab/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>

SELECT ?year ?stype (COUNT(?strike) as ?strikes) (GROUP_CONCAT(?sdate; separator = ";") as ?s_date) {
  ?strike strikes:date ?sdate .
  ?strike strikes:sector ?stype .
  BIND (substr (STR(?sdate),1,4) as ?year)
  FILTER (?sdate >= '1972-01-01'^^xsd:date && ?sdate < '1985-01-01'^^xsd:date)
}
ORDER BY ?year DESC(?strikes)
```
[It would be great if the above could result in a multi-line graph: e.g. a line
per type of strikes]

We can also look at the regional distribution of strikes. This is another way to
visualize the above, as types of industries are clustered regionally.
```
PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
PREFIX gg: <http://www.gemeentegeschiedenis.nl/gg-schema#>
PREFIX strikes: <https://iisg.amsterdam/vocab/>
PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
PREFIX geo: <http://www.opengis.net/ont/geosparql#>

SELECT ?muni ?polygon ?wktColor  (COUNT(?strike) as ?strikes) (GROUP_CONCAT(?sdate; separator = ";") as ?wktLabel) {
  ?strike strikes:place ?splace .
  ?strike strikes:date ?sdate .
  ?muni rdf:type gg:Municipality .
  ?muni rdfs:label ?ggplace .
  #?muni geo:hasGeometry / geo:asWKT ?polygon . # not in grouping result set error

  FILTER (?sdate >= '1972-01-01'^^xsd:date && ?sdate < '1985-01-01'^^xsd:date)
  FILTER(str(?splace) = str(?ggplace))

  #bind (concat('viridis,', xsd:float(?strikes)) as ?wktColor) #used in the result set outside aggregate and not mentioned in GROUP BY clause
}
GROUP BY ?muni
ORDER BY DESC(?strikes)
LIMIT 10
```
