# sparql
```sparql
select distinct ?city ?cityLabel ?pop ?at
where {
    ?city wdt:P131 wd:Q20937.

    { ?city wdt:P31 wd:Q29045252. }
    union
    { ?city wdt:P31/wdt:P279* wd:Q515. }
    union
    { ?city wdt:P31 wd:Q17143371. }

    optional {
        ?city p:P1082 ?popStatm.
        
        ?popStatm ps:P1082 ?pop.
        ?popStatm pq:P585 ?at.
    }

    service wikibase:label {
        bd:serviceParam wikibase:language "ko, en".
    }
}
order by desc(?pop)
```
