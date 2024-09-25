## Lab 10

- Name: Alec Porter
- Email: porter.223@wright.edu

## Part 1 - Linux Network Command Cheat Sheet

- `hostname`  The name of the computer.  It's the same as what is on the command line after the  user (user@hostname)
- `ifconfig`  Variety of information on system NICs including IP address, MAC, and packet recieve/transmitted info.
- `ip addr show` Shows IP address information for the system NICs. 
- `route` displays the IP routing table.
- `cat /var/lib/dhcp/dhclient.leases` A list of DHCP client leases.
- `cat /etc/resolv.conf`  Configuration file for DNS queries, it translates domain names to IP addresses.
- `curl ipinfo.io` Allows for data transfer from ipinfo.io which lists IP address information to the command line.
- `iptables -L` List any rules set up for IPv4 and IPv6 packet filetering.
- `nmap -p <IP_or_hostname>` Tool for network explotation and security auditing, -p allows you to check if TCP/UDP ports are opened or closed.
- `tcpdump -i <networkinterface> -n host <IP_or_hostname>` Data packet anlayzer that can display packets being transmitted/recieved by the host device.

## Part 2 - Network Info

### Network Info for Windows 11 Laptop

1. Hostname of the device: alec-laptop
2. MAC address of the NIC connected to the network:  E0-D4-E8-C7-A5-38
3. IPv4 address: 10.16.163.59
4. Subnet mask: 255.255.0.0
5. Gateway address: 10.16.0.1
6. DHCP server address: 192.168.151.43
7. DNS server address: 130.108.128.200
8. Public IPv4 address: 130.108.104.21

### Network Info for AWS Instance

1. Hostname of the device: ip-10-0-0-25
2. MAC address of the NIC connected to the network: 12:21:6B:E7:41:25
3. IPv4 address: 10.0.0.25
4. Subnet mask: 255.255.255.0
5. Gateway address: 10.0.0.1
6. DHCP server address: 10.0.0.1
7. DNS server address: 127.0.0.53
8. Public IPv4 address: 34.255.112.222

## Part 3 - Subnet Translation

Translate the below CIDR notation subnets to their IP ranges:
1. `130.108.0.0/16` 130.108.0.0 - 130.108.255.255
2. `192.168.1.0/8` 192.0.0.0 - 192.255.255.255
3. `8.8.8.8/32` 8.8.8.8

Translate the below IP ranges to their CIDR notation subnets:
1. `192.168.1.0 - 192.168.1.255` 192.168.1.0/24
2. `172.16.0.0 - 172.16.255.255` 172.16.0.0/16 
3. `132.189.13.78 - 132.189.13.78` 132.189.13.78/32

## Part 4 - Security
I tried deleting the default rules but received a message stating the default rules could not be deleted.

Screenshot of your changed Inbound Security Group rules.  
![Inbound Rules for Lab 10](https://github.com/WSU-kduncan/ceg2350s24-alec-porter/blob/main/Lab10/lab10part4.png)
![Error Message](https://github.com/WSU-kduncan/ceg2350s24-alec-porter/blob/main/Lab10/error.png)

Why should HTTP allow any IP, while SSH has restrictions?
The HTTP protocol is for fetching resources such as html documents, it allows for easy access of data.  SSH allows for operating and managing network services securely over an unsecured network.  HTTP can allow any IP becuase it is for accessing data but SSH needs to restrict IPs because it allows for management of a resource.  Restricting IP addresses helps to secure the protocol by allow only certain IP address access to use it.

## Extra Credit - Tattle Tale

### IPv4 Source Report

| Rank  | IPv4 Address    | # of Attempts |
| ----- | ------------    | ------------- |
| 1     | 205.185.122.211 |     204
| 2     | 205.185.123.156 |     86
| 3     | 209.141.61.58   |     28
| 4     | 209.141.61.33   |     28
| 5     | 209.141.36.11   |     28
| 6     | 115.56.115.248  |     28

Commands to parse `csv` for report:
datafile='/home/alecporter/Documents/2024Spring/ceg2350s24-alec-porter/Lab10/auth_logs.csv'
sort $datafile | awk '{print $2}' | sort | uniq -c | sort -n

### Username Used Report

| Rank  | Username     | # of Attempts |
| ----- | ------------ | ------------- |
| 1     | admin        |     79
| 2     | user         |     74
| 3     | test         |     28
| 4     | oracle       |     18
| 5     | postgres     |     15

Commands to parse `csv` for report:
datafile='/home/alecporter/Documents/2024Spring/ceg2350s24-alec-porter/Lab10/auth_logs.csv'
sort $datafile | awk -F', ' '{print $1}' | uniq -c | sort -n

