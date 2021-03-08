# Alpine Linux
Recipes used with Alpine Linux.

## Update package list
```
apk update
```

## Apache HTTP Server
### Installation
```
apk add apache2
```

### Control service
```
rc-service apache2 start
rc-service apache2 stop
```

## OpenVPN
### Installation
```
apk add openvpn
```

### Start a connection
```
openvpn --config <config file path>
```

## Resources
- [Alpine Linux](https://alpinelinux.org/)
- [Apache - Alpine Linux](https://wiki.alpinelinux.org/wiki/Apache)
- [Setting up a OpenVPN server - Alpine Linux](https://wiki.alpinelinux.org/wiki/Setting_up_a_OpenVPN_server)
