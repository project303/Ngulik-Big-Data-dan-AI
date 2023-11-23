It could be done by creating new config file in: /etc/security/limits.d/ (to be on safe side when upgrading etc). For example:

```
/etc/security/limits.d/nofile.conf
```

with content as written :

```
*    soft    nofile 8192
*    hard    nofile 8192
```
