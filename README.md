# Week 3 – Password Cracking with John the Ripper

![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows&logoColor=white)
![Tool](https://img.shields.io/badge/Tool-John%20the%20Ripper-black)
![GUI](https://img.shields.io/badge/GUI-Johnny-6E56CF)
![Status](https://img.shields.io/badge/Status-Educational%20Lab-success)

A hands-on password-auditing lab using **John the Ripper (JTR)** and its graphical front end **Johnny** to recover the password of protected PDFs. Plus another module in this lab covers the same thing using networkwalks tools like hash-calculator and password-cracker.


---

## Table of Contents

1. [Overview](#overview)
2. [Lab Objectives](#lab-objectives)
3. [Lab Environment](#lab-environment)
4. [Tools & Technologies](#tools--technologies)
5. [Repository Structure](#repository-structure)
6. [Practical Workflow](#practical-workflow)
7. [Screenshot Evidence](#screenshot-evidence)
8. [Result](#result)
9. [Learning Outcomes](#learning-outcomes)
10. [Security Insights](#security-insights)
11. [Ethical Considerations](#ethical-considerations)
12. [References](#references)
13. [Author](#author)
14. [Disclaimer](#disclaimer)

---

## Overview

John the Ripper (JTR) is a widely used password-auditing tool for testing password strength, capable of checking many hash types and unlocking password-protected files such as PDF, ZIP, and Office documents. **Johnny** is its graphical companion, giving JTR a point-and-click interface so attacks can be configured without hand-typing commands.

This lab uses both tools together, in a controlled training environment, to recover the password of a protected PDF — and in doing so, demonstrates concretely why weak passwords are a security liability.

## Lab Objectives

- Understand the fundamentals of password auditing.
- Explore John the Ripper's core functionality.
- Learn the Johnny graphical interface as a front end for JTR.
- Understand the difference between a password-protected file and the password hash representation JTR actually attacks.
- Walk through a dictionary-based password-auditing workflow end to end.
- Document the process with real screenshots, in chronological order.

## Lab Environment

| Component | Detail |
|---|---|
| Host OS | Kali Linux |
| Password-Auditing Tool | John the Ripper (JTR) |
| GUI Front End | Johnny |
| Target File | Password-protected PDF (`Multiple PDFs`) |


## Tools & Technologies

| Tool | Purpose |
|---|---|
| [John the Ripper](https://www.openwall.com/john/) | Core password-auditing engine |
| [Johnny](https://openwall.info/wiki/john/johnny) | Graphical interface for John the Ripper |
| Linux | Lab operating system |
| [Online PDF Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) | Extracts the password-hash representation of a protected PDF |
| Dictionary wordlist | Candidate-password list used for the audit attack |


## Practical Workflow

**Step 1 — Download John the Ripper**
Downloaded from the [official Openwall site](https://www.openwall.com/john/) (debian build).

**Step 2 — Download and install Johnny**
Downloaded [Johnny](https://openwall.info/wiki/john/johnny), ran the installer linking the GUI to the JTR engine.

**Step 3 — Prepare the target PDF and extract its hash**
Downloaded the encrypted lab PDF to the Windows PC, then used the [online PDF hash extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) to upload the file and generate its password-hash representation (format `$pdf$...`).

**Step 4 — Save the hash for Johnny**
Copied the extracted hash into Notepad and saved it as `hash1.txt or hash2.txt and so on...`, trimming any stray characters (e.g. a leading `b'`) so the file starts cleanly with `$pdf$`.

**Step 5 — Load the hash and run the audit**
In Johnny, used **Open password file** to load `respective hash file`, then clicked **Start new attack** to begin the dictionary-based password audit.

**Step 6 — Verify the result**
Once JTR/Johnny recovered the password, reopened the original encrypted PDF and entered the recovered password to confirm it worked.

## Screenshot Evidences

Evidences are placed in their respective directories. Just check them out...

## Result

The password for `respective pdf` was successfully recovered via John the Ripper, driven through Johnny's GUI, and verified by reopening the file. The following flags were captured from the recovered PDF content:

```text
nw{networkwalks_flag1_jtr_270521_1}
nw{networkwalks_persistence_jtr_270521}
etc...
```

## Learning Outcomes

- Practical exposure to password auditing using an industry-standard tool.
- Working understanding of John the Ripper's core engine and the Johnny GUI.
- Clear grasp of the role password hashes play in security testing — and that a hash is not simply "scrambled" data you decrypt back to the original.
- Hands-on experience with dictionary-based auditing against a real protected file.
- Reinforced awareness of why weak passwords are a serious security liability.
- Improved technical documentation and evidence-based writeup skills.

## Security Insights

- **Weak passwords fall fast:** dictionary attacks like this one succeed quickly against common, short, or predictable passwords.
- **Length and complexity matter:** longer passwords with mixed character types dramatically increase the search space an attacker has to cover.
- **Reuse compounds risk:** a password cracked once can unlock every other account that reuses it.
- **Hashing vs. encryption:** encryption is reversible with the right key; hashing is a one-way function. Tools like JTR don't "decrypt" a password hash — they hash candidate passwords from a wordlist and check for a match, which is why a strong, unpredictable password resists this kind of audit even when the hash itself is exposed.
- **Defense in depth:** strong password policies plus multi-factor authentication (MFA) meaningfully reduce the real-world impact of a cracked or leaked password.
- **Responsible use:** password auditing is a legitimate security practice only when performed on systems and files you're authorized to test.

## Ethical Considerations

This project was carried out strictly for educational purposes, as part of an authorized NetworkWalks Cybersecurity training exercise in a controlled lab environment.

- Intended for learning password-security concepts and authorized security testing only.
- Not intended to encourage or assist cracking passwords on files, accounts, or systems you do not own or have explicit permission to test.
- Password auditing should always be performed responsibly, with proper authorization.

## References

- John the Ripper (official): [https://www.openwall.com/john/](https://www.openwall.com/john/)
- Johnny (official): [https://openwall.info/wiki/john/johnny](https://openwall.info/wiki/john/johnny)
- NetworkWalks Academy: [https://www.networkwalks.com/](https://www.networkwalks.com/)

## Author

**Abdullah Tariq**
 Cybersecurity Professional


## Disclaimer

This repository documents a training lab exercise completed as part of NetworkWalks Academy's cybersecurity coursework. It is shared for educational and portfolio purposes only and does not constitute professional penetration-testing services or endorse unauthorized password recovery of any kind.
