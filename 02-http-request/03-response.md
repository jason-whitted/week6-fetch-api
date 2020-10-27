# HTTP Response
Wikipedia sees that you are requesting Nacho Libre, which of course receives a priority response.  It then packages up the response message that looks something like this:

```http
HTTP/1.1 200
status: 200
date: Fri, 23 Oct 2020 22:04:08 GMT
server: mw2309.codfw.wmnet
x-content-type-options: nosniff
p3p: CP="See https://en.wikipedia.org/wiki/Special:CentralAutoLogin/P3P for more info."
content-language: en
vary: Accept-Encoding,Cookie,Authorization
x-request-id: fc7bdcf3-04ae-4361-bcbd-feff7faeca1f
last-modified: Fri, 23 Oct 2020 14:52:13 GMT
content-type: text/html; charset=UTF-8
content-encoding: gzip
age: 1230
x-cache: cp2033 miss, cp2035 hit/5
x-cache-status: hit-front
server-timing: cache;desc="hit-front"
strict-transport-security: max-age=106384710; includeSubDomains; preload
report-to: { "group": "wm_nel", "max_age": 86400, "endpoints": [{ "url": "https://intake-logging.wikimedia.org/v1/events?stream=w3c.reportingapi.network_error&schema_uri=/w3c/reportingapi/network_error/1.0.0" }] }
nel: { "report_to": "wm_nel", "max_age": 86400, "failure_fraction": 0.05, "success_fraction": 0.0}
x-client-ip: 174.51.68.223
cache-control: private, s-maxage=0, max-age=0, must-revalidate
accept-ranges: bytes
content-length: 21514
X-DNS-Prefetch-Control: off
```

The status code 200 is a response that everything is OK.

Just like the request may send in some meta information, the response may also.  This is also referred to as the **header** of the response.

The content-length is 21,514 bytes.  This is the **body** of the response.  Reading this requires a stream to be opened to the server.

The `content-type` in the header specified `text/html; charset=UTF-8`.  Chrome knows to handle this as an HTML page and it begins to interpret and render the HTML the screen as the bytes are being read.

As it is reading the content it may reference other resources:
```html
<link rel="stylesheet" href="/w/load.php?lang=en&amp;modules=ext.cite.styles%7Cext.uls.interlanguage%7Cext.visualEditor.desktopArticleTarget.noscript%7Cext.wikimediaBadges%7Cjquery.makeCollapsible.styles%7Cmediawiki.toc.styles%7Cskins.vector.styles.legacy%7Cwikibase.client.init&amp;only=styles&amp;skin=vector">

<script async="" src="/w/load.php?lang=en&amp;modules=startup&amp;only=scripts&amp;raw=1&amp;skin=vector"></script>

<img alt="Nachopost.jpg" src="//upload.wikimedia.org/wikipedia/en/3/35/Nachopost.jpg" decoding="async" width="200" height="296" class="thumbborder" data-file-width="200" data-file-height="296">
```

Each of these resources are then sent off as new HTTP Requests and repeat the process.

These requests / response call all be seen in the Network tab of Chrome Developer Tools.
