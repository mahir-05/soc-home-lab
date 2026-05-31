# Home SOC Lab

I'm building a small security operations lab at home to get hands-on with the
blue team side of cyber: collecting logs, spotting attacks, and triaging alerts
the way a SOC analyst would. I'm documenting it here as I go.

The setup runs Wazuh (a free, open source SIEM) in Docker on my Mac. Once an
endpoint is reporting in, I'll run a few common attacks against it and see what
the SIEM catches, then tie each detection back to MITRE ATT&CK.

## What I'm using
- Wazuh 4.14.5 (manager, indexer, dashboard) running in Docker
- macOS with Docker Desktop

## Where I'm at
**Phase 1: getting the SIEM running (done)**
Deployed the Wazuh stack with Docker Compose, generated the certs it needs,
confirmed all three containers were up, and logged into the dashboard.

**Phase 2: onboarding an endpoint (next)**

**Phase 3: simulating attacks and catching them**

**Phase 4: mapping detections to MITRE ATT&CK and cutting down false positives**
