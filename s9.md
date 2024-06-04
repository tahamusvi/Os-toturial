# Session 9


## ifconfig

The `ifconfig` (interface configuration) command is used to configure and manage network interfaces in a Linux system.

The basic syntax for the `ifconfig` command is:

```
ifconfig [interface] [options]
```

Here are some common uses of the `ifconfig` command:

1. Display information about network interfaces:
   ```
   ifconfig
   ```
   This will show the configuration of all active network interfaces, including IP address, MAC address, and other details.

2. Configure an interface:
   ```
   ifconfig [interface] [up|down]
   ```
   This can be used to enable or disable a network interface.

3. Assign an IP address to an interface:
   ```
   ifconfig [interface] [IP address]
   ```
   This can be used to set the IP address of a network interface.

4. Set the netmask for an interface:
   ```
   ifconfig [interface] netmask [netmask]
   ```
   This can be used to set the netmask for a network interface.

5. Set the broadcast address for an interface:
   ```
   ifconfig [interface] broadcast [broadcast address]
   ```
   This can be used to set the broadcast address for a network interface.

The `ifconfig` command is useful for troubleshooting network issues, configuring network interfaces, and verifying the network settings of a Linux system.


## ifconfig -a

The `ifconfig -a` command displays information about all network interfaces, including those that are down or inactive.

The output of `ifconfig -a` typically includes the following information for each interface:

- Interface name (e.g., `eth0`, `lo`)
- IP address
- MAC address
- Netmask
- Broadcast address
- Flags (e.g., UP, BROADCAST, RUNNING, MULTICAST)
- MTU (Maximum Transmission Unit)
- Receive and transmit statistics

## Configuring IP Address Using ifconfig

To set a static IP address on a network interface using `ifconfig`, you can use the following command:

```
ifconfig [interface] [IP address]
```

For example, to set the IP address of the `eth0` interface to `192.168.1.20`, you would run:

```
ifconfig eth0 192.168.1.20
```

You can also set the netmask using the `netmask` option:

```
ifconfig eth0 192.168.1.20 netmask 255.255.255.0
```

To disable an interface, use:

```
ifconfig eth0 down
```

To enable an interface, use:

```
ifconfig eth0 up
```

## Using ifup and ifdown

The `ifup` and `ifdown` commands are used to enable and disable network interfaces, respectively.

```
ifup eth0
ifdown eth0
```

These commands read the network interface configuration from the `/etc/network/interfaces` file and apply the changes.

## Configuring Network Interfaces in /etc/network/interfaces

To configure a static IP address that persists across system reboots, you can edit the `/etc/network/interfaces` file. Here's an example configuration:

```
# The primary network interface
auto eth0
iface eth0 inet static
    address 10.0.0.41
    netmask 255.255.255.0
    gateway 10.0.0.1
```

To configure a dynamic (DHCP) IP address, use the following:

```
auto eth0
iface eth0 inet dhcp
```

After editing the configuration file, you can restart the network service to apply the changes:

```
ifdown eth0
ifup eth0
```

This will restart the `eth0` interface and apply the new settings.

#

## route

The `route` command is used to view and manipulate the IP routing table, which is used to determine where to forward packets based on the destination IP address.

Here are some common uses of the `route` command:

1. Display the current routing table:
   ```
   route
   ```
   This will show the current routing table, including the destination network, gateway, network interface, and other information.

2. Add a new route:
   ```
   route add -net 10.0.2.0/24 gw 172.20.20.10
   ```
   This adds a route to the network `10.0.2.0/24` with a gateway of `172.20.20.10`.

3. Delete a route:
   ```
   route del -net 10.0.2.0/24
   ```
   This removes the route to the network `10.0.2.0/24` from the routing table.

4. Set the default gateway:
   ```
   route add default gw 192.168.1.1
   ```
   This sets the default gateway to `192.168.1.1`.

The routing table is used to determine the path that packets should take to reach their destination. When a packet is sent, the operating system looks up the destination IP address in the routing table to find the appropriate interface and gateway to use.

The `route` command is useful for troubleshooting network connectivity issues, configuring static routes, and managing the routing table on a Linux system.

#

## ip

The `ip` command is a powerful tool for configuring and managing network interfaces and routing in Linux. It is part of the `iproute2` package and is often considered a more advanced and flexible replacement for the `ifconfig` and `route` commands.

Here are some common usages of the `ip` command:

1. View network interface information:
   ```
   ip addr show
   ```
   This command displays the IP addresses and other information for all network interfaces.

2. Assign an IP address to an interface:
   ```
   ip addr add 172.30.20.20 dev eth0
   ```
   This adds the IP address `172.30.20.20` to the `eth0` interface.

3. Remove an IP address from an interface:
   ```
   ip addr del 172.30.20.20 dev eth0
   ```
   This removes the IP address `172.30.20.20` from the `eth0` interface.

4. View the routing table:
   ```
   ip route show
   ```
   This displays the current routing table.

5. Add a new route:
   ```
   ip route add 172.20.0.0/16 via 192.168.10.10
   ```
   This adds a new route to the network `172.20.0.0/16` with a gateway of `192.168.10.10`.

6. Set the default gateway:
   ```
   ip route add default via 10.2.2.0
   ```
   This sets the default gateway to `10.2.2.0`.

The `ip` command provides a more comprehensive and flexible way to manage network interfaces and routing compared to the legacy `ifconfig` and `route` commands. It offers a wider range of functionality, including support for advanced features like traffic shaping, IPsec, and VLANs.

Overall, the `ip` command is a powerful tool for network administrators and advanced Linux users who need more control over their network configuration.

#

## netstat

The `netstat` command provides a report on network connections, routing tables, and network interface cards. In other words, this command shows the status of the ports that are being used by the host.

Some useful options for the `netstat` command include:

- `-a`: Displays all connections and listening ports.
- `-n`: Displays numeric addresses instead of resolving hostnames.
- `-p`: Displays the PID and name of the program to which each socket belongs.
- `-t`: Displays TCP connections.
- `-u`: Displays UDP connections.
- `-r`: Displays the kernel's routing table.
- `-i`: Displays a table of all network interfaces.

Examples:

- To see all active TCP connections:
```
netstat -antp
```
- To see all active UDP connections:
```
netstat -anup
```
- To display the kernel's routing table:
```
netstat -nr
```
- To see a list of all network interfaces:
```
netstat -i
```

The `netstat` command is a valuable tool for troubleshooting network issues and understanding the network activity on a system.

# 

## telnet

The `telnet` command is used to establish a remote connection between two hosts. The connection in the `telnet` command lacks security features. Telnet uses the TCP protocol to connect to a remote host. With this command, you can check if a port is open or closed, and also test the service running on that port. For example, by connecting to port 80, you can use HTTP protocol commands to test the web service.

After executing the `telnet` command, the `<telnet` prompt appears, and by typing the `open` command and then entering the name or address of the remote system, you can connect to the desired system.

You can also use the following command:

```
telnet remote_system_name_or_address
```

If the `-l` option is used and a specific username is provided after it, you will log in to the remote system with that user account. After the `telnet` connection is established, the operating system prompt will appear, and you can enter commands.

By issuing the `help` or `?` command, you can see the list of available `telnet` commands. To exit the `telnet` environment, use the `quit` command.

It is important to note that the `telnet` command is not a secure way of connecting to remote systems, as it does not encrypt the communication. For secure remote connections, it is recommended to use the `ssh` command instead.

#

## nmap

The `nmap` command is a powerful network scanning tool. Network administrators can use this command to examine the status of online services and open ports on systems.

The `nmap` command sends packets to the 1000 most common and widely used ports of each system and provides a report on whether those ports are open or closed.

The general syntax for the `nmap` command is:

```
nmap <address>
```

Some common options for the `nmap` command include:

- `-sV`: Probes open ports to determine service/version info
- `-sS`: TCP SYN scan (stealthy scan)
- `-sU`: UDP scan
- `-sn`: Ping scan (disable port scan)
- `-p-`: Scan all ports instead of just the most common 1000
- `-p <port ranges>`: Only scan specified ports
- `-oN <outputfile>`: Save the output to a file
- `-iL <inputfile>`: Read target locations from a file
- `-sC`: Use default nmap scripts for further enumeration
- `-sV`: Probe open ports to determine service/version info

The `nmap` command provides a wealth of information about the network and the systems connected to it. It is a valuable tool for network administrators and security professionals to understand the attack surface and identify potential vulnerabilities.

#

## ping

The `ping` command is one of the common methods used to test the connectivity between two network nodes. These nodes can be located in a local network or a WAN (Wide Area Network).

The `ping` command uses the ICMP (Internet Control Message Protocol) to communicate with other hosts. To run the `ping` command, you can enter the domain name or IP address of the target host:

```
ping <address>
```

When you run the `ping` command, a request is sent to the target computer, and if the target computer receives the request, it responds. This process continues repeatedly. To stop the `ping` command, you can use `Ctrl+C`.

Some common uses of the `ping` command include:

- Checking if a remote host is accessible
- Measuring the round-trip time (latency) between the local and remote host
- Troubleshooting network connectivity issues
- Determining if a network interface or router is functioning properly

The `ping` command is a valuable tool for network administrators and users to quickly test the connectivity and responsiveness of remote systems. It provides useful information about the network path and the latency between the local and remote hosts.

#


## traceroute

The `traceroute` command is one of the widely used troubleshooting tools in networking. With this method, you can determine the number of intermediate nodes (hops) between two hosts and also track the path taken by the packets between the two hosts.

The general syntax for the `traceroute` command is:

```
traceroute <destination address>
```

When you run the `traceroute` command, it sends packets to the destination host and records the IP addresses of the intermediate routers and the time it takes for the packets to reach each hop. This information is then displayed in the output.

Some common uses of the `traceroute` command include:

- Identifying network connectivity issues
- Determining the number of hops between the local and remote hosts
- Tracing the path taken by the packets to reach the destination
- Identifying the network devices (routers, firewalls, etc.) along the path
- Measuring the latency at each hop

The `traceroute` command is particularly useful when troubleshooting network problems, as it can help identify the specific point in the network where an issue is occurring. This information can then be used to take appropriate actions to resolve the problem.

It's worth noting that the `traceroute` command may be blocked or altered by certain network devices, such as firewalls, which can impact the accuracy of the information provided.

# ## arp

The `arp` command provides information about the IP addresses and physical addresses (MAC addresses) of network interface cards in network communications.

Using this command, you can view the mapping between IP addresses and the corresponding hardware (MAC) addresses of the network cards, as well as the IP addresses stored on the computer (the ARP table).

In the output of the `arp` command, the "Address" column displays the IP address or the computer name, and the "HW Address" column shows the physical or MAC address of the network card.

Some common usage examples of the `arp` command include:

1. Viewing the ARP table:
```
arp -a
```
This will display the current ARP table, showing the IP-to-MAC address mappings.

2. Resolving a specific IP address:
```
arp -n <IP_address>
```
This will look up the MAC address associated with the specified IP address.

3. Clearing the ARP cache:
```
arp -d <IP_address>
```
This will remove the specified IP address from the ARP table.

4. Adding a static ARP entry:
```
arp -s <IP_address> <MAC_address>
```
This will manually add a static ARP entry for the specified IP and MAC address.

The `arp` command is useful for network troubleshooting, analyzing network traffic, and understanding the mapping between IP addresses and MAC addresses on a local network.

#


## DNS Lookup: Converting Domain Names to IP Addresses

To obtain the IP address based on the domain name, or vice versa, you can use the `nslookup` or `dig` commands.

1. **nslookup**:
```
nslookup www.google.com
```
This will display the IP address(es) associated with the domain name `www.google.com`.

2. **dig**:
```
dig www.google.com
```
The `dig` command (Domain Information Groper) also performs a DNS lookup and provides more detailed information, including the DNS server used, the query type, and the response.

The output of these commands typically includes the following information:

- The requested domain name
- The IP address(es) associated with the domain name
- The DNS server(s) used for the lookup
- Additional details about the DNS response

For example, the output of the `dig` command for `www.google.com` might look like this:

```
$ dig www.google.com
;; QUESTION SECTION:
;www.google.com.			IN	A

;; ANSWER SECTION:
www.google.com.		181	IN	A	142.250.66.78
www.google.com.		181	IN	A	142.250.66.113
www.google.com.		181	IN	A	142.250.66.100
www.google.com.		181	IN	A	142.250.66.102

;; QUERY TIME: 17 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Jun 04 18:58:18 UTC 2024
;; MSG SIZE  rcvd: 124
```

These commands are useful for quickly looking up the IP address associated with a domain name, or for troubleshooting DNS-related issues.

#

## wget

The `wget` command is used to download files from the internet. It works with the HTTP, HTTPS, and FTP protocols.

The general syntax for the `wget` command is:

```
wget <URL>
```

Here's an example:

```
wget http://www.example.com
```

This will download the default file (usually the homepage) from the `www.example.com` website and save it in the current directory.

Some common options for the `wget` command include:

- `-O <filename>`: Specify the output file name.
- `-c`: Continue a partially downloaded file.
- `-r`: Recursively download an entire website.
- `-p`: Download all the required files to display a webpage properly.
- `-nc`: No-clobber, which means it won't overwrite existing files.
- `-q`: Quiet mode, which suppresses output.
- `-b`: Run in the background.

Here are a few examples:

1. Download a file and save it with a specific name:
   ```
   wget -O myfile.html http://www.example.com
   ```

2. Continue a partially downloaded file:
   ```
   wget -c http://www.example.com/large_file.zip
   ```

3. Recursively download an entire website:
   ```
   wget -r http://www.example.com
   ```

The `wget` command is a powerful tool for downloading files from the internet, especially when you need to automate the process or download large files. It's often used in shell scripts and batch jobs to automate file downloads.