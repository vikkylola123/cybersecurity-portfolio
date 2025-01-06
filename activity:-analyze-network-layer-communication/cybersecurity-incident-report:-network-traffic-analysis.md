## Part 1: Summary of the Problem Found in DNS and ICMP Traffic Log

The UDP protocol reveals that when attempting to contact the DNS server to retrieve the IP address for the domain of yummyrecipesforme.com website, the ICMP protocol responded with an error message. The UDP message going from your browser to the DNS server is shown in the first two lines of the log event, then the ICMP error response from the DNS server is on the third and fourth line showing the error message, “UDP port 53 unreachable.” UDP port 53 is heavily associated with DNS traffic meaning there is an issue with the DNS server. This issue is also prevalent due to the query identification number 35084 indicating flags with the UDP message and the “A” symbol indicating flags performing DNS protocol operations. Due to the ICMP error response message about port 53, the likely issue is that the DNS server isn't responding. This is also supported by the flags associated with the outgoing UDP message and domain name retrieval.

---

## Part 2: Analysis of the Data and Cause of the Incident

### Time Incident Occurred:
The incident occurred at 1:24 p.m. after several customers reported receiving a “destination port unreachable” error message when attempting to reach the yummyrecipesforme website. The IT department has attempted to troubleshoot the issue using the tcpdump network analyzer tool. In which they found that port 53 was unreachable. Next, we will attempt to investigate if the server is down or traffic to port 53 is blocked by the firewall. A possible cause for the DNS server being down could be due to a Denial of Service attack or a misconfiguration.

