# 🛡️ Linux Administration: Apache2 Incident Response & Recovery

### 📌 Executive Summary
This lab simulates a high-priority Cloud Support Ticket involving a critical web service outage. I utilized the Linux Command Line (CLI) to perform system triage, service restoration, and post-incident verification on a remote Apache2 web server.

---

### 🛠️ Technical Competencies Demonstrated

*   Service & Lifecycle Management: Orchestrated service states using 'systemctl' (Status, Stop, Restart).
*   System Observability: Leveraged 'top', 'df -h', and 'tail -f' for real-time resource monitoring and log analysis.
*   Administrative Configuration: Managed root-level directory indexing and file permissions using 'tee', 'mv', and 'echo'.
*   Network Triage: Verified service reachability using 'curl'' and browser-side cache resolution.

---

### 🚨 Incident Report: Web Service Outage & Restoration

#### Phase 1: Baseline Service Validation (The "Green Light")
Prior to the simulation, the system was audited to ensure Service Integrity. 
*   Action: Executed systemctl status apache2 to confirm the daemon was in an active (running) state.
*   Evidence: ![Service Status: Active](./Active-status.png)

#### Phase 2: Simulated Service Failure & Impact Analysis
To replicate a production outage, the Apache2 service was manually terminated to analyze the impact on end-user accessibility.
*   Observation: System logs confirmed the service transitioned to an inactive (dead) state.
*   User Impact: Browser-side requests returned a Connection Refused error, confirming a total service blackout.
*   Evidence: 
    *   ![CLI Output: Inactive](./Inactive-status.png)
    *   ![User Experience: Connection Error](./Connection-error.png)

#### Phase 3: Service Recovery & Deployment Verification
The incident was resolved by re-initializing the service and deploying a custom verification page to ensure administrative control over the web root (/var/www/html).
*   Recovery: Successfully restarted the service via systemctl restart apache2.
*   Deployment: Utilized echo piped through tee to inject a custom verification string into index.html.
*   Final Verification: Confirmed full restoration via browser-side validation of the custom deployment.
*   Evidence: ![Final Verification: Custom Message](./Custom-message.png)

---
Status: Incident Resolved. 🟢
