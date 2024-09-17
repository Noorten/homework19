стартуем vagrant up

проверяем

root@inetRouter:~# ip r
default via 10.0.2.2 dev eth0 proto dhcp src 10.0.2.15 metric 100
10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15 metric 100
10.0.2.2 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100
10.0.2.3 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100
192.168.0.0/24 via 192.168.255.2 dev eth1 proto static
192.168.1.0/24 via 192.168.255.2 dev eth1 proto static
192.168.2.0/24 via 192.168.255.2 dev eth1 proto static
192.168.255.0/30 dev eth1 proto kernel scope link src 192.168.255.1
192.168.255.0/24 via 192.168.255.2 dev eth1 proto static

root@centralRouter:~# ip r
default via 192.168.255.1 dev eth1 proto static
10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15 metric 100
10.0.2.3 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100
192.168.0.0/28 dev eth2 proto kernel scope link src 192.168.0.1
192.168.0.32/28 dev eth3 proto kernel scope link src 192.168.0.33
192.168.0.64/26 dev eth4 proto kernel scope link src 192.168.0.65
192.168.1.0/24 via 192.168.255.6 dev eth6 proto static
192.168.2.0/24 via 192.168.255.10 dev eth5 proto static
192.168.255.0/30 dev eth1 proto kernel scope link src 192.168.255.2
192.168.255.4/30 dev eth6 proto kernel scope link src 192.168.255.5
192.168.255.8/30 dev eth5 proto kernel scope link src 192.168.255.9

root@office1Router:~# ip r
default via 192.168.255.9 dev eth1 proto static
10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15 metric 100
10.0.2.3 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100
192.168.2.0/26 dev eth2 proto kernel scope link src 192.168.2.1
192.168.2.64/26 dev eth3 proto kernel scope link src 192.168.2.65
192.168.2.128/26 dev eth4 proto kernel scope link src 192.168.2.129
192.168.2.192/26 dev eth5 proto kernel scope link src 192.168.2.193
192.168.255.8/30 dev eth1 proto kernel scope link src 192.168.255.10

root@office2Router:~# ip r
default via 192.168.255.5 dev eth1 proto static
10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15 metric 100
10.0.2.3 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100
192.168.1.0/25 dev eth2 proto kernel scope link src 192.168.1.1
192.168.1.128/26 dev eth3 proto kernel scope link src 192.168.1.129
192.168.1.192/26 dev eth4 proto kernel scope link src 192.168.1.193
192.168.255.4/30 dev eth1 proto kernel scope link src 192.168.255.6

root@centralServer:~# ip r
default via 192.168.0.1 dev eth1 proto static
10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15 metric 100
10.0.2.3 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100
192.168.0.0/28 dev eth1 proto kernel scope link src 192.168.0.2

root@office1Server:~# ip r
default via 192.168.2.129 dev eth1 proto static
10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15 metric 100
10.0.2.3 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100
192.168.2.128/26 dev eth1 proto kernel scope link src 192.168.2.130vice: Consumed 1.657s CPU time.

root@office2Server:~# ip r
default via 192.168.1.1 dev eth1 proto static
10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15 metric 100
10.0.2.3 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100
192.168.1.0/25 dev eth1 proto kernel scope link src 192.168.1.2

root@office1Server:~# ping 192.168.1.2 -c 4
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=61 time=1.27 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=61 time=1.15 ms
64 bytes from 192.168.1.2: icmp_seq=3 ttl=61 time=1.14 ms
64 bytes from 192.168.1.2: icmp_seq=4 ttl=61 time=1.29 ms

--- 192.168.1.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3005ms
rtt min/avg/max/mdev = 1.143/1.212/1.290/0.066 ms

root@office1Server:~# ping 192.168.0.2 -c 4
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
64 bytes from 192.168.0.2: icmp_seq=1 ttl=62 time=0.967 ms
64 bytes from 192.168.0.2: icmp_seq=2 ttl=62 time=0.784 ms
64 bytes from 192.168.0.2: icmp_seq=3 ttl=62 time=0.960 ms
64 bytes from 192.168.0.2: icmp_seq=1 ttl=62 time=0.852 ms

--- 192.168.0.2 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 0.784/0.875/0.967/0.091 ms

root@office1Server:~# ping 8.8.8.8 -c 2
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=105 time=26.0 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=105 time=25.4 ms

--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 25.367/25.680/25.994/0.313 ms

root@office1Server:~# traceroute 8.8.8.8
traceroute to 8.8.8.8 (8.8.8.8), 30 hops max, 60 byte packets
 1  _gateway (192.168.2.129)  0.497 ms  0.524 ms  0.560 ms
 2  192.168.255.9 (192.168.255.9)  0.829 ms  0.817 ms  0.732 ms
 3  192.168.255.1 (192.168.255.1)  1.224 ms  1.264 ms  1.320 ms
 4  10.0.2.2 (10.0.2.2)  1.693 ms  1.683 ms  1.641 ms
 5  * * *
 6  * * *


# homework19
