# Home SOC Lab

I built a small security operations lab at home to get hands-on with the blue
team side of cyber: collecting logs, spotting attacks, triaging alerts, and
writing my own detection rules the way a SOC analyst would.

The setup runs Wazuh (a free, open source SIEM) in Docker on my Mac, with an
Ubuntu VM as a monitored endpoint. I run attacks against the endpoint, check
what the SIEM detects, map each detection to MITRE ATT&CK, and write custom
rules to catch things the defaults miss.

## What I used
- Wazuh 4.14.5 (manager, indexer, dashboard) in Docker
- Ubuntu VM (Multipass) as the monitored endpoint, running the Wazuh agent
- macOS with Docker Desktop

## What I did
1. Stood up the SIEM - deployed the Wazuh stack with Docker Compose and logged into the dashboard.
2. Onboarded an endpoint - spun up an Ubuntu VM, installed the agent, confirmed it reporting in as Active.
3. Detected a brute-force attack - simulated an SSH brute force; the SIEM caught the failed logins and mapped them to MITRE ATT&CK (Brute Force T1110, Password Guessing, SSH).
4. Wrote my own detection rule - added a custom rule (ID 100100, level 10) that fires on logins from the known-bad username "hacker", tagged to T1110, and confirmed it fired.
5. Added file integrity monitoring - turned on real-time monitoring of a folder, tampered with a file, and the SIEM flagged the unauthorised change (Integrity checksum changed, rule 550).

## What I learned
- How a SIEM collects and correlates endpoint logs end to end
- Triaging alerts and mapping them to MITRE ATT&CK
- Writing custom detection rules and using file integrity monitoring

## Screenshots
In the screenshots folder: the SIEM dashboard, the agent active, the brute-force
detection mapped to MITRE ATT&CK, my custom rule firing, and the file integrity alert.
