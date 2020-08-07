A social network for users to share and view nearby posts. This is the API part, [check here](https://github.com/mfishoo/aroung_frontend)for the front-end features.<br/>
Deploy on [Google App Engine](https://erudite-scanner-276717.wl.r.appspot.com).

## Build With
- [Golang](https://golang.org/)
- [ElasticSearch](https://www.elastic.co/what-is/elasticsearch) - open source search and analytics engine
- [Google Vision API](https://cloud.google.com/vision) - pre-trained machine learning models classify images into predefined categories.
- [JWT](https://jwt.io/) - user authentication 

## APIs

Feature       | Method        | Endpoint
------------- | ------------- | ----------
User register | POST          | /signup
User login    | POST          | /login
Create a post | POST          | /post
Search posts (within a range) | GET           | /search?lat=xx&lon=xx&range=xx
Filter image posts with faces | GET | /cluster?term=face



## DB Index
#### User
```
{
  "username": {"type": "keyword"},
  "password": {"type": "keyword", "index": false},
  "age":      {"type": "long", "index": false},
  "gender":   {"type": "keyword", "index": false}
}
```

#### Post
```
{
  "user":     { "type": "keyword", "index": false },
  "message":  { "type": "keyword", "index": false },
  "location": { "type": "geo_point" },
  "url":      { "type": "keyword", "index": false },
  "type":     { "type": "keyword", "index": false },
  "face":     { "type": "float" }
}
```
