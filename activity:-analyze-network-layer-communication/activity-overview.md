# Activity Overview

In this activity, you will analyze DNS and ICMP traffic in transit using data from a network protocol analyzer tool. You will identify which network protocol was utilized in the assessment of the cybersecurity incident.

In the internet layer of the TCP/IP model, the IP formats data packets into IP datagrams. The information provided in the datagram of an IP packet can provide security analysts with insight into suspicious data packets in transit.

Knowing how to identify potentially malicious traffic on a network can help cybersecurity analysts assess security risks on a network and reinforce network security.

**Be sure to complete this activity before moving on.** The next course item will provide you with a completed exemplar to compare to your own work.

---

# Scenario

Review the scenario below, then complete the step-by-step instructions.

You are a cybersecurity analyst working at a company that specializes in providing IT services for clients. Several customers of clients reported that they were not able to access the client company website **www.yummyrecipesforme.com**, and saw the error “destination port unreachable” after waiting for the page to load.

You are tasked with analyzing the situation and determining which network protocol was affected during this incident. To start, you attempt to visit the website and you also receive the error **“destination port unreachable.”** To troubleshoot the issue, you load your network analyzer tool, `tcpdump`, and attempt to load the webpage again.

To load the webpage:
1. Your browser sends a query to a DNS server via the UDP protocol to retrieve the IP address for the website's domain name. This is part of the **DNS protocol**.
2. Your browser then uses this IP address as the destination IP for sending an HTTPS request to the web server to display the webpage.

The analyzer shows:
- When you send UDP packets to the DNS server, you receive **ICMP packets** containing the error message: `udp port 53 unreachable`.

---

![image](https://github.com/user-attachments/assets/bed8eb75-7214-485c-a101-6ef7d6811fb7)


## Tcpdump Log Analysis

### 1. Initial Outgoing Request
The first two lines of the log file show the initial outgoing request from your computer to the DNS server, requesting the IP address of `yummyrecipesforme.com`. This request is sent in a UDP packet.  

---

### 2. Error Response from the Server
The third and fourth lines of the log file show the response to your UDP packet.  
- The ICMP packet from `203.0.113.2` indicates the start of the error message.  
- The error message highlights that the UDP packet was undeliverable to **port 53** of the DNS server.  

---

### 3. Timestamps of the Incident
- Each request and response in the log is preceded by a timestamp.  
- Example: `13:24:32.192571` represents the time as **1:24 p.m., 32.192571 seconds**.  

---

### 4. Source and Destination IP Addresses
- **First Line (UDP Request):**  
  - **Source IP Address:** `192.51.100.15` (Your computer's IP address)  
  - **Destination IP Address:** `203.0.113.2.domain` (DNS server's IP address)  
- **ICMP Error Response:**  
  - **Source IP Address:** `203.0.113.2` (DNS server's IP address)  
  - **Destination IP Address:** `192.51.100.15` (Your computer's IP address)  

---

### 5. Additional Details
- **Query Identification Number:** `35084`  
  - The query identification number has a `+` symbol, indicating flags associated with the UDP message.
  - The `"A?"` flag indicates a DNS request for an **A record**, which maps a domain name to an IP address.  
- **Protocol of the Response:** `ICMP`  
  - The response includes an ICMP error message.  

---

### 6. Error Message Details
- The error message `"udp port 53 unreachable"` is displayed in the last line of the log.  
- **Port 53:** This port is used for DNS service.  
- The term `"unreachable"` indicates that the UDP message requesting an IP address for `www.yummyrecipesforme.com` did not reach the DNS server, as no service was listening on the receiving DNS port.  

---

### 7. ICMP Packets Sent Multiple Times
- The remaining lines in the log confirm that ICMP packets were sent **two more times**, but the same delivery error was received both times.  

---

## Next Steps
Now that the data packets have been analyzed, it is your responsibility to:
1. Identify the **network protocol** and **service** impacted by this incident.  
2. Prepare a follow-up report with your findings.  

---

## Additional Context
As an analyst, inspecting network traffic and network data helps determine the root cause of network-related issues during cybersecurity incidents. In this course, you will later explore how to manage and resolve incidents effectively.  

In the meantime, this event is being handled by **security engineers** after the issue was escalated to your direct supervisor.
