# BIND-dock
Generic BIND server docker container

## Set-up
```sh
docker build -t binddock .
docker run --name binddock -i -d -t binddock
```

## Test
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
## Interactive Mode
To enter the docker container:
```sh
$ docker attach binddock
root@21eba089c6e5:~#
```

To exit the container (without killing the process), press:
`'Ctrl+p`, followed by `Ctrl+q`
