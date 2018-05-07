# pREST issue 299

Repo to test issue 299

## Running

```
PREST_PG_USER=postgres PREST_PG_DATABASE=prest PREST_PG_PORT=5432 PREST_HTTP_PORT=3010 PREST_QUERIES_LOCATION=./queries PREST_JWT_DEFAULT=false ./prest
```

## Tests

### Pass values inside body using cURL

```
curl -XPOST "http://localhost:3010/_QUERIES/test/insert" -d '{"id":1, "name":"test issue 299"}'
```

It fails responding it below.

```
{
	"error": "could not execute sql pq: invalid input syntax for integer: \"\u003cno value\u003e\", INSERT INTO \"Reply\" (id, name) VALUES('\u003cno value\u003e','\u003cno value\u003e')"
}
```

### Pass values inside querystring using cURL

```
curl -XPOST "http://localhost:3010/_QUERIES/test/insert?id=2&name=test+issue+299"
```

It runs as expected.

```
{"rows_affected":1}
```