# lxc-portforward
Simple script to automatically set up port forwarding for LXC containers

USAGE:
------

Copy lxc-portforward, lxc-portforward.conf, and lxc-portforward-helper to /etc/lxc.

In your container config set:

    lxc.network.script.up = /etc/lxc/lxc-portforward
    lxc.network.script.down = /etc/lxc/lxc-portforward

Edit lxc-portforward.conf to forward the ports you want forwarded

FILES:
------

Port forwarding information is stored in /etc/lxc/lxc-portforward.conf.  Format is:

    container_name:local_port:remote_port[:protocol]

protocol defaults to tcp

IP addresses are stored in /var/run/lxc-portforward/<container name> so when
the container is stopped the proper iptables rules can be removed.
