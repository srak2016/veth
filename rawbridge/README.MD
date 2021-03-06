Redirects received raw ethernet frames from "enp0s3" interface to a UDP socket of "enp0s8" and vice versa.

VirtualBox Adapter Setup
----------------
Setup 'Adapter 1' as 'Bridge Adapter'. Set Promiscuous mode as Allow All.
<br>![adapter1](adapter1.png)<br>
Setup 'Adapter 2' as 'Host only Adapter'. 
<br>![adapter2](adapter2.png)<br>
Make sure Host only interface matches with following setting.
<br>![host_interface1](host_interface1.png)
<br>![host_interface2](host_interface2.png)

Setup
-----
install Python

    sudo apt-get install python3

install scapy

    sudo apt-get install scapy

verify both interfaces is up. (enp0s3 is 'Bridge Adapter' and enp0s8 is 'Host only Adapter')
    ifconfig
<pre>enp0s3: flags=4163&lt;UP,BROADCAST,RUNNING,MULTICAST&gt;  mtu 1500
        inet 192.168.0.10  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::4189:181f:8063:4095  prefixlen 64  scopeid 0x20&lt;link&gt;
        ether 08:00:27:ef:43:6f  txqueuelen 1000  (Ethernet)
        RX packets 42567  bytes 29890307 (29.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 816  bytes 81921 (81.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

enp0s8: flags=4163&lt;UP,BROADCAST,RUNNING,MULTICAST&gt;  mtu 1500
        inet 169.254.0.2  netmask 255.255.0.0  broadcast 169.254.255.255
        inet6 fe80::f346:71c7:d25:7ff4  prefixlen 64  scopeid 0x20&lt;link&gt;
        ether 08:00:27:14:48:c2  txqueuelen 1000  (Ethernet)
        RX packets 45  bytes 9312 (9.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 745  bytes 93683 (93.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0</pre>

Usage

    sudo python rawbridge_m.py --iface "enp0s3" --iface_ipaddr "169.254.0.2"
