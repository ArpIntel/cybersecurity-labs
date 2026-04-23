Intrusion Detection with Snort

Subject: Network Security UTS  
Tools Used: Snort, Linux CLI  
Topics: IDS Configuration, Network Monitoring, Rule Writing, Alert Management

Overview
This lab focused on setting up and configuring Snort as a network-based intrusion detection system (IDS). 
Rather than just reading about how IDS works, the lab involved writing actual rules, triggering alerts, and observing how Snort responds to different types of traffic in real time.

What I Did
Scoping the Network Interface
Updated Snort's `ipvar` configuration to monitor the local network specifically, rather than listening on any/all interfaces. 
This is a basic but important step  in a real deployment you want your IDS watching the right segment of traffic.

Writing and Testing ICMP Rules
Wrote a custom Snort rule to generate alerts whenever an ICMP packet was received, 
then verified it by pinging the monitored host. Watched the alerts appear on the console in real time. Simple rule, but it confirms the detection pipeline is working end to end.

IDS Mode with Console Alerts
Configured Snort to run in IDS mode with console output, 
confirming that pings from external hosts triggered the expected alerts while the system logged the activity correctly.

Web Traffic Detection Rules
Wrote a specific Snort rule targeting web service traffic (HTTP). 
This kind of rule is relevant for detecting things like unusual request patterns or scanning activity against a web server.

Telnet Detection Rules
Added rules to detect Telnet connection attempts. Telnet is inherently insecure (credentials sent in plaintext) and flagging it is a common real-world security baseline  
most organisations either block it entirely or monitor for it.

 Key Takeaways

- Writing Snort rules manually gives you a much deeper understanding of what commercial SIEM tools are doing under the hood
- The difference between IDS (detect and alert) and IPS (detect and block) is architectural  Snort can do both depending on how it's deployed
- Scoping your monitoring to the right network segment matters a lot for reducing noise and false positives

Skills Demonstrated
Snort, IDS Configuration, Rule Writing, Network Traffic Analysis, ICMP Monitoring, Telnet Detection, Linux CLI
