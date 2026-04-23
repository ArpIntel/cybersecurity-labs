Firewall Configuration with iptables
Subject: Network Security  UTS
Tools Used: iptables, Linux CLI, SSH
Topics: Firewall Rules, Traffic Filtering, Network Access Control, Host Hardening

Overview
This lab involved configuring iptables on a Linux host to control inbound and outbound network traffic. 
The environment simulated a real network with a cybersecurity server, a legitimate client, and an attacker VM  which made it easy to see the direct impact of each firewall rule.

What I Did
Dropping All Traffic (Default Deny)
Started with a default-deny policy  configured iptables to drop all incoming traffic. 
This is the baseline for any properly hardened server. The result was that all pings and connections failed, confirming the rules were active.

Allowing Trusted Source Traffic
Added a rule to allow traffic specifically from the cybersec-server (10.0.2.6). Pings from that host succeeded while the attacker VM remained blocked  
exactly the behaviour you'd want in a production environment where only known sources should have access.

Blocking the Attacker VM
With the allowlist rule in place, verified that the attacker VM could not reach the server. This demonstrated how source-based filtering works and why IP allowlisting 
is a useful layer of defence (while also understanding its limitations in real environments where IPs can be spoofed).

SSH Access Control
Tested SSH connectivity before and after applying firewall rules. Configured iptables to restrict SSH access to authorised hosts only  a critical hardening step since SSH is a common attack vector.

Permitting HTTP and HTTPS
Configured the firewall to allow inbound HTTP (port 80) and HTTPS (port 443) traffic on the cybersec-server, 
while keeping everything else locked down. This reflects a typical web server hardening pattern that only opens the ports you actually need.

Key Takeaways
Default-deny with explicit allowlisting is the right approach to firewall configuration  not default-allow with a blocklist
iptables rule order matters  rules are evaluated top-down and the first match wins
The combination of SSH restriction + HTTP/HTTPS allowlisting represents a realistic baseline config for a hardened Linux web server

Skills Demonstrated
iptables, Firewall Configuration, Network Access Control, SSH Hardening, Traffic Filtering, Linux Host Security, Default-Deny Policy

