# Requirements

* Docker
* Hostfile routing grpc.test.example.com to localhost

### Run Traefik

But change the path of the mount first
```
docker run --rm -v /Users/manuelzapf/Projects/grpc-go/grpc-go/examples/route_guide/traefik:/etc/conf -v /Users/manuelzapf/Projects/grpc-go/grpc-go/examples/data/x509/:/etc/certs  -p 80:80 -p 443:443 -p 8000:8000 traefik:2.4 --configFile=/etc/conf/static.toml
```

### Run Server
```
go run server/server.go -tls=true
```

### Run Client(s)

```
go run client/client.go --server_addr=grpc.test.example.com:443 --server_host_override=grpc.test.example.com -tls=true
```