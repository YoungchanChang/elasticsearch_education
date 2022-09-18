
### Analyzer

- 환경설정("settings")에서 분석기 환경설정 진행

```
PUT blogs_test
{
  "settings": {
    "analysis": {
      "analyzer": {
        "content_analyzer": {
          "tokenizer": "standard",
          "filter": ["lowercase"],
          "char_filter": ["html_strip"]
        }
      }
    }
  }
}
```

### test Analyzer

```
GET blogs_test/_analyze
{
  "analyzer": "content_analyzer",
  "text":     "<b>Is</b> this <a href='/blogs'>clean</a> text?"
}
```


### Mapping


```
PUT test_blogs
{
  "mappings": {
    "properties": {
      "@timestamp": {
        "type": "date"
      },
      "abstract": {
        "type": "text"
      },
      "author": {
        "type": "keyword"
      },
        ...
    }
  }
}
```

### Mapping paramters

```
PUT blogs_fixed2
{
  "mappings": {
    "_meta": {
      "created_by": "Elastic Student"
    },
    "properties": {
      "authors": {
        "properties": {
          "company": {
            "type": "text",
            "fields": {
              "keyword": {
                "type": "keyword",
                "ignore_above": 256
              }
            }
          },
          "uid": {
            "enabled": false
          }
        }
      },
      "content": {
        "type": "text",
        "analyzer": "content_analyzer"
      },
      "publish_date": {
        "type": "date",
        "format": "iso8601"
      },
      "search_tags": {
        "type": "keyword",
        "doc_values": false
      },
      "tags": {
        "properties": {
          "elastic_stack": {
            "type": "keyword",
            "copy_to": "search_tags"
          },
          "industry": {
            "type": "keyword",
            "copy_to": "search_tags"\
            ...
        }
      },
        ...
    }
  }
}


```