# Alpine Linux
Recipes used with Alpine Linux.

## Base Alpine Installation
The following steps are for a virtual machine installation with one Network Interface Card (NIC) and one drive, and it is intended to use as a client to connect to other machines using SSH. It is not intended to use it as a server nor a desktop computer.

- Create a new virtual machine and insert the Alpine Linux iso image for installation and start it.
- Log into the virtual machine using `root` user, it won't ask for a password.
- Install the base system using `setup-alpine` command, it will ask you for the following parameters
- Keyboard Layout: `es` (I'm guatemalan)
- Variant (of the keyboard): `es-winkeys` (I'm used to Windows Systems, hahaha)
- Hostname: use the default value `localhost`
- Interfaces to initialize: use the default, maybe `eth0` (I'm just have one interface configured)
- IP Address for the interface: use the default `dhcp`
- Any manual network configuration: default `no`
- Set the password for root account
- Time zone: I use `America/Guatemala` (you can use the `?` to view the list of time zones available)
- HTTP/FTP Proxy: I don't have any so `none` (It will depend on your network configuration)
- NTP Client: I use the default `chrony`
- Mirror: I use the default again `1`
- SSH Server: I'm used to OpenSSH, so `openssh`
- Select the disk to use: It shows `sda` or `vda`
- How would you like to use the disk: In my case, I want all configuration in the only disk I have configured, so `sys`, you can use the `?` to see the alternatives
- Erase the above disk and continue: I choose yes `y`
- Reboot using `poweroff` command, detach the installation ISO Image and start the virtual machine.

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
