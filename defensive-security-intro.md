
Defensive Security Intro write-up | tryhackme
Task 1
Defensive security is the practice of protecting computer systems, networks, and data from cyber threats, attacks, and unauthorized access. Its main goal is to prevent breaches, detect suspicious activity, and respond quickly to minimize damage.
It involves measures like monitoring systems, analyzing logs, managing vulnerabilities, and implementing security controls such as firewalls, intrusion detection systems (IDS), and antivirus software. Defensive security professionals focus on strengthening systems, identifying weaknesses, and ensuring that attacks are stopped or contained before causing harm.
In real-world scenarios, defensive security helps organizations protect sensitive data, maintain user trust, and ensure business continuity by reducing the impact of cyberattacks.
Some of the tasks that are related to defensive security include:
User cyber security awareness: Training users about cyber security helps protect against attacks targeting their systems.
Documenting and managing assets: We need to know the systems and devices we must manage and protect adequately.
Updating and patching systems: Ensuring that computers, servers, and network devices are correctly updated and patched against any known vulnerability (weakness).
Setting up preventative security devices: firewall and intrusion prevention systems (IPS) are critical components of preventative security. Firewalls control what network traffic can go inside and what can leave the system or network. IPS blocks any network traffic that matches present rules and attack signatures.
Setting up logging and monitoring devices: Proper network logging and monitoring are essential for detecting malicious activities and intrusions. If a new unauthorized device appears on our network, we should be able to detect it.

There is much more to defensive security. Aside from the above, we will also cover the following related topics:
Security Operations Center (SOC)
Threat Intelligence
Digital Forensics and Incident Response (DFIR)
Malware Analysis

Task 2
Security Operations Center (SOC)
A Security Operations Center (SOC) is a centralized team or facility responsible for continuously monitoring, detecting, analyzing, and responding to cybersecurity threats in an organization.

---

What does a SOC do? (Key Points)
Monitors network and system activity 24/7
Detects suspicious behavior and potential cyber threats
Analyzes security alerts and logs
Responds to incidents (e.g., malware, breaches, attacks)
Investigates and mitigates security incidents
Performs threat intelligence and risk assessment
Manages security tools like SIEM, IDS/IPS, firewalls
Ensures compliance with security policies and standards

What is Threat Intelligence?
 Threat intelligence is the process of collecting, analyzing, and using information about potential or existing cyber threats to help organizations prevent and respond to attacks.

---

Key Points (What it involves)
Collecting data about cyber threats (hackers, malware, attack methods)
Analyzing patterns and behaviors of attackers
Identifying vulnerabilities and possible risks
Providing actionable insights to improve security
Sharing information across security teams and organizations
Supporting faster detection and response to attacks

---

Types of Threat Intelligence
Strategic - High-level insights for decision-making
Tactical - Information about attack methods and techniques
Operational - Details about specific ongoing threats
Technical - Indicators like IP addresses, domains, malware hashes

Digital Forensics and Incident Response (DFIR)
This section is about Digital Forensics and Incident Response (DFIR), and we will cover:
Digital Forensics
Incident Response
Malware Analysis

Digital Forensics
Forensics is the application of science to investigate crimes and establish facts. With the use and spread of digital systems, such as computers and smartphones, a new branch of forensics was born to investigate related crimes: computer forensics, which later evolved into digital forensics.
In defensive security, the focus of digital forensics shifts to analyzing evidence of an attack and its perpetrators and other areas such as intellectual property theft, cyber espionage, and possession of unauthorized content. Consequently, digital forensics will focus on different areas, such as:
File System: Analyzing a digital forensics image (low-level copy) of a system's storage reveals much information, such as installed programs, created files, partially overwritten files, and deleted files.
System memory: If the attacker runs their malicious program in memory without saving it to the disk, taking a forensic image (low-level copy) of the system memory is the best way to analyze its contents and learn about the attack.
System logs: Each client and server computer maintains different log files about what is happening. Log files provide plenty of information about what happened on a system. Even if the attacker tries to clear their traces, some traces will remain.
Network logs: Logs of the network packets that have traversed a network would help answer more questions about whether an attack is occurring and what it entails.

Incident Response
An incident usually refers to a data breach or cyber attack; however, in some cases, it can be something less critical, such as a misconfiguration, an intrusion attempt, or a policy violation. Examples of a cyber attack include an attacker making our network or systems inaccessible, defacing (changing) the public website, and data breach (stealing company data). How would you respond to a cyber attack? Incident response specifies the methodology that should be followed to handle such a case. The aim is to reduce damage and recover in the shortest time possible. Ideally, you would develop a plan that is ready for incident response.
The four major phases of the incident response process are:
Preparation: This requires a team trained and ready to handle incidents. Ideally, various measures are put in place to prevent incidents from happening in the first place.
Detection and Analysis: The team has the necessary resources to detect any incident; moreover, it is essential to analyze any detected incident further to learn about its severity.
Containment, Eradication, and Recovery: Once an incident is detected, it is crucial to stop it from affecting other systems, eliminate it, and recover the affected systems. For instance, when we notice that a system is infected with a computer virus, we would like to stop (contain) the virus from spreading to other systems, clean (eradicate) the virus, and ensure proper system recovery.
Post-Incident Activity: After a successful recovery, a report is produced, and the lesson learned is shared to prevent similar future incidents.

Malware Analysis
Malware stands for malicious software. Software refers to programs, documents, and files you can save on a disk or send over the network. Malware includes many types, such as:
A virus is a piece of code (part of a program) that attaches itself to a program. It is designed to spread from one computer to another and works by altering, overwriting, and deleting files once it infects a computer. The result ranges from the computer becoming slow to unusable.
Trojan Horse is a program that shows one desirable function but hides a malicious function underneath. For example, a victim might download a video player from a shady website that gives the attacker complete control over their system.
Ransomware is a malicious program that encrypts the user's files. Encryption makes the files unreadable without knowing the encryption password. The attacker offers the user the encryption password if the user is willing to pay a "ransom."

Malware analysis aims to learn about such malicious programs using various means:
Static analysis works by inspecting the malicious program without running it. This usually requires solid knowledge of assembly language (the processor's instruction set, i.e., the computer's fundamental instructions).
Dynamic analysis works by running the malware in a controlled environment and monitoring its activities. It lets you observe how the malware behaves when running.

What would you call a team of cyber security professionals that monitors a network and its systems for malicious events?
Security Operations Center
What does DFIR stand for?
Digital Forensics and Incident Response
Which kind of malware requires the user to pay money to regain access to their files?
ransomware
Task 3
Press on view site.
What I Learned ?
In this module, I learned the fundamentals of defensive security, which focuses on protecting systems, networks, and data from cyber threats. The primary goal is to prevent attacks, detect suspicious activity, and respond quickly to reduce damage.
I understood that defensive security involves multiple practical tasks such as:
Monitoring systems and analyzing logs
Managing and documenting assets
Updating and patching systems
Using security tools like firewalls, IDS/IPS, and antivirus
Implementing logging and continuous monitoring

I also learned about key domains within defensive security:
Security Operations Center (SOC): A team that monitors systems 24/7, detects threats, and responds to incidents.
Threat Intelligence: The process of collecting and analyzing information about cyber threats to improve defense strategies.
Digital Forensics and Incident Response (DFIR): Investigating attacks, collecting evidence, and handling incidents effectively.
Malware Analysis: Studying malicious software like viruses, trojans, and ransomware using static and dynamic analysis.

Additionally, I learned the incident response lifecycle, which includes preparation, detection, containment, recovery, and post-incident analysis.

---

Why This is Important (Real-World Relevance)?
Defensive security is critical because cyber attacks are increasing rapidly, and organizations must protect their systems and data.
It helps prevent data breaches and financial loss
Protects user privacy and sensitive information
Ensures business continuity during attacks
Builds trust with users and customers
Enables quick response and recovery from incidents
Helps identify weaknesses before attackers exploit them

In real life, companies rely on SOC teams and threat intelligence to stay ahead of attackers and reduce risks.