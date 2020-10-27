# HTTP Request

Chrome packages up your request.  It creates a message signifying that you are trying to `GET` information, what URL you are requesting, and also adds some meta information such as `User-Agent` that the server may need to know.

The request looks something like this:
```http
GET https://en.wikipedia.org/wiki/Nacho_Libre
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.111 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
```

The meta information is referred to as the **header** of the request.

This request is routed via **Domain Name System** (DNS).  

It may first go to a root `org` server, which looks up the domain `wikipedia.org` and forwards it on.  

There, `wikipedia.org` may route the request to the the subdomain `en.wikipedia.org` server.  

Finally the request is pawned off to one of Wikipedia's servers for processing.
