# eJPT Lab – Metasploit Pivoting & Internal Enumeration

## 📖 Overview
This project documents my approach to an **eJPT (eLearnSecurity Junior Penetration Tester) lab**, where the goal was to exploit a vulnerable target and enumerate services on a second internal machine.  

While the initial exploit was straightforward, the real learning came from **pivoting, custom scanning, and adapting tools** to simulate a real-world penetration test.

---

## 🎯 Lab Objectives
- Exploit the vulnerable target `demo1.ine.local`
- Enumerate services on an internal host within the same network
- Practice **pivoting**, **binary uploads**, and **custom scripting** for scanning

---

## 🛠️ Tools & Techniques
- **Metasploit Framework**
  - `exploit/unix/webapp/xoda_file_upload` (XODA file upload exploit)
  - `autoroute` for pivoting
  - `auxiliary/scanner/portscan/tcp` for internal scanning
- **Nmap (static binary)** – uploaded via Meterpreter
- **Custom Bash Port Scanner** – simple TCP connect script
- **Meterpreter Commands**
  - `upload` to transfer binaries
  - `chmod +x` to set executables

---

## 🔑 Steps Taken
1. **Initial Enumeration**
   - Ran Nmap on DNS, discovered HTTP on port 80
   - Identified the application running **XODA**

2. **Exploitation**
   - Used Metasploit’s XODA file upload exploit  
   - Gained a **Meterpreter shell**

3. **Pivoting**
   - Discovered internal IP `192.XXX.XXX.2`
   - Guessed next target as `192.XXX.XXX.3`  
   - Set up **autoroute** for pivoting

4. **Scanning**
   - Used Metasploit’s TCP scanner (ports 1–1000)  
   - Uploaded custom tools for more control:  
     - **Static Nmap binary**  
     - **Custom Bash scanner**  

5. **Full Internal Enumeration**
   - Executed `./nmap -p- 192.XXX.XXX.3` on the pivoted target  
   - Enumerated all open ports for further exploitation

---

## 💡 Key Takeaways
- Getting the initial shell is **only the beginning**  
- Pivoting teaches you to think **like an attacker inside the network**  
- Writing simple scripts (like a port scanner) reinforces core concepts  
- Labs are about **mindset shifts**: from just “popping shells” to **engineering access**

---

## 📂 Repository Contents
- `lab_walkthrough.md` – step-by-step notes
- `custom_port_scanner.sh` – Bash script used for port scanning
- `recording/` – video recording of the lab session
- `screenshots/` – selected screenshots from the walkthrough

---

## 📜 License
This project is intended **for educational purposes only**.  
You are free to use the scripts and notes under the **MIT License**.  

*(If you want to restrict it from commercial reuse, you could instead use **CC BY-NC 4.0**.)*

---

## ⚠️ Disclaimer
This repository contains penetration testing practices performed in a **controlled lab environment**.  
Do **not** attempt these techniques on systems you do not own or have explicit permission to test.  
