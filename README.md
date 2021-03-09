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
modprobe tun
echo "tun" >> /etc/modules-load.d/tun.conf
```

### Start a connection
```
openvpn --config <config file path>
```

## VirtualBox shared folders
### Installation
#### Enable the Community repository
Edit the `/etc/apk/repositories` file and delete the # character at the beginning of the comunity repository.

#### Add the VirtualBox Guest Addittions package
```
apk add virtualbox-guest-additions
modprobe -a vboxsf
```

### Mount a shared folder
Create a directory to mount the shared folder and mount it.
```
mkdir /mnt/outside
mount -t vboxsf vbox_shared_name /mnt/outside
```

## Resources
- [Alpine Linux](https://alpinelinux.org/)
- [Apache - Alpine Linux](https://wiki.alpinelinux.org/wiki/Apache)
- [Setting up a OpenVPN server - Alpine Linux](https://wiki.alpinelinux.org/wiki/Setting_up_a_OpenVPN_server)
- [VirtualBox shared folders](https://wiki.alpinelinux.org/wiki/VirtualBox_shared_folders)
