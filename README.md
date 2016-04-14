# serp

This module allows to execute search on Google with or without proxies.
It provides different options for scraping the google results.

# Installation

``` bash
$ npm install serp -S
```


# Simple usage

``` javascript
var serp = require("serp");

var options = {
  host : "google.be",
  qs : {
    q : "test",
    filter : 0,
    pws : 0
  },
  num : 1000
};

serp.search(options, function(error, links){
      console.log(links);
});
```

*Understanding the options structure :*
- For google.com, the param host is not necessary.
- qs can contain the usual Google search parameters : https://moz.com/ugc/the-ultimate-guide-to-the-google-search-parameters.
- options.qs.q is the keyword
- num is the number of desired results (defaut is 10).
- The options object can also contain all request options like http headers, ... . SERP is using the request module :  https://github.com/request/request
- The user agent is not mandatory. Default value will be : 'Mozilla/5.0 (Windows NT 6.1; WOW64; rv:40.0) Gecko/20100101 Firefox/40.1'


## With proxy

You need to add the proxy reference in the options

``` javascript
var serp = require("serp");

var options = {
  qs : {
    q : "test",
  },
  proxy : "http://username:password@host:port"  
};

serp.search(options, function(error, links){
      console.log(links);
});
```


## Delay between requests

It is possible to add a delay between each request made on Google with the option *delay* (value in ms).


``` javascript
var serp = require("serp");

var options = {

  qs : {
    q : "test"
  },
  num : 1000,
  delay : 2000 // in ms
};

serp.search(options, function(error, links){
      console.log(links);
});
```
