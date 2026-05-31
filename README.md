# Home SOC Lab

I'm building a small security operations lab at home to get hands-on with the
blue team side of cyber: collecting logs, spotting attacks, and triaging alerts
the way a SOC analyst would. I'm documenting it here as I go.

The setup runs Wazuh (a free, open source SIEM) in Docker on my Mac, with an
Ubuntu VM as a monitored endpoint. I run common attacks against the endpoint and
check what the SIEM detects, then tie each detection back to MITRE ATT&CK.

## What I'm using
- Wazuh 4.14.5 (manager, indexer, dashboard) running in Docker
- Ubuntu VM (Multipass) as the monitored endpoint, running the Wazuh agent
- macOS with Docker Desktop

## Where I'm at
**Phase 1: getting the SIEM running (done)**
Deployed the Wazuh stack with Docker Compose and logged into the dashboard.

**Phase 2: onboarding an endpoint (done)**
Spun up an Ubuntu VM, installed the Wazuh agent, and confirmed it reporting in as Active.

**Phase 3: simulating an attack and catching it (done)**
Ran a simulated SSH brute force (repeated failed logins) against the endpoint.
The SIEM caught the 8 failed authentications and mapped them to MITRE ATT&CK:
Brute Force (T1110), Password Guessing, and SSH.

**Phase 4: writing my own detection rules and cutting false positives (next)**

## Screenshots
In the screenshots folder: the SIEM dashboard, the agent reporting in, and the
brute-force detection mapped to MITRE ATT&CK.
