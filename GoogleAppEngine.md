# Helper Function #

```
def getGeoIPCode(ipaddr):
   from google.appengine.api import memcache
   memcache_key = "gip_%s" % ipaddr
   data = memcache.get(memcache_key)
   if data is not None:
      return data

   geoipcode = ''
   from google.appengine.api import urlfetch
   try:
      fetch_response = urlfetch.fetch(
            'http://geoip.wtanaka.com/cc/%s' % ipaddr)
      if fetch_response.status_code == 200:
         geoipcode = fetch_response.content
   except urlfetch.Error, e:
      pass

   if geoipcode:
      memcache.set(memcache_key, geoipcode)
   return geoipcode
```

# Django Helper for Google App Engine #

```
getGeoIPCode(request.META['REMOTE_ADDR'])
```


# WSGI #

```
getGeoIPCode(self.request.remote_addr)
```