Passive reconnaissance is one of two sub-types of reconnaissance, the other being active. Before diving in, it’s worth understanding why the distinction matters: active recon without proper authorization is illegal, you can and will face serious legal consequences if you probe systems you don’t own or don’t have written permission to test. Passive recon, on the other hand, relies only on publicly available information and carries no such risk. In this room, we’ll start with passive.

Task — 2 Passive versus Active Recon
So instead of entire theory paragraph, let’s understand it via a small analogy. Suppose you like someone, you find them cute and want to know more about them, where do they hang out, what do they like, what kind of life they have, so you open up their instagram, and scroll through their entire profile. Now this could be any social media platform. You look at what they like, what they post and try to put them all together, and boom you have so much information. This is an example of passive recon.

On the other hand, okay, prepare for ptsd, you go talk to them, you ask them all the details you want to know no matter how nervous or scared you are, no matter how much your voice is cracking or sweaty you are, you ask them, here they specifically know that you are collecting information about them. This is active recon.

By now, the difference should be clear. Passive doesn’t leave a trace about what you are doing or the data you are finding but in case of active recon, the system knows that you are seeking information.

Common passive activities include:

Querying public DNS records from open resolvers (A, MX, TXT, etc.).
Searching certificate transparency logs (e.g., crt.sh) for subdomains and issued certificates.
Reviewing job postings on LinkedIn or company career pages for tech stack hints.
Reading public news, press releases, or leaked documents on paste sites.
Checking exposed devices via search engines like Shodan or Censys.
Scanning public GitHub repositories for hardcoded credentials or configuration files.
Common active activities include:

Sending packets to discover live hosts (e.g., ICMP pings, ARP requests).
Port scanning or service enumeration (Nmap, masscan).
Interacting with web applications or APIs (fuzzing endpoints, directory brute-forcing).
Social engineering attempts (phishing, vishing, pretexting phone calls).
Physical approaches (tailgating, posing as a vendor).
Note that any direct interaction with a person affiliated with the target also counts as active reconnaissance, even when no packets are involved. For example, attending a social event and asking an employee about their company’s technology stack is active reconnaissance because you are directly engaging with the target organisation.

You visit the Facebook page of the target company, hoping to get some of their employee names. What kind of reconnaissance activity is this? (A for active, P for passive)

P

You ping the IP address of the company webserver to check if ICMP traffic is blocked. What kind of reconnaissance activity is this? (A for active, P for passive)

A

You happen to meet the IT administrator of the target company at a party. You try to use social engineering to get more information about their systems and network infrastructure. What kind of reconnaissance activity is this? (A for active, P for passive)

A

Task — 3 Whois
Remember the analogy? This time instead of going on their instagram or talking to them, you thought, hey! why don’t I talk to one of their friends and get some information? It’s a nice idea, you don’t have to go through their entire profile or have to talk to them, and the best part is they don’t even know you asked about them, but the difference is the information you could have found on instagram and by asking them is different.

Let’s consider an example of a company, LinkedOn, you can go through their profiles on the internet and gain details about the organisation and employees, this is passive recon, and if you actually go to your laptop and open your terminal to use tools like ping or nmap, this is active recon. Whois, rather than being a separate type of recon, is a passive recon.

From a WHOIS response, the following details may be available (when not redacted):

Registrar: The company (e.g., Namecheap, GoDaddy) that registered the domain.
Registrant contact information: Name, organisation, address, phone, and email. However, privacy services (standard since GDPR 2018) usually replace this with “Withheld for Privacy” or similar.
Dates: Creation (registration), Updated (last change), and Expiration (renewal deadline).
Name servers: The DNS servers authoritative for the domain.
Status codes: For example, clientTransferProhibited indicates the domain is locked against unauthorised transfers.
Abuse contacts: The registrar’s email and phone for reporting issues.
Services like whoxy.com provide historical WHOIS snapshots. Historical WHOIS data can reveal previous owners, registrar changes, or name server migrations that may indicate past compromises or infrastructure shifts.

Just like an ex moving on and getting replaced, WHOIS got replaced by RDAP. And just like that replacement, RDAP is newer, cleaner, and honestly just better in every way. (Don’t be sad though, everyone goes through it. Well, almost everyone. Some of us are still waiting for our first relationship, let alone a replacement.)

Why is RDAP (Registration Data Access Protocol) better?

RDAP uses HTTPS (secure), returns structured JSON (machine-readable and consistent), supports internationalisation, provides better privacy controls (differentiated access), and aligns with current data protection rules. While legacy whois clients still work (often via failover or older servers), RDAP is now the authoritative standard. Many tools and browsers redirect to RDAP automatically, and command-line access is straightforward with curl or dedicated clients like OpenRDAP.

Open the attackbox on tryhackme, which is a browser based virtual machine. Let’s use whois and find information about tryhackme.com.

Press enter or click to view image in full size

The original result was longer, but I just pasted a small screenshot.

Use curl to query a public RDAP endpoint (e.g., Verisign for .com domains). The jq utility formats the JSON output for readability; it is pre-installed on the AttackBox. If you are using your own system, install it via your package manager (e.g., sudo apt install jq).

Press enter or click to view image in full size

We can see the rdap result is way cleaner and easier to read.

What to look for:

Redirection chain (Verisign to registrar server).
Dates: useful for estimating company age or identifying renewal phishing windows.
Name servers: potential new targets (if in scope).
Status: locked domains (e.g., clientTransferProhibited) are harder to hijack.
Online alternatives (if the whois command behaves unexpectedly):

https://whois.icann.org/ (legacy WHOIS)
https://lookup.icann.org/ (modern RDAP-focused lookup)
https://www.whoxy.com/ (historical WHOIS snapshots, free limited use)
When was TryHackMe.com registered?

20180705

What is the registrar of TryHackMe.com?

namecheap.com

Which company is TryHackMe.com using for name servers?

cloudflare.com

Task — 4 nslookup and dig
Now instead of asking anyone or going throught their social media, you look at a public phonebook and find details like their address, where they work, who delivers their mail. Another classic example of passive recon.

Write on Medium
But before we get into the tools let’s first understand what is DNS (domain name system).

DNS (Domain Name System) is the internet’s phone book that translates human-readable website names into numeric IP addresses.

Suppose you want to open chatgpt on a browser to find answers for your college assignment because you are too lazy to open a book and actually study (I won’t judge, I do the same thing), and imagine instead of writing chatgpt.com you had to type it’s IPaddress. You now have to make a proper note of the IP addresses and enumerate through them everytime you want to go to a certain site. Isn’t that exhausting? To help with this problem, DNS was introduced. It converts name of the website like chatgpt.com and translates it into IP address, that machines actually understand.

We now have two tools introduced in the room: nslookup and dig, personally I tend to use nslookup rather than dig. It’s just a preference and you can use whichever you are comfortable with.

nslookup

Syntax:

nslookup DOMAIN_NAME performs a simple lookup using your default resolver.
nslookup -type=TYPE DOMAIN_NAME [SERVER] specifies a record type and an optional DNS server.
Press enter or click to view image in full size


dig

dig is the modern, preferred DNS query tool.

Syntax: dig [@SERVER] DOMAIN_NAME [TYPE]

Check the TXT records of thmlabs.com. What is the flag there?


THM{a5b83929888ed36acb0272971e438d78}

Task — 5 DNSDumpster
Before learning anything about DNSDumpter, let’s begin with discussing what subdomain is. In extreme layman’s term, subdomain is sub part of a domain, so, something like blog.linkedon.com is a subdomain whereas linkedon.com/blog is a subdirectory and linkedon.com is the domain

dig or nslookup will only give you results of domains unless you go specifically search for sub-domains. Now instead of one target, you have more than 10, first you will have to find the subdomains that exist using tools like gobuster or ffuf and then check DNS result for each individually. Wouldn’t it be easier if there was a way we could do this with just typing the name of a domain and it gives you all the details? The solution to this problem: DNSDumpster.

Subdomains matter because they often expose forgotten or vulnerable services (outdated CMS installations, development panels), shadow IT or misconfigured applications, and additional attack surface such as exposed APIs or admin portals.

DNSDumpster aggregates public DNS data from sources such as search engine caches, zone transfer databases, and certificate records. It does not perform brute-force enumeration, which means it remains fully passive. The results include subdomains and hosts, resolved IPs with geolocation, MX, TXT, and CNAME records, and visual maps showing the relationships between these.

Press enter or click to view image in full size

Certificate Transparency (CT) Logs
The most effective passive subdomain discovery method today is Certificate Transparency logs, accessible through crt.sh(opens in new tab).

Certificate Transparency is a public logging framework (mandatory since approximately 2015) that records every SSL/TLS certificate issued by participating Certificate Authorities. Each certificate contains a Subject Alternative Name (SAN) field listing the domains and subdomains it covers. By searching these logs, you can discover subdomains without sending any traffic to the target.

Lookup tryhackme.com on DNSDumpster. Under Services / Banners, which one has the highest count?

Press enter or click to view image in full size

Cloudflare

Task — 6 Shodan.io
Shodan is a search engine for internet-connected devices. It continuously scans the public internet, collects banners and responses from open ports and services, and indexes them for search. Unlike Google, which indexes web pages, Shodan focuses on devices: servers, IoT equipment, cameras, routers, industrial control systems, and more.

Navigating the Shodan Interface
To begin, navigate to https://www.shodan.io. No account is required for basic searches. Enter a domain name (e.g., tryhackme.com) or an IP address from your earlier DNS lookups (e.g., 104.26.10.229) into the search bar.

The results page displays a list of matching hosts. Selecting a host opens a detailed view containing the following information:

IP address and ASN (Autonomous System Number): identifies the network block.
Hosting provider/organisation (e.g., Cloudflare, AWS): reveals the infrastructure behind the domain.
Geographic location (country, city): approximate physical location of the server.
Open ports and services: with version strings and banners (e.g., HTTP server type and version).
Tags: such as cdn or vuln if a known vulnerability matches the detected service version.
Search Tips
Shodan supports a range of search filters for narrowing results:

hostname:tryhackme.com matches a specific hostname.
org:"TryHackMe" filters by organisation name.
port:443 country:US filters by port and country.
http.component:"wordpress" identifies technology stack (if exposed).
According to Shodan.io, what is the first country in the world in terms of the number of publicly accessible Apache servers?


United States

Based on Shodan.io, what is the 3rd most common port used for Apache?

8080

Based on Shodan.io, what is the most common port used for nginx?

80

Hope this writeup helped you understand passive reconnaissance the way I understand it — through analogies and bad memories of talking to crushes. If something didn’t click, read it again, and if it still doesn’t, the THM room itself is right there.

Thank you for reading!
