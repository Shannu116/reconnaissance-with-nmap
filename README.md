Here’s a draft `README.md` file for your Task-1 that outlines the steps, analysis, and findings for the Nmap scan and Wireshark packet capture. You can customize the VM IP, ports, and research content after your actual scan.

---

````markdown
# Task 1: Port Scanning and Packet Analysis using Nmap & Wireshark

## Objective
To perform a **TCP SYN scan** on a virtual host using `nmap`, capture and analyze packets using `Wireshark`, identify open ports and running services, understand potential personal security risks, and store the scan results in **HTML format**.

---

## Steps Followed

### 1. Installed Nmap
```bash
sudo apt update
sudo apt install nmap
````

### 2. Started Wireshark for Packet Capture

* Opened Wireshark.
* Selected the active interface (e.g., `eth0`, `ens33`, etc.).
* Started capturing **before** running the scan.

### 3. Performed a TCP SYN Scan

```bash
sudo nmap -sS -Pn -T4 -oX scan_output.xml <TARGET_IP>
```

* `-sS` : TCP SYN scan.
* `-Pn` : Skip host discovery (treat host as online).
* `-T4` : Aggressive timing for faster scanning.
* `-oX` : Output in XML (for HTML conversion).

### 4. Converted XML Output to HTML

```bash
xsltproc scan_output.xml -o scan_report.html
```

---

## Scan Summary

| Port | State | Service      |
| ---- | ----- | ------------ |
| 22   | open  | SSH          |
| 80   | open  | HTTP         |
| 139  | open  | NetBIOS-SSN  |
| 445  | open  | Microsoft-DS |
| 3306 | open  | MySQL        |

*(Replace with your actual results)*

---

## Packet Analysis (Wireshark)

* Verified TCP three-way handshake (SYN, SYN-ACK, ACK).
* Observed destination ports.
* Identified that SYN packets were being sent to a range of ports.
* Confirmed SYN-ACK responses only for open ports.

---

## Service Research & Potential Risks

### 1. **SSH (Port 22)**

* **Purpose:** Remote login.
* **Risk:** Weak passwords, brute force attacks.
* **Mitigation:** Use key-based auth, disable root login, change default port.

### 2. **HTTP (Port 80)**

* **Purpose:** Web server.
* **Risk:** Data sent in plain text, vulnerable to MITM.
* **Mitigation:** Use HTTPS, keep web server updated.

### 3. **NetBIOS/SMB (Ports 139 & 445)**

* **Purpose:** File sharing on Windows.
* **Risk:** EternalBlue exploit, lateral movement.
* **Mitigation:** Disable SMBv1, apply patches, restrict access.

### 4. **MySQL (Port 3306)**

* **Purpose:** Database access.
* **Risk:** Exposed DB, credential theft.
* **Mitigation:** Bind to localhost, use firewalls, strong credentials.

---

## Personal Security Risks of Open Ports

* **Unauthorized Access:** Attackers may exploit weak configurations.
* **Data Leakage:** Open services may expose sensitive info.
* **Attack Surface Expansion:** More ports = more entry points.
* **Botnet Inclusion:** Vulnerable services may be hijacked.

---

## Output Files

* `scan_output.xml` – Nmap XML output.
* `scan_report.html` – Converted HTML report.
* `wireshark_capture.pcapng` – Packet capture for analysis.

---

## Conclusion

This task helped in:

* Understanding port scanning techniques.
* Analyzing network behavior.
* Identifying security weaknesses due to open ports.

> **Reminder:** Always scan systems you own or have explicit permission to assess.

```

Let me know if you'd like a template folder structure or want to automate this with a Bash script too.
```
