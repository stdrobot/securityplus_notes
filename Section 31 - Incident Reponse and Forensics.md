# 31.1 Incident Resopnse Procedures
- **Incident Management Program**: program consisting of the monitoring and detection of security events on a computer network and the execution of proper responses to those security events
	- Preparation, ID-ing, containment, eradication, recovery, lessons learned
- **Identification**: process of recognizing whether an event that occurs should be classified as an incident
- **Containment**: is focused on isolating the incident
- **Eradication**: is about removing the threat
- **Recovery**: focused on data restoration system repair, and re-enabling any servers or networks taken offline during the incident response

# 31.2 Incident Response Planning
- Key people that are available to respond to any incident that meets the severity threshold set out by the incident response plan
	- Incident Response Manager
	- Security Analysts
	- Triage analyst
	- Forensic analyst
	- Threat researcher
	- Cross functional support
- CSIRT should be the single point of contact for security incidents and may be a part of the SOC or an independent team
- Team must have a secure method of communication regarding incidents
- Figure out a plan
- Notifications are obviously based on how organizations do this
	- Email, web portals, phone calls, in-person updates, voicemail, and formal reports
- Anything that goes outside of the security team goes out to affected stakeholders
	- **Senior Leadership**: executives and managers who are responsible for business operations and functional areas
	- **Regulatory bodies**: governmental orgs that oversee the compliance with specific regulations and laws
	- **Legal teams**: Org's legal counsel is responsible for mitigating risk from civil lawsuits
	- **Law enforcement**: may provide services to assist in your incident handling efforts or prepare for legal action against the attacker in the future
	- **Human resources**: used to ensure no breaches of employment law or employee contracts is made during an incident response
	- **Public relations**: used to manage negative publicity from a serious incident

# 31.3 Investigative Data
- **Security Information and Event Monitoring (SIEM)**: a combo of different data sources into one tool that provides real-time analysis of security alerts generated by hardware and applications
	- **Sensor**: endpoint being monitored
	- **Sensitivity**: how much you'll be logging
	- **Trends**: GUI has a huge impact on reading trends in certain areas (i.e. how often shutdowns occur)
	- **Alerts**: see that certain alerts happen under circumstances
	- **Correlation**: how different events are related
- **Log files**: a file that records events that occur in an OS or other software runs, or messages between different users
	- Network, System, App, Security, Web, DNS, Authentication, Dump Files, VoIP, Call Managers can all have logs
- **syslog/rsyslog/syslog-ng**: three variations of syslog which all permit the logging of data from different types of systems in a central repo
- **journalctl**: Linux CLI tool used for querying and displaying logs from journald, the systemd logging service on Linux
- **nxlog**: log management tool that helps to easily ID security risks, policy breaches, or analyze operational problems in server logs, oepration system logs, and application logs
- **netflow**: network protocol system created by Cisco. Coolects active IP network traffic, including point of origin, destination, volume, paths on the network
- **sflow**: sampled flow. Provides a means for exporting truncated packets, together with interface counters for network monitoring
- **IP Folow Information Export (IPfix)**: universal standard of export for IP flow information from routers, probes, and other devices that are used by mediation systems, accounting/billing systems, and network management systems. Facilitates services like measurement, accounting, and billing. Defines how IP flow information is formatted
- **Metadata**: data that describes other data by providing an underlying definition or description
	- Email, mobile, web, file

# 31.4 Forensic Procedures
- **Identification**: ensure the scene is safe, secure, the scene to prevent evidence contaomination, and identify the scope of evidence to be collected
- **Collection**: ensure authorization to collect evidence is obtained, and then document prove the integrity of evidence as it is collected
- **Analysis**: create a copy of evidence for analysis and use repeatable methods and tools during analysis
- **Reporting**: create a report of the methods and tools used in the investigation and present detailed findings and conclusions based on the analysis
- **Legal hold**: process designed to preserve all relevant info when litigation is reasonably expected
- A computer or server can be considered evidence
- Appoint a **liaison** with legal knowledge and expertise who can be the point of contact with the law
- Code of ethics:
	1. Analysis must be performed without bias
	2. Analysis methods must be repeatable by third parties
	3. Evidence cannot be changed
- **Timeline**: shows the sequence of file system events within a source image in a graphical format
	- How was access to the system obtrained?
	- What tools have been installed?
	- What changes to files were made?
	- What data has been retrieved?
	- Was data exfiltrated?
- Many forensic tools can generate a timeline (i.e. The Sleuth Kit / Autopsy)
- Use a spreadsheet if you don't use any tools that support this

# 31.5 Data Collection Procedures
- For a compromised machine, create a forensic disk image of the data as evidence
- Collection will look at the following steps:
	- Capture and hash system images
	- Analyze data with tools
	- Capture screenshots
	- Review network traffic and logs
	- Capture video
	- Consider order of volatility
		- Which component is being changed faster? Cache is the shortest, then memory, swap files, disks
	- Take statements
	- Review licensing and documentation
	- Track man-hours and expenses
- **FTK** and **EnCase** are popular forensic tools
- **Data Acquisition**: method and tools used to create a forensically sound copy of data from a source devices, such as system meory or a hard disk
	- BYOD complicates this because you probably can't legally acquire this device
- Some data can only be collected after a shutdown or power DC
- Follow the **order of volatility**:
	- CPU registers and cache memory
	- Contents of system memory (RAM), routing tables, ARP caches, process table, temp swap files
	- Data on mass storage (HDDs/SDDs/flash)
	- Remote logging and monitoring data
	- Physical configs and network topology
	- Archival media
- Most registries are stored on the disk,but some are only stored in memory
# 31.6 Security Tools
- #### Networking
	- **Tracert**: diagnostic command for displaying possible routes and measuiring transit delays of packets across an IP
	- **nslookup**: determines the IP address associated with a domain name, obtain the mail server settings, and other DNS info
	- **ipconfig/ifconfig**: displays all network configs of the currently connected network devices and can modify DHCP/DNS settings
	- **nmap**: open-source network scanner that is used t odiscover hosts and services on a network by pinging
	- **ping**: determines if a host is reachable on an IP network
	- **hping**: open-source packet generator and analyzer for TCP/IP that is used for auditing and testing of firewalls/networks
	- **netstat**: displays network connections for TCP, routing tables, and a number of interfaces/protocol stats
	- **netcat**: reading from and writing to network connections using TCP/UDP which is a dependable back-end that can be used directly or easily driven by other programs and scripts
	- **arp**: viewing amd modifying the local Address Resolution Protocol (ARP) caches on a given host
	- **route**: used t oview and manipulate the IP routing table on a host or server
	- **curl**: CLI tool to transfer data to or from a server. Supports HTTP, FTP, POP3, SCP, SFTP, SMTP, TFTP, TELNET, LDAP, and FILE
	- **the harvester**: python reconaissance script that gathers emails, subdomains, hosts, employee names, open ports and banners from different public sources like search engines
	- **sn1per**: automated scanner that pentesters use to enumerate and scan for vulns across a network
	- **scanless**: used to create an exploitation website that can perform open port scans in a stealthy manner
	- **dnsenum**: used for DNS enumeration to locate all DNS servers and entries for a given org
	- **Nessus**: proprietary vuln scanner that remotely scans a computer or network for vulns
	- **Cuckoo**: open-source software that automates analysis of suspicious files
- #### File Manipulation
	- **head**: CLI tool for outputting the first ten lines of a file provided to it
	- **tail**: SEE HEAD, but last ten lines
	- **cat (concatenate)**: CLI tool for outputting the contents of a file to the screen
	- **grep**: CLI tool for searching plaintext data sets for lines that match a regular expression or pattern
	- **chmod**: used to change the access permissions of file system objects
	- **logger**: provides an easy way to add messages to the `/var/log/syslog` file from the command line or from other files
- #### Shell and Scripts
	- **SSH**: supports encrypted data transfer between two computers for secure logins/file transfers/general purpose connections
	- **PowerShell**: task automation and config management framework from Microsoft, consisting of a CLI shell and the associated scripting language
	- **Python**: interpreted, high-level and general-purpose programming language
	- **OpenSSL**: library for applications that secures communications over computer networks against eavesdropping or need to ID the party at the other end
- #### Packet Capture
	- **tcpdump**: allows capturing and analysis of network traffic going through your system
	- **tcpreplay**: suite of free open source utilities for editing and replaying previous capture network traffic
	- **Wireshark**: captures network packets and displays them at a granular level for real-time or offline analysis
- #### Forensics
	- **dd**: CLI tool used to copy disk images using a bit by bit copying process
	- **FTK Imager**: data preview and imaging tool that lets you quickly assess electronic evidence to determine if furhter analysis with another tool is needed
	- **Memdump**: CLI tool used to dump system memory to the standard output stream by skipping over holes in memory maps
	- **WinHex**: commercial disk editor and universal hexadecimal editor used for data recovery and digital forensics
	- **Autopsy**: GUI for The Sleuth Kit and other digital forensics tools
- #### Exploitation
	- **Metasploit**: computer security tool that offers info about software vulnerabilities, IDS signature development, and improves pentesting
	- **Browser Exploitation Framework**: can hook one or more browsers and can use them as a beachhead of launchying various direct commands and further attacks against the system from within the browser context
	- **Cain and Abel**: password recovery tool that can be used through sniffing the network, cracking encrypted passwords using brute-force, dictionary, and cryptanalysis attacks, recording VoIP convos, decoding scrambled passwords, revealing password boxes, and analyzing routing protocols
	- **John the Ripper**: open source password security auditing and password recover tool available for many OSes
