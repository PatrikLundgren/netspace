netspace - a dead simple start script for your lab network services

Let's say you want to run a few services for your embedded devices on a separate
network interface. You may want to do this as your IT department may be upset
with you if you start a dhcp/dns tftp and webservers on your internal network.

netspace is a few dead (not to say stupid) simple start scripts for starting a
few services on a network interface without worrying about how those services
may interact with your other interfaces.

It provides a simple interface for creating a namespace with a single interface,
sets it up for you, and runs your start scripts. You can ofcourse do further
setup (or all of it) in the start scripts if you like.

## Getting started
```
sudo make install
netspace.sh create eth1 192.168.1.99 foo
netspacectl start foo
```

## Creating a service
By default, all scripts in `/etc/netspace/init.d` are executed with
`$START` set to a suitable execute command which will execute the line
inside the netspace.

Example start script:
```
# init.d/dnsmasq.sh
#!/bin/bash
$START /usr/sbin/dnsmasq -x /run/dnsmasq/dnsmasq.pid -u dnsmasq -7 /etc/dnsmasq.d,.dpkg-dist,.dpkg-old,.dpkg-new --local-service
```



