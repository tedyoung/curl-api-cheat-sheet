# Basic GET

## GET a single resource via its URI

Default operation is a GET:

    curl http://api.example.com:8080/statuses/1234

## GET multiple resources where IDs are in a range

Use square brackets with a dashed range:

    curl http://api.example.com:8080/items/[1230-1234]

## GET multiple resources where IDs aren't in a range

Use curly braces with comma-delimited strings:

    curl http://api.example.com:8080/products/{abc,def,ghi}/status

# Using HTTP Headers

## Accept only the application/json content-type

Use the header option: `-H` or `--header`

    curl -H 'Accept: application/json' http://api.example.com:8080/items/1234

## Add multiple headers

Use multiple `-H` options:

    curl -H 'Accept: application/json' -H 'Accept-Encoding: gzip' http://api.example.com:8080/products/a1b2c3ef/status

Note: the output from this is likely to be unreadable, because it's gzipped!

More likely you'd use this with ETags:

    curl -H 'Accept: application/json' -H 'If-None-Match: "1cc044-172-3d9aee80"' http://api.example.com:8080/products/a1b2c3ef/status
