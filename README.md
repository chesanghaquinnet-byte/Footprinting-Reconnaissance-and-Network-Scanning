# Footprinting-Reconnaissance-and-Network-Scanning
A hands-on cybersecurity lab documenting footprinting, reconnaissance, information gathering, and local network scanning using Kali Linux, Nmap/Zenmap, and other reconnaissance tools week2 project with Networkwalks

## Overview

This repository documents my hands-on cybersecurity practical on footprinting, reconnaissance, information gathering, and network scanning.

The practical started with gathering information about a Networkwalks.com using different reconnaissance tools in Kali Linux. I then moved to network scanning using Zenmap/Nmap to identify live hosts on my local subnet and collect information such as IP addresses and MAC addresses.

This project helped me understand how reconnaissance and scanning are used during the early stages of a cybersecurity assessment.


## Objectives

The main objectives of this practical were to:

* Understand the concept of footprinting and reconnaissance.
* Gather information about a target using different reconnaissance tools.
* Understand how WHOIS information can be collected.
* Identify technologies and information associated with a website.
* Examine DNS information.
* Check HTTP response headers.
* Identify possible web application firewalls.
* Perform network discovery using Zenmap.
* Identify live hosts on a local subnet.
* Identify the IP addresses and MAC addresses of live hosts.
* Generate and save a network topology.


## Part 1 — Footprinting and Reconnaissance

**What is Footprinting and Reconnaissance**?

Footprinting and reconnaissance are information-gathering activities carried out during the early stages of a cybersecurity assessment.

The purpose is to collect useful information about a target before moving to other security testing activities.

During this practical, I used several tools to gather different types of information.


## Tools Used

## 1. WHOIS

WHOIS was used to retrieve publicly available registration information associated with a domain,networkwalks.com.

I ran the WHOIS command from my Kali Linux terminal and saved the output for documentation and later use in my report.
Command used:
 ```bash
whois networkwalks.com
```

## What I found
From the WHOIS results, I was able to gather information such as:

* Domain name
* Domain registration and expiry dates
* Registrar information
* Domain status
* Name servers
* Other publicly available registration details.

## Evidence  

###WHOIS Result
![WHOIS Result](1-whois-networkwalks.png)

## 2. WhatWeb

WhatWeb was used to gather information about the technologies used by networkwalks.com.

It can help identify technologies such as web servers, frameworks, content management systems, JavaScript libraries and other technologies associated with a website.

command used:
### WhatWeb

```bash
whatweb networkwalks.com
```

## Evidence

###Whatweb Result
![Whatweb Result](2-whatweb-networkwalks.png)

## 3. NSLookup

NSLookup was used to gather DNS information about the networkwalks.com domain.

command used:
```bash
nslookup networkwalks.com
```

## What I found
The command returned DNS information for networkwalks.com, including the domain’s IP address and the DNS server that provided the response.

This information is useful during reconnaissance because it helps identify the IP address associated with a domain and understand how the domain is resolved on the internet.

## Evidence

###Nslookup Result
![Nslookup Result](3-nslookup-networkwalks.png)

## 4. cURL

cURL was used to inspect the HTTP response headers returned by the networkwalks.com website.
command used:
```bash
curl -I https://networkwalks.com
```
## What I Found

The command returned the HTTP response headers from the website. The response showed the HTTP status code and other information about how the web server responded to the request.

This information is useful during reconnaissance because HTTP headers can reveal details about the website’s server, security configurations, content type, and how the website handles web requests.

## Evidence
### Curl Result
![Curl Result](4-curl-I-networkwalks.png)


## 5. WAFW00F

WAFW00F was used to check whether a Web Application Firewall (WAF) was protecting the networkwalks.com website.

command used:
```bash
wafw00f networkwalks.com
```

## What I Found

The WAFW00F scan checked networkwalks.com for the presence of a Web Application Firewall. The result showed whether a WAF was detected and, if identified, the type of WAF protecting the website.

This information is useful during reconnaissance because it helps identify security technologies that may be deployed in front of a web application.

## Evidence

### WafW00f Result
![Wafw00f Result](5-wafw00f-networkwalks.png)

## 6. DNSRecon

DNSRecon is a DNS enumeration tool used to gather information about DNS records and configurations.

What I did

I used DNSRecon with the -d option to enumerate DNS information for the target domain.
command used:
```bash
dnsrecon -d networkwalks.com
```

## What I found
I used DNSRecon to enumerate the DNS information available for networkwalks.com. The tool returned DNS records and information associated with the domain, including the DNS infrastructure and records identified during the enumeration.

The results were saved and documented as part of my reconnaissance process for further analysis and reporting.

## Evidence

### Dnsrecon Result
![Dnsrecon Result](6-dnsrecon-networkwalks.png)



## Part 2 — Network Scanning with Zenmap

After completing the footprinting and reconnaissance activities, I moved on to network scanning.

For this section, I used Zenmap, the graphical user interface for Nmap.

The purpose of this practical was to identify live hosts on my local network and collect information about them.

## Tools Used

* Windows Command Prompt
* Zenmap
* Nmap

## 1. Finding My Local IP Address and Subnet

Before performing the scan, I used Windows Command Prompt to identify my local network information.

command used:
```cmd
ipconfig
```

## The information I obtained was:

Information       Result

IPv4 Address    172.20.10.10

Subnet Mask     255.255.255.240

Default Gateway  172.20.10.1

Network/Subnet   172.20.10.0/28

The subnet mask 255.255.255.240 corresponds to /28.

## Evidence

### Ipconfig Result

![Ipconfig Result](7-windowscmd-networkwalks.png)

## 2. Configuring the Zenmap Scan

I opened Zenmap and entered my local subnet as the target 
172.20.10.0/28.

I then performed the scan to identify the active hosts within the subnet.

Zenmap provided information about the hosts that responded to the scan.

## 3. Live Hosts Discovered

The Zenmap scan identified 3 live hosts within my local subnet.

| No. | IP Address | MAC Address | Status |
|---|---|---|---|
| 1 | 172.20.10.1 | B2:8C:75:89:C1:64 | Up |
| 2 | 172.20.10.7 | 1A:50:75:F2:76:3D | Up |
| 3 | 172.20.10.11 | 9C:2F:9D:A0:2E:2F | Up |

## Total Number of Live Hosts

The total number of live hosts discovered during the Zenmap scan was 3.

## Evidence

### Zenmap Result
![Zenmap Result](8-zenmap-networkwalks.png)


## Real-World Implications

## Finding:
The Nmap scan identified three active hosts on the network. Their IP addresses and MAC addresses were also discovered.

## Implication:
Identifying active hosts gives a security professional a better understanding of the devices present on the network. The IP addresses can help identify and communicate with specific devices, while MAC addresses can provide additional information for identifying devices on the local network.

## Potential Impact:
If this information is exposed to an unauthorized person, it could help them map the network and identify potential targets for further reconnaissance. This could increase the organization’s attack surface and make it easier to plan future attacks.

## Recommended Next Steps:
The identified hosts should be reviewed to confirm that they are authorized devices. Network administrators can also monitor the network for unknown devices, apply appropriate access controls, and limit unnecessary exposure of network information.

## Network Topology

After completing the scan, I used Zenmap’s topology feature to visualize the discovered hosts and their relationship within the network.

The topology output was saved in PDF format as required by the practical.

## Topology Evidence

### Zenmap Topology Result
![Zenmap Topology Result](nmap-zenmap.pdf)


 ## Summary of the Practical

During this practical, I worked through two major stages:

Stage 1 — Footprinting & Reconnaissance

I used:

* WHOIS
* WhatWeb
* NSLookup
* cURL
* WAFW00F
* DNSRecon

These tools helped me understand different methods of gathering information about a target from publicly accessible services and responses.

## Stage 2 — Network Scanning

I used:

* Windows ipconfig
* Zenmap
* Nmap

I first identified my local network information and then scanned my local subnet. The scan allowed me to identify live hosts and obtain information such as their IP and MAC addresses.


## What I Learned

This practical helped me understand that reconnaissance is an important part of cybersecurity because information about a target can be collected from several different sources.

I also learned that different tools provide different types of information. WHOIS focuses on domain registration information, WhatWeb performs web technology fingerprinting, NSLookup works with DNS queries, cURL allows me to inspect HTTP responses, WAFW00F can identify possible WAFs, and DNSRecon performs DNS enumeration.

The Zenmap practical also helped me understand how network scanning can be used to discover active devices within a network and how IP addresses, MAC addresses, and network topology can be documented.

Most importantly, I gained practical experience using tools that I had previously only learned about theoretically.



## Project Report
![View Project Report](zenmap-network-scanning-report.pdf)


## Ethical Consideration

The techniques and tools used in this practical should only be used on systems and networks where I have permission to perform testing.

Reconnaissance and scanning can provide sensitive information about systems and networks, so responsible and authorized use is essential.



## Conclusion

This practical gave me hands-on experience with cybersecurity reconnaissance and network scanning.

I started by gathering information using several footprinting and reconnaissance tools and then moved into network discovery using Zenmap.

The practical helped me connect the concepts I have been learning in cybersecurity with real command-line and graphical tools.

This is another step in my journey from learning cybersecurity concepts to gaining practical, hands-on experience.






# 👤 Author

**Chesangha Quinneta**

**Networkwalks 2026 Intern**


LinkedIn:[https://www.linkedin.com/in/cyber~-nneta-77a37b3ab?utm_source=share_via&utm_content=profile&utm_medium=member_ios

---

##  Project Information

**Program Name:** Cybersecurity at Networkwalks | **Week:** 02 | **Project:** Cybersecurity & Pentesting Footprinting&scanning | **Repository:** GitHub


