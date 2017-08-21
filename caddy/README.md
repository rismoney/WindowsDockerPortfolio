# Caddy

[Caddy](https://caddyserver.com) is the HTTP/2 web server with automatic HTTPS.

## Caddy Documentation

* [Guide](https://caddyserver.com/docs)
* [Examples](https://github.com/caddyserver/examples)

## Build with optional build arg for proxy:
```
docker build --build-arg HTTP_PROXY="http://proxy.example.com:9090" -t tpcaddy .
```

## Run the container

```
docker run --name caddy -d -p 8080:80 caddy:0.10.5 -rm
```
