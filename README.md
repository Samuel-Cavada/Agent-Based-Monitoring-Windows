<p align="center"
  <a href="https://github.com/Samuel-Cavada" target="_blank"
    <img src="https://img.shields.io/badge/Back_to_Main_Page-000000?style=for-the-badge&logo=github&logoColor=white" alt="Back to Main Page"/
  </a
</p

<h1 align="center"Windows VM Agent-Based Vulnerability Scanning with Tenable</h1

<p align="center"
  <img src="https://img.shields.io/badge/Platform-Local%20VM-0078D4?style=for-the-badge&logo=microsoft&logoColor=white" alt="Cloud Platform" /
  <img src="https://img.shields.io/badge/OS-Windows%2010-0078D6?style=for-the-badge&logo=windows&logoColor=white" alt="OS" /
  <img src="https://img.shields.io/badge/Tool-Tenable.io-00B388?style=for-the-badge&logo=tenable&logoColor=white" alt="Tool" /
  <img src="https://img.shields.io/badge/Focus-Agent%20Based%20Scanning-orange?style=for-the-badge" alt="Focus Area" /
</p

---

## Project Objective
 This project demonstrates how to provision a Windows Virtual Machine, deploy a Tenable Nessus Agent, and perform an agent-based vulnerability scan. The focus is on securely installing the agent, triggering the scan, monitoring its completion, and properly deprovisioning all assets.

---

## Tools & Technologies
- **Platform:** Local Virtual Machine
- **OS:** Windows 10
- **Tools:** Tenable.io (Cloud), Nessus Agent
- **Languages/Scripts:** PowerShell

---

## Skills Gained / Focus Areas
- Provisioned and secured a Windows virtual machine
- Deployed Tenable Nessus Agent using PowerShell
- Configured agent groups and triggered scans from the cloud portal
- Observed scan lifecycle and validated agent linking
- Practiced full deprovisioning and asset cleanup in Tenable.io

---

## Environment Setup
 A Windows 10 VM was provisioned with strong credentials to prevent unauthorized access. Nessus Agents were installed using secure PowerShell scripts provided by the Tenable Cloud Portal. Configuration steps were followed to ensure the agent group, scan, and trigger were correctly set up for automated execution.

![Environment Setup](https://github.com/Samuel-Cavada/Agent-Based-Monitoring-Windows/blob/main/images/ABMW1.png)

---

## Walkthrough
1. [Step 1: VM and Agent Group Setup](#step-1-vm-and-agent-group-setup)
2. [Step 2: Install Nessus Agent](#step-2-install-nessus-agent)
3. [Step 3: Create and Trigger Agent Scan](#step-3-create-and-trigger-agent-scan)
4. [Step 4: Monitor and Analyze Results](#step-4-monitor-and-analyze-results)

---

### Step 1: VM and Agent Group Setup
 - Provisioned a Windows 10 VM from the Azure Marketplace. [See full provisioning steps ↗](https://github.com/Samuel-Cavada/Azure-VM-Build) (Ctrl+Click to open in a new tab).
 - Logged into Tenable.io portal at [https://cloud.tenable.com](https://cloud.tenable.com)
   - Created a new Agent Group in Tenable:  
      `Settings → Sensors → Nessus Agents → Agent Groups → + Add Agent Group`

![Step 1](https://github.com/Samuel-Cavada/Agent-Based-Monitoring-Windows/blob/main/images/ABMW5.png)

---

### Step 2: Install Nessus Agent
 - Navigated to:  
  `Settings → Sensors → Nessus Agents → + Add Nessus Agent`
 - Copied the PowerShell install script, edited parameters as needed:

 - Ran the script in PowerShell as administrator inside the VM

![Step 2](https://github.com/Samuel-Cavada/Agent-Based-Monitoring-Windows/blob/main/images/ABMW13.png)
![Step 2](https://github.com/Samuel-Cavada/Agent-Based-Monitoring-Windows/blob/main/images/ABMW18.png)


---

### Step 3: Create and Trigger Agent Scan
`Scans → My Scans → Create Scan → Nessus Agent → Basic Agent Scan`

- **Name**: `Custom Name`
- **Agent Group**: `Your Agent Group Name`
- **Scan Type**  
  - **Triggered Scan**  
    - Select trigger: `Filename`  
    - Enter value: `File name & file type (e.g., Start.txt)`

![Step 3](https://github.com/Samuel-Cavada/Agent-Based-Monitoring-Windows/blob/main/images/ABMW10.png)
![Step 3](https://github.com/Samuel-Cavada/Agent-Based-Monitoring-Windows/blob/main/images/ABMW20.png)


---

### Step 4: Monitor and Analyze Results
- Monitored agent linking under:
  `Settings → Sensors → Nessus Agents`
- Checked the “Scans” tab in Tenable to view scan status and results:  
  `Scans → My Scans → Your Agent Scan Name`

- Waited 30–60 minutes for full vulnerability data to populate

![Step 4](https://github.com/Samuel-Cavada/Agent-Based-Monitoring-Windows/blob/main/images/ABMW23.png)
![Step 4](https://github.com/Samuel-Cavada/Agent-Based-Monitoring-Windows/blob/main/images/ABMW24.png)

---

## Outcomes and Lessons Learned
- **Technical Insight:** Agent-based scanning is ideal for transient or isolated devices; triggers allow for on-demand scanning without continuous cloud connectivity.
- **Configuration Skills:** Learned how to deploy and configure Nessus Agents using PowerShell and Tenable’s cloud interface.
- **Troubleshooting:** Encountered common linking delays and resolved them by validating trigger file placement, group configuration, and credentials.
- **Takeaway:** Proper cleanup (deleting scans, groups, agents, and VMs) is essential to prevent cloud clutter and avoid potential security risks.

---

## References
- [Tenable Nessus Agent Documentation](https://docs.tenable.com/nessus/agent)
- [Tenable Cloud Portal](https://cloud.tenable.com/)
- [PowerShell Script Guide](https://docs.tenable.com/cloud/Content/NessusAgents/Install.htm)
