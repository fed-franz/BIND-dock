# BIND-dock
Generic BIND server docker container.

This container is meant for testing purposes and it is supposed to be configured as needed.

Default config answers requests for www.domain.com with the IP 1.2.3.4

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
## MAN
* Enter the container shell:
```sh
$ docker attach binddock
root@a1eba089c6e5:~#
```

* Exit the container (without killing the process):<br/>
Press `'Ctrl+p`, followed by `Ctrl+q`

* Terminate the container:
```sh
$ docker kill binddock
```
* Restart the container:
```sh
$ docker start binddock
```

* Remove the container:
```sh
$ docker kill binddock
```
