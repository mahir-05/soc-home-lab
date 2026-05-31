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
**1. Stood up the SIEM** - deployed the Wazuh stack with Docker Compose and logged into the dashboard.

**2. Onboarded an endpoint** - spun up an Ubuntu VM, installed the agent, confirmed it reporting in as Active.

**3. Simulated an attack and detected it** - ran a simulated SSH brute force against the endpoint; the SIEM caught the failed logins and mapped them to MITRE ATT&CK (Brute Force T1110, Password Guessing, SSH).

**4. Wrote my own detection rule** - added a custom rule (ID 100100, level 10) that fires when someone logs in with the known-bad username "hacker", tagged to MITRE T1110. Re-ran the attack and confirmed my rule fired on all 8 attempts.

## What I learned
- How a SIEM collects and correlates endpoint logs end to end
- Triaging alerts and mapping them to MITRE ATT&CK
- Writing and validating custom detection rules

## Screenshots
In the screenshots folder: the SIEM dashboard, the agent active, the brute-force
detection mapped to MITRE ATT&CK, and my custom rule firing.
