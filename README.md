# Enterprise SIEM Home Lab: Live Attack & Detection

## Executive Summary & Project Objective

The goal of this project was to build a Security Operations Center from scratch. I wanted to move from learning about cybersecurity concepts and actually create a working environment. This environment is different from the labs that use recordings. Instead I made a network that is protected like an one. The Security Operations Center is like an one.

I used configurations. Managed the firewalls on each computer. I also simulated attacks. Made automated alerts. The Enterprise SIEM Home Lab project shows that I can do everything needed for a Security Information and Event Management system. This includes making the Security Information and Event Management system hunting for threats and finding them automatically. The Security Information and Event Management system is very important.

## ⚙️Tools

* **Hypervisor:** Oracle VirtualBox

* **Attacker Node:** Kali Linux (NAT Network: `10.0.2.15`)

* **Victim Endpoint:** Windows 10 Pro (NAT Network: `10.0.2.3`)

* **SIEM / Indexer:** Splunk Enterprise

* **Telemetry Agents:** Splunk Universal Forwarder, Microsoft Sysmon

---

## 🛠️Phase 1: Endpoint Telemetry & Forwarding

I installed Microsoft Sysmon on the Windows 10 computer to see everything that happens on it. The Microsoft Sysmon is very useful. I set up the Splunk Universal Forwarder to send logs to the Splunk server. The Splunk Universal Forwarder is an important tool.

**Overcoming Obstacles:** The Forwarder had a problem. It would not work. I fixed this by stopping some processes and setting up the connection to the VirtualBox network. I also made a rule on the Windows Defender Firewall to let the logs be sent without turning off the computers protection. The Windows Defender Firewall is very important for protection.

![Endpoint Telemetry Proof](real%20security%20data%20(index=main%20showing%20EventCode%204672)%20split%20screen.png)

---

## ⚔️Phase 2: Adversary Simulation (Red Team)

I set up the Kali Linux computer to simulate an attack. The Kali Linux computer is like an attacker.

**Overcoming Obstacles:** The Windows computers firewall was blocking the attack so I could not see what was happening. To test the Enterprise SIEM Home Lab system I made the attacker computer connect to the Windows computer using a method. I used a Python server on the attacker computer. I made the Windows computer connect to it. The Python server is very useful.

![Kali Attack Simulation](Kali%20ifconfig%20&%20Python%20Honeypot%20server.png)

---

## 🔍Phase 3: Threat Hunting & Detection (Blue Team)

I used Splunk Enterprise to look at the logs and try to find the attack. The Splunk Enterprise is an important tool.

**Overcoming Obstacles:** I found that some logs were not being sent because the Sysmon configuration was set to ignore them. I changed the simulation to use a method that would not be ignored. I used a command to extract the information from the logs. The logs are very important for the Security Information and Event Management system.

![Splunk Threat Detection](final%20result-attack%20and%20detect%20split%20screen.png)

---

## 📊Phase 4: SOC Dashboarding & Automated Alerts

I made a dashboard to show the information. The dashboard is very useful. I also made a rule to alert me if the Security Information and Event Management system detects a connection. The Security Information and Event Management system is very important, for detecting connections.

![Splunk Dashboard](Splunk%20Pie%20Chart%20Dashboard.png)

![Triggered Splunk Alert](Splunk%20Triggered%20Alerts%20flashing%20High%20Severity.png)

## 🛠️ Technical Appendix: Troubleshooting and Hardening

We did a lot of work to make sure the environment was stable and secure.

* **Host Firewall Engineering:** We made a rule for the Host Firewall. This rule lets traffic come in on Port 9997 so that Splunk can work properly. We needed to do this for Splunk to work well.

![Firewall Rule](a%20custom%20Inbound%20TCP%20rule%20for%20port%209997.png)

* **Local Telemetry Verification:** Before we tried to fix any Splunk problems we checked if Sysmon was working correctly. We used the Event Viewer for this check.

![Event Viewer Check](event%20viewer-%20sysmon%20operational%20logs.png)

* **Service Validation:** I checked that the main programs that collect data, like Sysmon and Splunk Universal Forwarder were started and running all the time in the background.

![Service Validation](services.msc%20showing%20Sysmon%20%26%20SplunkForwarder%20%27Running%27..jpg)
