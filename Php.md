# PHP Helper Function #

```
function get_geo_ip_code($ipaddr)
{
   return file_get_contents("http://geoip.wtanaka.com/cc/$ipaddr");
}
```

# PHP Example Code #

```
get_geo_ip_code($_SERVER['REMOTE_ADDR']);
```