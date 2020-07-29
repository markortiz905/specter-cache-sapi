# specter-cache-system-api

### Sample GET Request

header

```
X-Correlation-Id: rt30927105072320150615112557855 (required)
```

uri param:

```
key: provision-history9364000094 (required)
```

request url

```
http://cache-sapi.us-e2.cloudhub.io/api/entry/provision-history9364000094
```

### Sample Get Response (200)

```
{
"value": "1"
}
```

### 404 Cache Key not found

```
http status 404
```

------

### Sample PUT Request

header

```
X-Correlation-Id: rt30927105072320150615112557855 (required)
```

uri param:

```
key: context_9364000094 (required)
```

body

```
{
    "prefix": "provision-history",
    "value": "1",
    "expiration": 1607731200
}
```

request url

```
http://cache-sapi.us-e2.cloudhub.io/api/entry/9364000094
```

### Sample PUT Response (200)

```
{
  "message": "success",
  "key": "provision-history9364000094"
}
```


