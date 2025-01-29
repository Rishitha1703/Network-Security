<h1>Wire Shark</h1>
## capture filter:

captures only the mentioned filter 

## display filter

from all the captured packets displays only mentioned

## filters:

***)ip.addr ==192.168.1.11**

>>the filter `ip.addr == 192.168.1.11` is used to filter packets that have an IP address of 192.168.1.11 either as the source or the destination.

***)ip.src ==192.168.1.11**

>> used to filter packets that have an IP address of 192.168.1.11  as the source

***)ip.dst ==192.168.1.11**

>>used to filter packets that have an IP address of 192.168.1.11  as the destination

***)tcp,udp,dns…**

>>these filters are used to see the mentioned protocol packets only

***)tcp or udp**

—>two or more commands can be used using **or**

***)http.response.code==200**

>>`http.response.code==200` in Wireshark filters traffic to display only HTTP responses with a status code of 200, indicating a successful request.

***)udp.port==53**

>>displays udp traffic on port number 53(dns)

***)tcp.analysis.flags**

>>displays packets responsible for slow network

>>`tcp.analysis.flags` in Wireshark represents analysis flags used to highlight potential issues or noteworthy events in TCP communication, such as retransmissions, duplicate ACKs, or packet loss.

***)ip.src==192.168.1.0/24**

>>The filter `ip.src==192.168.154.0/24` in Wireshark displays packets where the source IP address belongs to the **192.168.154.0** subnet with a **/24 mask**, which includes IPs ranging from **192.168.154.0 to 192.168.154.255**.

## filters

| address | ip.addr==192.169.0.2 | eth.addr==ff:ff:ff |
| --- | --- | --- |
| port | tcp.port==80 | udp.port==50 |
| logical | tcp.port==80 and ip.addr==192.169.0.2 | tcp.port==80  or  ip.addr==192.169.0.2 |

## coloring

Colorization in Wireshark is a feature that helps users visually distinguish packets based on specific attributes, such as protocols, packet contents, or specific conditions. It makes analyzing network traffic more efficient by highlighting patterns or issues.

### Key Points About Colorization in Wireshark:

1. **Default Coloring Rules**:
    - Wireshark comes with predefined coloring rules for common protocols and conditions.
    - For example:
        - **Green** for TCP traffic.
        - **Blue** for DNS traffic.
        - **Yellow** for HTTP traffic.
2. **Custom Coloring Rules**:
    - Users can create or edit rules to match specific criteria.
    - Steps:
        1. Go to **View > Coloring Rules**.
        2. Click **New** to add a rule.
        3. Define a name, filter (e.g., `http` or `tcp.port == 80`), and choose a foreground/background color.
        4. Save the rule.
3. **How It Works**:
    - Wireshark applies coloring rules based on the order in the list. The first matching rule is applied.
    - Reordering rules can change the display priority.
4. **Benefits**:
    - Quickly identify protocols, errors, or specific traffic.
    - Simplifies troubleshooting by visually grouping packets.
5. **Disabling Coloring**:
    - You can toggle colorization on or off via **View > Colorize Packet List**.

Coloring rules enhance clarity during packet analysis, making it easier to detect trends, anomalies, or issues in captured data.

# promiscus mode

In Wireshark, if your network card is in promiscuous mode, it can capture traffic from other devices on the same network, even if it's not intended for your device.

**Example:**

- You have a computer running Wireshark connected to a network with multiple devices.
- Without promiscuous mode, Wireshark can only capture packets addressed to your computer.
- With promiscuous mode enabled, Wireshark can capture packets from other devices on the network, such as someone else's computer or printer, even if those packets are not meant for your machine.

This allows you to see all traffic on the network, which is useful for troubleshooting or monitoring network activity.

# we we should not use wire shark as root

reason:

>>it captures all the data if it is promiscus mode and if the attacker already has access to network then he may send the malicious packets and as soon as u capture the packet ur system becomes vulnerable and all root privileges will be compromised

# Alternate tool for wireshark

>>tshark —> it is not gui its command line interface tool

# **Wireshark Password Capture**

**example:using metasploit and ftp**

To crack an FTP password using Wireshark on Metasploitable:

1. **Set up Metasploitable** and ensure FTP is running.
2. **Connect to FTP** using the command:
    
    ```bash
    ftp 192.168.1.20
    
    ```
    
3. **Log in** with a username and password (or try multiple attempts).
4. **Start Wireshark** and capture traffic on the network interface with filter “ftp”(FTP).
5. **Look in Wireshark** for packets with "USER" and "PASS" to see the credentials in plaintext.

or

- Look at the **"USER"** and **"PASS"** FTP commands under **Statistics > Conversations** or **Statistics > Packet Lengths**.
- Find the packets containing the **username** and **password** (they’ll be in plaintext).

*****) if we dont use secure websites or protocols the passwords can be visible in captured packets**
