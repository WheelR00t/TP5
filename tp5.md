# TP 5

# I. Setup


# IP


Routeur :

````powershell
[wheelroot@localhost ~]$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:1b:10:19 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic noprefixroute enp0s3
       valid_lft 83928sec preferred_lft 83928sec
    inet6 fe80::a00:27ff:fe1b:1019/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:86:fb:0b brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.254/24 brd 10.5.1.255 scope global noprefixroute enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe86:fb0b/64 scope link
       valid_lft forever preferred_lft forever
````

Client1 :
````powershell
[wheelroot@localhost ~]$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:29:c0:26 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.11/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe29:c026/64 scope link
       valid_lft forever preferred_lft forever
````

Client2:

````powershell
[wheelroot@localhost ~]$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:fc:59:70 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.12/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fefc:5970/64 scope link
       valid_lft forever preferred_lft forever
````

# Hostname

Routeur:
````powershell
[wheelroot@localhost ~]$ sudo hostnamectl set-hostname routeur
````

Client1:
````powershell
[wheelroot@localhost ~]$ sudo hostnamectl set-hostname client1
````

Client2:
````powershell
[wheelroot@localhost ~]$ sudo hostnamectl set-hostname client2
````

# Ping

Routeur vers client1 et client2:
````powershell
[wheelroot@routeur ~]$ ping 10.5.1.11
PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data.
64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=1.27 ms
64 bytes from 10.5.1.11: icmp_seq=2 ttl=64 time=0.381 ms
64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=1.25 ms
64 bytes from 10.5.1.11: icmp_seq=4 ttl=64 time=0.561 ms
64 bytes from 10.5.1.11: icmp_seq=5 ttl=64 time=0.338 ms
64 bytes from 10.5.1.11: icmp_seq=6 ttl=64 time=0.515 ms
64 bytes from 10.5.1.11: icmp_seq=7 ttl=64 time=0.575 ms
^C
--- 10.5.1.11 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6158ms
rtt min/avg/max/mdev = 0.338/0.698/1.269/0.364 ms
[wheelroot@routeur ~]$ ping 10.5.1.12
PING 10.5.1.12 (10.5.1.12) 56(84) bytes of data.
64 bytes from 10.5.1.12: icmp_seq=1 ttl=64 time=1.38 ms
64 bytes from 10.5.1.12: icmp_seq=2 ttl=64 time=0.395 ms
64 bytes from 10.5.1.12: icmp_seq=3 ttl=64 time=0.772 ms
64 bytes from 10.5.1.12: icmp_seq=4 ttl=64 time=0.351 ms
^C
--- 10.5.1.12 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3037ms
rtt min/avg/max/mdev = 0.351/0.723/1.377/0.411 ms
````

client1 vers client2 et routeur:
````powershell
[wheelroot@client1 ~]$ ping 10.5.1.254
PING 10.5.1.254 (10.5.1.254) 56(84) bytes of data.
64 bytes from 10.5.1.254: icmp_seq=1 ttl=64 time=0.704 ms
64 bytes from 10.5.1.254: icmp_seq=2 ttl=64 time=0.466 ms
64 bytes from 10.5.1.254: icmp_seq=3 ttl=64 time=0.524 ms
64 bytes from 10.5.1.254: icmp_seq=4 ttl=64 time=0.490 ms
^C
--- 10.5.1.254 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3066ms
rtt min/avg/max/mdev = 0.466/0.546/0.704/0.093 ms
[wheelroot@client1 ~]$ ping 10.5.1.12
PING 10.5.1.12 (10.5.1.12) 56(84) bytes of data.
64 bytes from 10.5.1.12: icmp_seq=1 ttl=64 time=1.23 ms
64 bytes from 10.5.1.12: icmp_seq=2 ttl=64 time=0.471 ms
64 bytes from 10.5.1.12: icmp_seq=3 ttl=64 time=0.357 ms
64 bytes from 10.5.1.12: icmp_seq=4 ttl=64 time=0.508 ms
^C
--- 10.5.1.12 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3087ms
rtt min/avg/max/mdev = 0.357/0.640/1.227/0.343 ms
````

# II. Accès internet pour tous

1. Accès internet routeur
☀️ Déjà, prouvez que le routeur a un accès internet

````powershell
[wheelroot@routeur ~]$ ping www.ynov.com
PING www.ynov.com (172.67.74.226) 56(84) bytes of data.
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=1 ttl=46 time=46.6 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=2 ttl=46 time=124 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=3 ttl=46 time=53.2 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=4 ttl=46 time=67.3 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=5 ttl=46 time=57.1 ms
^C
--- www.ynov.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4014ms
rtt min/avg/max/mdev = 46.647/69.610/123.829/27.924 ms
````


☀️ Activez le routage

````powershell
[wheelroot@routeur ~]$ sudo firewall-cmd --add-masquerade --permanent
[sudo] password for wheelroot:
success
[wheelroot@routeur ~]$ sudo firewall-cmd --reload
success
````

2. Accès internet clients

☀️ Prouvez que les clients ont un accès internet

````powershell
[wheelroot@client1 ~]$ ping ynov.com
PING ynov.com (104.26.10.233) 56(84) bytes of data.
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=1 ttl=45 time=101 ms
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=3 ttl=45 time=102 ms
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=4 ttl=45 time=111 ms
64 bytes from 104.26.10.233 (104.26.10.233): icmp_seq=5 ttl=45 time=96.3 ms
^C
--- ynov.com ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4021ms
rtt min/avg/max/mdev = 96.343/102.380/110.597/5.161 ms
````

Client2

````powershell
[wheelroot@client2 network-scripts]$ ping ynov.com
PING ynov.com (104.26.11.233) 56(84) bytes of data.
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=1 ttl=45 time=39.3 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=2 ttl=45 time=54.8 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=3 ttl=45 time=78.5 ms
64 bytes from 104.26.11.233 (104.26.11.233): icmp_seq=4 ttl=45 time=36.0 ms
^C
--- ynov.com ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4008ms
rtt min/avg/max/mdev = 36.007/52.166/78.546/16.797 ms
````

☀️ Montrez-moi le contenu final du fichier de configuration de l'interface réseau

````powershell
[wheelroot@client2 etc]$ cd /etc/sys
sysconfig/          sysctl.conf         sysctl.d/           systemd/            system-release      system-release-cpe
[wheelroot@client2 etc]$ cd /etc/sysconfig/network-scripts/
[wheelroot@client2 network-scripts]$ ls
ifcfg-enp0s3  readme-ifcfg-rh.txt
[wheelroot@client2 network-scripts]$ cat ifcfg-enp0s3
DEVICE=enp0s3
NAME=client2

ONBOOT=yes
BOOTPROTO=static

IPADDR=10.5.1.12
NETMASK=255.255.255.0
GATEWAY=10.5.1.254
DNS1=1.1.1.1
````

# III. Serveur SSH

☀️ Sur routeur.tp5.b1, déterminer sur quel port écoute le serveur SSH
````powershell
[wheelroot@routeur ~]$ sudo ss -lnpt | grep 22
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=701,fd=3))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=701,fd=4))
````


☀️ Sur routeur.tp5.b1, vérifier que ce port est bien ouvert

````powershell
[wheelroot@routeur ~]$ sudo firewall-cmd --permanent --add-port=22/tcp
success
[wheelroot@routeur ~]$ sudo firewall-cmd --reload
success
[wheelroot@routeur ~]$ sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 22/tcp
  protocols:
  forward: yes
  masquerade: yes
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
````

# IV. Serveur DHCP

A. Installation et configuration du serveur DHCP

☀️ Installez et configurez un serveur DHCP sur la machine routeur.tp5.b1

````powershell
[wheelroot@routeur ~]$ sudo dnf -y install dhcp-server


[wheelroot@routeur ~]$ sudo systemctl enable --now dhcpd
[wheelroot@routeur ~]$ sudo firewall-cmd --add-service=dhcp
success
[wheelroot@routeur ~]$ sudo firewall-cmd --runtime-to-permanent
success
[wheelroot@routeur ~]$ sudo cat /var/lib/dhcpd/dhcpd.leases
# The format of this file is documented in the dhcpd.leases(5) manual page.
# This lease file was written by isc-dhcp-4.4.2b1

# authoring-byte-order entry is generated, DO NOT DELETE
authoring-byte-order little-endian;

server-duid "\000\001\000\001.\241EY\010\000'\206\373\013";
````

````powershell
[wheelroot@routeur ~]$ sudo cat /etc/dhcp/dhcpd.conf
default-lease-time 2592000;

max-lease-time 3888000;

authoritative;

subnet 10.5.1.0 netmask 255.255.255.0 {

    range 10.5.1.137 10.5.1.137;

    option routers 10.5.1.254;

    option subnet-mask 255.255.255.0;

    option domain-name-servers 1.1.1.1;

}
````
### B. Test avec un nouveau client

````powershell
[wheelroot@client3 ~]$ ping ynov.com
PING ynov.com (172.67.74.226) 56(84) bytes of data.
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=1 ttl=54 time=20.3 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=2 ttl=54 time=21.1 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=3 ttl=54 time=23.2 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=4 ttl=54 time=20.4 ms
64 bytes from 172.67.74.226 (172.67.74.226): icmp_seq=5 ttl=54 time=20.6 ms
^C
--- ynov.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4007ms
rtt min/avg/max/mdev = 20.322/21.145/23.205/1.063 ms
````

### IP
````powershell
[wheelroot@client3 ~]$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:fe:ae:68 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.150/24 brd 10.5.1.255 scope global dynamic noprefixroute enp0s3
       valid_lft 594sec preferred_lft 594sec
    inet6 fe80::a00:27ff:fefe:ae68/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
````
