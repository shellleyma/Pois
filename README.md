# Pois
Whois client for Python with Proxy


## Why use Pois over other libraries?


so why use Pois over robust libraries like [pythonwhois](https://github.com/joepie91/python-whois), [pywhois](https://bitbucket.org/richardpenman/pywhois)...


1. Pois uses a complete list of whois servers for all available tlds and if it didn't find any whois server for a specific brand new tld
 it query `whois.iana.org` to get tld whois server (`tlds.json` file will be updated when new whois servers fetched)

 
2. Pois accept http and socks proxies, thank to `pysocks`


3. Pois accepts user defined whois server to query desired domain


4. Pois accepts a timeout for whois operation, some whois servers time out after user quota exceeded


5. Pois parses result and if it finds a Registrar whois server, re-whois that server to get complete whois (thick whois)




## How to use it

copy `pois` folder anywhere you want then import it.



## How to use it with Proxy

just pass `proxy_info` dict with these arguments to `Pois()` <br>
`proxy_type`, `addr`, `port`, `username`, `password`<br>
proxy_type can be `http`,`socks4` or `socks5`


```python

from pois import *

# without proxy
try:
    p = Pois(timeout=10)
    result = p.fetch(domain='github.com', whois_server=None,)
except Exception as err:
    print(str(err))
    
    
# with proxy
try:
    proxy_info = {'proxy_type':'http','addr':'localhost', 'port':8118}
    p = Pois(timeout=10, proxy_info=proxy_info)
    result = p.fetch(domain='github.com', whois_server=None,)
except Exception as err:
    print(str(err))
    
    
```


## Exceptions


```
TldsFileError, BadDomainError, NoWhoisServerFoundError, SocketTimeoutError, SocketError

```





