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


## Module: Attackers

### Organized Crime

A group of professional cyber criminals who use the internet for unlawful activities, including corporate espionage. 

### State Affiliated

An inidividual or group associated with a global government that attacks to disrupt or compromise governments, organizations, or individuals.

### Evil SysAdmin

If a Sysadmin decides to go rogue.

### Hacktivists

An inidividual or loosely organized group whose activity is aimed at promoting a social or political cause.

### Insiders

Employees, Contractors, or partners that carry out criminal activity using legitimate access. Although they are not necessarily system admins, could be anyone.


### White, Gray, Black Hat Hackers

- White Hat : has skills and they use it to help organizations. Like Security consultants.
- Black Hat : has skills to break into systems, use it for illegal activity.
- Gray Hat :  has skills to break into systems, and use it for legal and illegal stuff. Hard to identify these people.


### Depths of Internet

- Surface Net : Usual internet we all use.
- Deep Net : Internet that's not(can't be) indexed by a search engine.
- Dark Net : Special browser like TOR allow you to access different internet where illegal data from breaches, goods or services are sold/auctioned.


### APT - Advanced persistent attack

Cyberattack executed by criminals, or nation-states with the intent to steal data or surveil systems over an extended period of time, with specific goal and target and which has spent time and resources to identify which vulnerabilities they can exploit, to gain access and design an attack that will likely remain undetected for a long time.

- Funded by global government
- Target specific industry or econonomical sectors
- Utilize public and non-public malware families(writing their own malware)
- Specific attack vectors/patterns they could follow, help us identify them



## Module: Data Breaches

An event where confidential data has been accessed, viewed, stolen by an unauthorized individual. 

Impacts: 
- Data Loss
- Breach Cleanup/Recovery cost
- Revenue impact
- Reputational damage


Common Path:

Research the target ---> Attack ---> Exfiltration

### How to prevent breaches

- Patch software with updates in timely manner
- External web application testing is a must for all public facing applications
- Own your failures as quickly as possible and fix it
- Unprotected data collections should never be attached to a public server



## Module: Security Business Case

Shift Left: Security is built into the process and desgined into the application at an earlier stage of the development lifcycle.

Shift Right: Is obtaining visibility into how applications and APIs are attacked and abused in production.

Start left and start right = secure development lifecycle - what's old is new again.

Cost to fix a bug earlier is lower. After release it could be upto 30x more than what it was when you are still gathering requirements.


Excuses for 'security' and the 'proper' response: 

- I don't have resources, response: you will need more resources when a vulnerability is found after release.
- Need to ship product, response: you need to ship a secure product
- Competitive pressure, other companies coming to market before us, response: You should release secure product and differentiate yourself over your competition using that fact.
- Agile/WaterFall/DevOps does not support security, response: 


## Module: Security Myths

- Myth1: Security is someone else's problem.

  Fact: It is actually everyone's responsibility.

- Myth2: Nobody would want to attack us.

  Fact: Every computer can be attacked, try plugging a computer into public internet, disable firewall and see for yourself. There are automated port scanners that are constantly looking to leverage open unprotected ports.

- Myth3: Security is expensive.

  Fact: Losing customer data is too much more expensive.

- Myth4: No one will ever do that, or think of that method to attack us.

  Fact: Attackers will always to something you did not expect. Expect the unexpected. Build layers of security.

- Myth5: Only critical apps require security.
  
  Fact: All applications need security. Attackers are gonna look at non-critical apps(weak links) to gain access.

- Myth6: Compliance==Security

  Fact: Compliance != Security. Compliance can't be always adequate to protect against all attacks.

- Myth7: Single incident does little damage.

  Fact: Every incident can cause huge damage. More so if it involves customer data.

- Myth8: The firewall will protect us.

  Fact: The app must have its own security built in. Firewall can only prevent traffic from certain sources. But attackers can use authorized source to find different weakness in your app to attack it. Example would be SQLInjection, Cross-site request forgery, etc.

- Myth9: We have TLS; therefore we are secure.

  Fact: TLS protects confidentiality/integrity only for traffic being transported across the wire.

- Myth10: We have security through obscurity.

  Fact: Attackers can easily find hidden things too. That's their thing.

- Myth11: Security is solved with tools.
  
  Fact: Tools are fine but not the total answer. 

- Myth12: Penetration testing or scanning solves all security woes.

  Fact: Testing is necessary, but you cannot hack yourself secure.



## Module: Threat Landscape


**IoT devices**: Home Automation, Automobiles, Smart Meters, Insulin Pumps(or other medical devices). These devices add to the threat landsape in the current era.
  - Lack of updatability, as some IoT devices don't have update mechanism, so in case of a vulnerability you only can buy a newer product to replace existing one.
  - Some companies lack of security, like cameras etc.


**Cloud**: Ownership of data, responsibility for securing the data, multi-tenancy, insecure storage buckets.
  - Data breach
  - System vulnerabilities of underlying hardware of cloud providers
  - Multi-tenancy

**Mobile**: Threats extend to the user population, a less savvy group then corporate. Massive number of devices.
  - Phishing
  - BYOD - Bring your own Device employers
  - Corrupt App Stores


### Newer internet security: 

**Crypto Jacking**: There are attackers that try to break into other computers trying to find crypto currency.

**Supply-chain attacks**: Trying to modify libraries and push those as updates and users suddenly end up with vulnerable version of the code.

**Hardware attacks**: Hardware is now being targeted as new way of attack, like finding CPU vulnerabilities e.g. Meltdown, Spectre.


### Other weaknesses:

- Weak or poorly implemented cryptography/encryption
- Unencrypted data at rest on harddrives.
- Weak authentication:
  - No enforcement of password or strength
  - Failure to enforce acount lock outs
  - Lack of encryption in transit to protect auth data
  - Weak password hash storage


### Other threats:

- Data breach:
  - Accidental disclosure, like sending wrong file to wrong person or other accidents.
  - Improper access control to the systems
  - Web application attacks

- APIs: 
  - Open in a controlled manner, standardize access methods, protect against scraping
  - Lack of security features
  - API's have access to everything

- Denial of service:
  - Single packet, in which attacker finds out vulnerability in application that makes application go in non-responsive state when a certain kind of data packet is sent.
  - Volumetric Attack, in which attacker sends loads and loads of data to make application so busy with useless traffic that it stops serving genuine customers.


### Defenders Dilemma

- Attackers have to only find one vulnerability
- Defenders have to Secure any potential attack/



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
