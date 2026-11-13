# cybersecurity-reconnaissance-week-2
A hands-on cybersecurity reconnaissance project exploring WHOIS enumeration, DNS analysis, web technology fingerprinting, WAF detection, HTTP header inspection, OSINT, and Nmap host discovery, with documented findings and security observations.

# Week 2 – Cybersecurity Reconnaissance Project

## About This Project

This repository contains my work from Week 2 of my cybersecurity internship with Networkwalks.com.

The task focused on reconnaissance and information gathering. I used different tools to collect information about assigned domains, examine DNS records, identify web technologies, inspect HTTP response headers, and perform host discovery on my own local network.

I have included the tools used, a summary of the activities, observations from the exercises, and supporting evidence where appropriate.

## Tools Used

- WHOIS
- WhatWeb
- WAFW00F
- Nslookup
- cURL
- DNSRecon
- theHarvester
- Nmap

## What I Did

### 1. WHOIS Lookup

I used WHOIS to examine the registration information for `networkwalks.com`.

The information collected included:

- Domain registrar
- Registration and expiry dates
- Domain status codes
- Nameservers
- DNSSEC status

The domain registration information also showed that the registrant's details were protected by a privacy service.

### 2. Web Technology Identification

I used WhatWeb to identify technologies detected on `networkwalks.com`.

The output identified WordPress, Apache, Bootstrap, jQuery, Google Tag Manager, and other web components.

The website also redirected HTTP traffic to HTTPS.

These results provide a basic picture of the technologies used by the website. They do not, by themselves, confirm that any of the identified components are vulnerable.

### 3. WAF Detection

I ran WAFW00F against the assigned website.

The tool identified ModSecurity (SpiderLabs) as the Web Application Firewall.

This exercise helped me understand how WAF detection tools identify possible protective technologies used by websites.

### 4. DNS Enumeration

I used Nslookup and DNSRecon to gather DNS information about the domain.

The records examined included:

- A records
- MX records
- NS records
- SOA records
- TXT records
- SRV records

The DNSRecon output also reported that DNSSEC was not enabled.

I recorded the findings for the report rather than treating every discovered configuration detail as a vulnerability.

### 5. HTTP Header Inspection

I used cURL to inspect the HTTP response headers returned by the website.

Some of the information observed included:

- HTTP response status
- Web server information
- Cookie security attributes
- Referrer-Policy
- Permissions-Policy
- WordPress REST API references
- Caching-related headers

The session cookie observed in the response included Secure and HttpOnly attributes.

### 6. OSINT Using theHarvester

I used theHarvester 4.11.1 against the assigned `microsoft.com` domain.

The tool collected publicly available information from multiple sources, including hostnames, IP addresses, email addresses, ASNs, and URLs.

Some data sources could not be queried successfully because of API-key restrictions or service errors.

This affected the completeness of the results, so the collected information was treated as reconnaissance data rather than verified security findings.

### 7. Nmap Host Discovery

I also performed a host discovery scan on my own local network.

Command used:

nmap -sn 192.168.206.223/24
```

The scan examined 256 IP addresses and identified two active hosts.

The `-sn` option performs host discovery without carrying out a port scan.

## Findings and Observations

A few observations stood out during the exercise:

- The target domain used HostGator nameservers in the DNS information collected.
- The website redirected HTTP requests to HTTPS.
- WhatWeb identified WordPress and several associated technologies.
- WAFW00F detected ModSecurity.
- DNSRecon reported that DNSSEC was unsigned.
- The DNS records included mail-related and SPF information.
- theHarvester returned a large collection of publicly indexed information for the assigned Microsoft domain.
- Nmap identified two active hosts on my local network.

These are observations from the tools used. Further validation would be required before classifying any of them as security vulnerabilities.

## Challenges

Some of the OSINT sources used by theHarvester required API credentials that were unavailable or did not work. As a result, not every source returned information.

Another important part of the exercise was understanding the difference between information exposure, configuration observations, and an actual security vulnerability.

## What I Learned

This exercise gave me practical experience with several reconnaissance tools and helped me understand how they complement one another.

I also learned that collecting information is only one part of the process. The results must be reviewed, checked for accuracy, and documented carefully.

## Project Evidence

Screenshots and sanitized tool outputs are organised in the `evidence` directory.

The full reconnaissance report is included in the `report` directory, subject to approval for public sharing.

## Scope and Disclaimer

The domain reconnaissance activities were performed against assigned project targets. The Nmap host discovery exercise was performed on my own local network.

This repository is for educational and portfolio purposes. It does not contain a claim that the identified targets have confirmed exploitable vulnerabilities.

Sensitive information, credentials, cookies, tokens, and unapproved raw data should not be published.

## Author

Amos Ibrahim

Cybersecurity Intern | SOC Analyst
