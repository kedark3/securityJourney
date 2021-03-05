# White Belt
## This is the notes for basic security principles.

### Security is a Journey, not a destination!!

## Module: Introduction to Security
### Define Security
- Defn: Freedom or resilience from potential harm caused by others
- Attacker: anyone who can act as an adversary
- Three Tiers of Security
    People, Process and Tools

    People: build the apps
    
    Process: Standardize how we apply security while building apps
    
    Tools: Help us to find and fix problems

### Visualize how app security is implemented

Application Security : what measures are we gonna take to find, fix and prevent problems

Software Security : Engineering software so that it continues to function correctly under malicious attack

Threats: Possible danger that might breach security and cause harm

Risk: Possibility of a negative or undesirable occurrence, threats are everywhere, but risk is subjective, if you have poor security then you have risk, if you have top grade security then you potentially don’t have a risk or have a very little risk

Attack Surface: Interface an attacker can use to attempt to compromise a product or system. For example in a house, an attacker can use doors, windows or potentially put a hole in the roof. Those are all the surfaces of attack.

### Builders, Breakers and defenders

    Builder: Developer that’s building something. You should use right tools to make sure what you build is secure

    Breaker: like Penetration testers

    Defender: Prevent bad actors from being able to get into your system

**Remember: everyone has a responsibility to ensure security**


## Module: Core Security Concepts

Defining these adequately helps in communicating effectively throughout the organization. Without standardization, the terms could be used interchangeably, or incorrectly, causing inadequate understanding of the security concepts.

### The CIA Triad
Confidentiality : Information is protected from unauthorized disclosure
Integrity : Being able to see if the information has been modified
Availability : Reliable access to information when needed

### A Weakness
Quality or feature that prevents something from being secure

### Vulnerability, Exploit, Attack

Vulnerability: Weakness that is subject to exploitation or misuse. These are everywhere.

Exploit: Program that allows attackers to automatically break into a system

Attack: An attempt to gain unauthorized access

### Mitigation
Steps you take to eliminate or diminish a threat or risk. Proactively mitigate threats or vulnerability

### Exposure
Period of time when a Vulnerability can be Exploited. Like in a bank, the exposure is the period when the vault is opened for employees and customers to access, it is exposed, it has a higher risk of being exploited. 


### Framework

__Identify__ any issues

__Protect your__ vulnerabilities

__Detect__ any attacks

__Respond__ to attacks quickly and

__Recover__ the systems


### Red, Purple and Blue Team

Red: Technical penetration testers, actively trying to attack network ethically within the own org

Purple: When the Red/Blue teams come together to improve security

Blue: Everyday protecting env, reading alarms, triaging false alarms, keep eye on things

### Zero day exploit

Repeatable exploit, is an unknown exploit, as no one in the world has seen it and only the attacker knows and keeps using it, and we don’t know how long it has been open and being used in attacks.

### Backdoor

Accessing computer that bypasses the security mechanism. It’s usually hidden and created to gain access for debugging purposes, but attackers will likely find out about it.


### Access Control and Authentication


Access Control: Means of restricting access to files, referenced functions, URLs and data, based on the identity of users and groups to which they belong.

Atuhentication: Verification of the claimed identity of an application user

## Module: Attacks

### Why do you care? 

Attacks are inevitable. You should always be prepared.

### Anatomy of an Attack

Define target and objective

Research target

Initial Intrusion like phising/zero-day attacks

Persistence: maintaining access to the system

Lateral Movement: gain access to more systems

Data Gathering

Exfiltrate: how to take the data from inside and copy it out or publish it.

Cover the tracks: Delete traces of ever being on the systems you attacked.


### 4 types of attacks


**Buffer Overflow**:  In a software, you have piece of memory holding the data. Attacker sends too much data to flood the memory to cause overflow. And then exploit that. There's more to it, but this is in a simplest definition. Attacker is trying to get the privileged access on the target system.

    * Local Buffer Overflow: Only accessible with access to the local product/server.
    * Remote Buffer Overflow: Accessible from outside of targets' local network, code is sent to the product/site from an outside source and that code is run on the product/site.

**Web-based application attacks**: SQL Injection, Cross-site Scripting(CSS), Cross-site Request Forgery(CSRF)

**Denial-of-Service(DoS)**: Single Packet, or Distributed Denial of Service(DDoS)

**Social Engineering**: Try to learn from engineers to get competitive advantage. Steps: Info gathering about the target, Establish Rapport, Exploitation, Execution.


### Impacts Successful Attacks

- Product/system/application compromised
- Data Breach
- Malware/Ransomware infections

## Module: Privacy vs Security and Customer Data Protection

### Security vs Privacy:

Security: Protecting the data

Privacy : Secure the Identity of the customers if you collect Personally Identifiable Information(pii)

### 3 States of Data:

Make sure all data is encrypted.

In-use : Actively utilizing or ready in memory for you to utilize.

In-Transit: Being moved from one system to another, datacenter->cloud or otherwise.

At-Rest: Backup/databases.

### Customer Data:

This can be found in Databases, Cloud, Log Files or Backups.

### Privacy Legislation:

2 Regulations:

GDPR:

    Right to Correct incorrect Data

    Require explicit consent

CCPA:

    Requires a privacy notice on site

Common between GDPR and CCPA:

    Right to access

    Right to delete

    Right to opt-out

COPPA:

    Protection for kids under 13

    Protect kids’ information

    Gain parental consent

HIPPA:
    
    Protect personal health information(PHI)


Protecting privacy and customer data

**Minimize use** : Don’t ask for data if you don’t need to use or store it

**Conduct privacy assessments**: Audit periodically if you need all the data you ask for, if you don’t, then stop asking for it

**Use tokenization**

**De-identify data**: like remove names or PII from the data

**Anonymize it**


## Module: Dealing with Vulnerabilities

Value of a Response process

Why researchers hunt for vulnerabilities

PSIRT Process and reasons for its success
