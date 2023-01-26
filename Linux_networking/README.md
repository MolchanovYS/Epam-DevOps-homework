
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
- Server_1 - UbuntuServer-22.04

| Interfaces | IP addresses | MAC addresses |
| ------------- | ------------- | ----------|
| enp0s3 | 192.168.0.200/24 | 08:00:27:01:4c:ad |
| enp0s8 | 10.91.15.200/24 | 08:00:27:1b:35:1a |
| enp0s9 | 10.15.91.200/24 | 08:00:27:8b:31:0c |

- Client_1 - Ubuntu-22.04

| Interfaces | IP addresses | MAC addresses |
| ------------- | ------------- | ----------|
| enp0s3 | dynamic | 08:00:27:43:c7:d7 |
| enp0s8 | 172.16.15.15/24 | 08:00:27:ec:16:e8 |

- Client_2 - Centos-7

| Interfaces | IP addresses | MAC addresses |
| ------------- | ------------- | ----------|
| enp0s3 |dynamic | 08:00:27:4a:42:5d |
| enp0s8 | 172.16.15.16/24 | 08:00:27:b2:e8:d2 |

## Steps of Task
**1. Сonfiguration of network settings on virtual machines.**

1.1 Starting the first VM machine with DHCP Server. Entering network settings according to the task. Open the network plan configuration file and add settings:</br>

__/etc/netplan/*yaml__</br>

![](/Linux_networking/Screens/Server-netplan.png)

1.2  Apply the settings using the following command:
```
 sudo netplan apply
```
1.3 Сonfiguring the DHCP server on Server-1 to issue network addresses for new clients in next files:</br>

__/etc/dhcp/dhcpd.conf__</br>

![](/Linux_networking/Screens/Server-dhcpd.png)

__/etc/default/isc-dhcp-server__</br>

![](/Linux_networking/Screens/Server-isc.png)

1.4 Checking the operation of the DHCP service:

```
 sudo systemctl status isc-dhcp-server.service
 ```
![](/Linux_networking/Screens/Server-DHCP-service.png)

1.5 Сonfigure the operation of network ports for Client-1 and Client-2. One port works on the principle of getting a dynamic address, and the second port sets statics, according to the task:</br>

__Client_1__</br>
> In the screenshot, Client_1 is recorded as Client_3. It`s ok.
![](/Linux_networking/Screens/client3-ip-addresses.png)</br>

__Client_2__</br>
![](/Linux_networking/Screens/client2-ip-addresses.png)

1.6 Сheking the connection between computers using the `ping` and `traceroute` command.

__Server-1__</br>
![](/Linux_networking/Screens/Server-ping-traceroute.png)

__Client-1__</br>
![](/Linux_networking/Screens/client3-ping-traceroute.png)

__Client-2__</br>
![](/Linux_networking/Screens/client2-ping-traceroute.png)

2.Setting static IP`s on the Server.
