# node request.js demo

```javascript
// for use with request.js ...
const request = require('request');
const cheerio = require('cheerio')
const async = require('async')

function parseHtml(html){
  var $ = cheerio.load(html)
  const arr = [];
  $('ul[class=list1] li').each(function(i, elem) {
    arr[i] = $(this).text();
  });
  return arr
}
request('http://127.0.0.1/test/', function (error, response, body) {
  if(response.statusCode === 200){
    var html = parseHtml(body)
    console.log(html)
  }
});
```