```shell
docker-compose -f docker-compose.yml up -d

docker exec -it hbase-master /bin/bash

hbase shell

scan 'wiki_small', {COLUMNS=>"page:page_title", FILTER=>"ValueFilter(=,'substring:(disambiguation)')"}

scan 'wiki_small', {COLUMNS => 'page:page_title', FILTER => "ValueFilter(=, 'substring: (disambiguation)|')"}

scan 'wiki_small', {COLUMNS=>['author:timestamp','page:page_title'], FILTER=>"SingleColumnValueFilter('page', 'page_title', =, 'substring:list of') AND (SingleColumnValueFilter('author', 'timestamp', =, 'substring:2020'))"}

scan 'wiki_small', {COLUMNS=>'page:page_title', FILTER=>"ValueFilter(=,'regexstring:(?i)(disambiguation(?![)][|])|[^(]disambiguation[)][|])')"}

```

