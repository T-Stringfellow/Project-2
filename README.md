# Project-2: Complete Penetration Test Report

## Project Description

This second project is a simulation of a Red Team vs Blue Team scenario, where both the role of pentester and SOC analyst are played.

As the red team a vulnerable VM was attacked, ultimately resulting in root access to the machine. As the Blue Team, Kibana was used to review logs captured during the attack, these logs were then used to extract hard data and create visualizations for the final report.

The log data was then interpreted in order to suggest mitigation strategies for each exploit that was successfully performed.


### Project Objectives

This project will apply the knowledge and use of the following skills and tools:

- Penetration testing with Kali Linux.
- Log and incident analysis with Kibana.
- System hardening and configuration.
- Reporting, documentation, and communication.


**The technical skills of this project were performed in a lab environment located in Windows Azure Lab Services.**


### Red Team

Before performing the attack it was essential to setup the backend logs to capture the attack data.

<details>
    <summary>Click here to see beats and commands used to set up Kibana.</summary>
  <br>

**Filebeat**
- `filebeat modules enable apache`
- `filebeat setup`
  
**Metricbeat**
- `metricbeat modules enable apache`
- `metricbeat setup`
  
**Packetbeat**
- `packetbeat setup`
  
**Restarting to ensure they working and operational**
- `systemctl restart filebeat`
- `systemctl restart metricbeat`
- `systemctl restart packetbeat`
  
</details>

<br>

**Red Team Instructions**

1. Discover the IP address of the Linux web server.
2. Locate the hidden directory on the web server.
3. Brute force the password for the hidden directory using Hydra.
4. Break the hashed password with the Crack Station website or John the Ripper.
5. Connect to the server via WebDAV.
6. Upload a PHP reverse shell payload.
7. Execute payload to open up a meterpreter session.
8. Find and capture the flag.


### Blue Team

**Blue Team Instructions**

Using Kibana to analyze logs taken during the Red Team attack, new alert thresholds and criteria can be established to help mitigate against future attacks.

Post-attack analysis of logs enables many different avenues for growth, such as:
- Development of breach detection skills.
- Deeper understanding of the effectiveness of different attack strategies.
- A more finely tuned comprehension of baselines and alert thresholds.

**Creating Dashboards**

The following panels were deployed to assist with analyzing the following reports:
- `HTTP status codes for the top queries [Packetbeat] ECS`
- `Top 10 HTTP requests [Packetbeat] ECS`
- `Network Traffic Between Hosts [Packetbeat Flows] ECS`
- `Top Hosts Creating Traffic [Packetbeat Flows] ECS`
- `Connections over time [Packetbeat Flows] ECS`
- `HTTP error codes [Packetbeat] ECS`
- `Errors vs successful transactions [Packetbeat] ECS`
- `HTTP Transactions [Packetbeat] ECS`

Using the search queries in the Discover screen with packetbeat the following criteria were able to be addressed:
1. Identifying the offensive traffic.
2. Isolating the request for the hidden directory.
3. Identifying the brute force attack.
4. Detecting the WebDAV connection.
5. Illuminating the reverse_tcp shell and meterpreter traffic.


### Please view the Presentation to view the complete report.

GOTO https://github.com/T-Stringfellow/Project-2/blob/main/PenTest-Report.pdf