
# EPAM-DevOps22: Linux Networking
![](/Linux_networking/Screens/Task_Linux_Net.png)

[Task description in .pdf file](/Linux_networking/Task_Linux_Net.pdf)
## Description 
### Networks:
+ Net1 - 192.168.0.0/24
+ Net2 - 10.91.15.0/24
+ Net3 - 10.15.91.0/24
+ Net4 - 172.16.15.0/24
### Used VM machines and interfaces
- Server-1 - UbuntuServer-22.04

| Interfaces | IP addresses | MAC addresses |
| ------------- | ------------- | ----------|
| enp0s3 | 192.168.0.200/24 | 08:00:27:01:4c:ad |
| enp0s8 | 10.91.15.200/24 | 08:00:27:1b:35:1a |
| enp0s9 | 10.15.91.200/24 | 08:00:27:8b:31:0c |

- Client-3 - Ubuntu-22.04

| Interfaces | IP addresses | MAC addresses |
| ------------- | ------------- | ----------|
| enp0s3 | dynamic | 08:00:27:43:c7:d7 |
| enp0s8 | 172.16.15.15/24 | 08:00:27:ec:16:e8 |

- Client-2 - Centos-7

| Interfaces | IP addresses | MAC addresses |
| ------------- | ------------- | ----------|
| enp0s3 |dynamic | 08:00:27:4a:42:5d |
| enp0s8 | 172.16.15.16/24 | 08:00:27:b2:e8:d2 |

## Steps of Task
**1. –°ONFIGURATION OF NETWORK SETTINGS ON VIRTUAL MACHINES.**

1.1 Starting the first VM machine with DHCP Server. Entering network settings according to the task. Open the network plan configuration file and add settings:</br>

__/etc/netplan/*yaml__</br>

![](/Linux_networking/Screens/Server-netplan.png)

1.2  Apply the settings using the following command:
```
 sudo netplan apply
```
1.3 –°onfiguring the DHCP server on Server-1 to issue network addresses for new clients in next files:</br>

__/etc/dhcp/dhcpd.conf__</br>

![](/Linux_networking/Screens/Server-dhcpd.png)

__/etc/default/isc-dhcp-server__</br>

![](/Linux_networking/Screens/Server-isc.png)

1.4 Checking the operation of the DHCP service:

```
 sudo systemctl status isc-dhcp-server.service
```
![](/Linux_networking/Screens/Server-DHCP-service.png)

1.5 –°onfigure the operation of network ports for Client-3 and Client-2. One port works on the principle of getting a dynamic address, and the second port sets statics, according to the task:</br>

__Client-3__</br>
![](/Linux_networking/Screens/client3-ip-addresses.png)</br>

__Client-2__</br>
![](/Linux_networking/Screens/client2-ip-addresses.png)

1.6 –°heking the connection between computers using the `ping` and `traceroute` command:

__Server-1__</br>
![](/Linux_networking/Screens/Server-ping-traceroute.png)

__Client-3__</br>
![](/Linux_networking/Screens/client3-ping-traceroute.png)

__Client-2__</br>
![](/Linux_networking/Screens/client2-ping-traceroute.png)

**2. CONFIGURING NETWORK TRAFFIC ON A CLIENT VIRTUAL PORT.** </br>

2.1 Add two virtual IP addresses **172.17.D+10.1/24** and **172.17.D+20.1/24** to the lo interface on Client-3. After that, we configure the routing of Client-2 along the following route:

| Host |  Via |IP addresses recipient| MAC addresses | Gateway |
| ---------| ------------- | ----------| ----------| ----------| 
| Client-2 |  Server-1|172.17.25.0 | 255.255.255.0 | 10.91.15.11 |
| Client-2 | Net4 | 172.17.35.0 | 255.255.255.0 |  172.16.15.15 |

2.2 Adding two addresses to lo interface on Client-3.</br>

![](/Linux_networking/Screens/Add-2-virtual-ip-client-1.png)

2.3 Adding route from Client-2 to Server-1:</br>

![](/Linux_networking/Screens/Add-route-Client2.png)

2.4 Adding route from Server-1 to Client-3:</br>

![](/Linux_networking/Screens/Add-route-Server.png) 

2.5 Checking the connection between Client-2 and Client-3`s virtual port:</br>

![](/Linux_networking/Screens/Ping-route-Client-2.png)

2.6 Adding a route between Client-3 and Client-2 via the Net4 network and checking connections:</br>

![](/Linux_networking/Screens/Add-route-via-Net4.png)

**3. CONFIGURE THE USE OF A SUMMARY VIRTUAL NETWORK.**

3.1 Using networks 172.17.25.0/24 and 172.17.35.0/24 configure routing for summarized network via Server-1:
![](/Linux_networking/Screens/Summarized%20network.png)

3.2 Replacing old IP addresses in lo interface Client-3:

![](/Linux_networking/Screens/Set%20IP%20address%20Client3.png)

3.3 Adding a new route from Client-2 to Server-1:

![](/Linux_networking/Screens/Add-new-route-Client2.png)

3.4 Adding a new route from Server-1 to Client-3:</br>

![](/Linux_networking/Screens/Add-new-route-Server.png)

3.5 –°hecking ping and traceroute from Client-2 to 172.17.0.0/18 network:

![](/Linux_networking/Screens/Cheking-new-ping.png)

**4. SETTING UP AN SSH CONNECTION.**

4.1 Create a new ssh-key by command `ssh-keygen` on each VM and copying public keys using the next command:
```
ssh-copy-id username@remote_host
```

4.2 Checking connection via `ssh` from Client-3 to Server-1 and Client-2:</br>

![](/Linux_networking/Screens/Client-1-Server-1%20(ssh).png)

![](/Linux_networking/Screens/Client-1-Client-2%20(ssh).png)

4.3 Checking connection via `ssh` from Client-2 to Client-3:</br>

![](/Linux_networking/Screens/Client-2-Client-1(ssh).png)

**5. SETTING FIREWALL**

5.1 Configuration `iptables` on Server-1:

![](/Linux_networking/Screens/IP-tables-Server.png)

5.2 Checking ssh connection:

![](/Linux_networking/Screens/Client-1-Server-1-new-(ssh).png)

![](/Linux_networking/Screens/Client2-Server(den).png)

5.3 Checking ping connections:

![](/Linux_networking/Screens/Checking-Ping-Clien2.png)

*End task*
