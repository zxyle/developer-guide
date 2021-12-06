## 聚合查询
## 示例:
```
GET /bank/_search
```
```json
{
  "query": {
    "match": {
      "address": "mill"
    }
  },
  "aggs": {
    "ageAgg": {
      "terms": {
        "field": "age",
        "size": 10
      }
    },
    "ageAvg": {
      "avg": {
        "field": "age"
      }
    }
  }
}
```

## 嵌套查询
netsted