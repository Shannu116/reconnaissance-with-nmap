

# Task 1: Scan Your Local Network for Open Ports

## Objective
Learn to discover open ports on devices in your local network to understand network exposure.
## Tools
nmap, wireshark
## OS
Kali (attacking),Metasploitable 2 (victim)
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
sudo nmap -sS -sV -sC -O -oX scan_output.xml <TARGET_IP> -v
```

* `-sS` : TCP SYN scan.
* `-oX` : Output in XML (for HTML conversion).
* `-sV` : Probe open ports to determine service/version info.
* `-sC` : used the nmap default scripts for more information gathering

### 4. Converted XML Output to HTML

```bash
xsltproc scan_output.xml -o scan_report.html
```

---

## Scan Summary

You can find the results in the above **HTML file**


## Packet Analysis (Wireshark)

* Verified TCP Half way handshake (SYN, SYN-ACK).
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

