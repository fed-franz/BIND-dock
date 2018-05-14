# BIND-dock
Generic BIND server docker container

## Set-up
```sh
docker build -t binddock .
docker run --name binddock -d -t binddock
```

To test the DNS server:
```sh
$ BINDsrv=$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' binddock)
$ nslookup - $BINDsrv
> www.domain.com
Server:		172.17.0.2
Address:	172.17.0.2#53

Name:	www.domain.com
Address: 1.2.3.4
>
```
