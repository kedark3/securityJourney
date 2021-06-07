# Yellow Belt
<!-- TOC -->

- [Yellow Belt](#yellow-belt)
  - [Module: Six Foundational Truths of Application Security](#module-six-foundational-truths-of-application-security)
  - [Module: Secure Design Principles](#module-secure-design-principles)
    - [Defence in depth](#defence-in-depth)
    - [Minimize attack surface](#minimize-attack-surface)
    - [Security by obscurity](#security-by-obscurity)
    - [Keep security simple](#keep-security-simple)
    - [Make security usable](#make-security-usable)
    - [Fail Securely](#fail-securely)
    - [Run with least privilege](#run-with-least-privilege)
    - [Separation of concern](#separation-of-concern)
    - [Don't trust services and infrastructure](#dont-trust-services-and-infrastructure)
    - [Establish secure defaults](#establish-secure-defaults)
  - [Module: Input Validation](#module-input-validation)
    - [Syntacting and Semantic validations](#syntacting-and-semantic-validations)
    - [Dangerous and safe lists](#dangerous-and-safe-lists)
    - [Client side and server side validation](#client-side-and-server-side-validation)
    - [Ways of input validation](#ways-of-input-validation)
    - [Implementing input validation](#implementing-input-validation)
    - [Tips for input validations](#tips-for-input-validations)
  - [Module: Output Encoding](#module-output-encoding)
    - [Goals:](#goals)
    - [Tips to improve encoding:](#tips-to-improve-encoding)
  - [Module: Authentication Theory](#module-authentication-theory)
    - [Authentication Threats:](#authentication-threats)
    - [Authentication Weaknesses](#authentication-weaknesses)
    - [Authentication Data](#authentication-data)
  - [Module: Access Control and Authorization](#module-access-control-and-authorization)
    - [Authorization threats](#authorization-threats)
    - [Authorization weaknesses](#authorization-weaknesses)
    - [Subjects and Objects](#subjects-and-objects)
    - [Types of Authorization](#types-of-authorization)
    - [Design principles](#design-principles)
  - [Module: Logging and Exception Handling](#module-logging-and-exception-handling)
    - [Threats to logging](#threats-to-logging)
    - [Logging weaknesses](#logging-weaknesses)
    - [Which events to log](#which-events-to-log)
    - [Where should we log](#where-should-we-log)
    - [4 Ws of Logging](#4-ws-of-logging)
    - [Data to exclude from logs](#data-to-exclude-from-logs)
    - [Tips for logging data at rest](#tips-for-logging-data-at-rest)
    - [Tips for Protection of logging data in transit](#tips-for-protection-of-logging-data-in-transit)
    - [Monitoring of Events](#monitoring-of-events)
    - [Security concerns for exceptions](#security-concerns-for-exceptions)
  - [Module: Crytography](#module-crytography)
    - [Key Terms](#key-terms)
    - [Different Ciphers](#different-ciphers)
    - [Rolling your crypto : BAD](#rolling-your-crypto--bad)
  - [Module: Risk Management in AppSec](#module-risk-management-in-appsec)
    - [Process for risk management](#process-for-risk-management)
    - [Risk management principles](#risk-management-principles)
  - [Module: The  Hacker(Problem Solver) Mindset](#module-the--hackerproblem-solver-mindset)
    - [Types of hackers](#types-of-hackers)
    - [Hacker Attitude](#hacker-attitude)
    - [Hacker view](#hacker-view)
    - [Programmer, Developer, Hacker](#programmer-developer-hacker)
    - [Applying hacker mindset](#applying-hacker-mindset)
  - [Module: OWASP Top 10](#module-owasp-top-10)
    - [What is OWASP top 10](#what-is-owasp-top-10)
    - [Injection](#injection)
    - [Broken Authentication](#broken-authentication)
    - [Sensitive Data Exposure](#sensitive-data-exposure)
    - [XML External Entity (XXE)](#xml-external-entity-xxe)
    - [Broken Access Control](#broken-access-control)
    - [Security misconfiguration](#security-misconfiguration)
    - [XSS](#xss)
    - [Insecure Deserialization](#insecure-deserialization)
    - [Using components with known vulnerabilities](#using-components-with-known-vulnerabilities)
    - [Insufficient logging and monitoring](#insufficient-logging-and-monitoring)
  - [Module: Buffer OverFlow and Remote code execution](#module-buffer-overflow-and-remote-code-execution)
    - [**Buffer OverFlow**](#buffer-overflow)
    - [Types of Buffer OverFlow](#types-of-buffer-overflow)
      - [Mitigations](#mitigations)
    - [**Shell code**](#shell-code)
  - [Module: Denial of Service](#module-denial-of-service)
    - [Types of Attacks](#types-of-attacks)
    - [Mitigations:](#mitigations-1)
  - [Module: XSS Cross-Site Scripting](#module-xss-cross-site-scripting)
    - [What is XSS?](#what-is-xss)
    - [Threats](#threats)
    - [What is Stored or persistent XSS?](#what-is-stored-or-persistent-xss)
    - [What is Reflected or non-persistent XSS?](#what-is-reflected-or-non-persistent-xss)
    - [What is DOM based XSS?](#what-is-dom-based-xss)
    - [Mitigations](#mitigations-2)
  - [Module: Injection Attacks](#module-injection-attacks)
    - [Types:](#types)
    - [Threats:](#threats-1)
    - [Mitigation:](#mitigation)
  - [Module: CSRF - Cross Site request foregery](#module-csrf---cross-site-request-foregery)
    - [What is CSRF?](#what-is-csrf)
    - [What is a Synchronizer token (CSRF Token)?](#what-is-a-synchronizer-token-csrf-token)
    - [What is SameSite cookies?](#what-is-samesite-cookies)
    - [CSRF Risks](#csrf-risks)
    - [CSRF Mitigations](#csrf-mitigations)
  - [Module: Insecure Communications](#module-insecure-communications)
    - [Mitigations:](#mitigations-3)
    - [Ciphers choices](#ciphers-choices)
  - [Module: Social Engineering](#module-social-engineering)
    - [Social Engineering Process](#social-engineering-process)
  - [Module: AppSec in an Agile World](#module-appsec-in-an-agile-world)
    - [Agile Terms:](#agile-terms)
    - [Highlight from Agile Manifesto](#highlight-from-agile-manifesto)
    - [Agile principles impacting security](#agile-principles-impacting-security)
    - [Sprint with Security](#sprint-with-security)
    - [Definition of Done](#definition-of-done)
    - [Security focused agile sprint](#security-focused-agile-sprint)
  - [Module: AppSec in DevOps World](#module-appsec-in-devops-world)
    - [DevSecOps](#devsecops)
  - [Module: Security behaviors for DevOps](#module-security-behaviors-for-devops)
    - [Security Behaviors and Habits](#security-behaviors-and-habits)
  - [Module: Writing Security Requirements](#module-writing-security-requirements)
    - [Uses:](#uses)
    - [The positive impact of security requirements](#the-positive-impact-of-security-requirements)
    - [Sources for Security Requirements](#sources-for-security-requirements)
    - [Three Phases of security requirements](#three-phases-of-security-requirements)
  - [Module: Threat Modeling Basics](#module-threat-modeling-basics)
    - [Benefits:](#benefits)
    - [Security Feedback loop](#security-feedback-loop)
    - [Threat Modeling in the SDL](#threat-modeling-in-the-sdl)
    - [Threat Modeling Process](#threat-modeling-process)
    - [A "good" Threat Model](#a-good-threat-model)
    - [Threat Modeling Tools](#threat-modeling-tools)
    - [4 questions for threat modeling](#4-questions-for-threat-modeling)
    - [Threat Prioritization](#threat-prioritization)
    - [Threat Modeling Examples](#threat-modeling-examples)
  - [Module: Static Application Security Testing(SAST)](#module-static-application-security-testingsast)
    - [Benefits](#benefits-1)
    - [SAST Traits](#sast-traits)
    - [SAST Use Cases](#sast-use-cases)
    - [Developer Workflow](#developer-workflow)
  - [Module: Dynamic Application Security Testing (DAST)](#module-dynamic-application-security-testing-dast)
    - [Benefits:](#benefits-2)
    - [Traits](#traits)
    - [Classes of Fuzz finding](#classes-of-fuzz-finding)
  - [Module: Next Gen AppSec Tools](#module-next-gen-appsec-tools)
  - [Module: Vulnerability Scanning](#module-vulnerability-scanning)
    - [Benefits](#benefits-3)
    - [Traits](#traits-1)
    - [Process of Vuln Scanning](#process-of-vuln-scanning)
    - [How does it work?](#how-does-it-work)
    - [Developer workflow](#developer-workflow-1)
  - [Module: Penetration Testing and Bug Bounty](#module-penetration-testing-and-bug-bounty)
    - [Benefits](#benefits-4)
    - [Pen Testing Process](#pen-testing-process)
    - [How to choose a pen testing company](#how-to-choose-a-pen-testing-company)
    - [Bug bounty process](#bug-bounty-process)
  - [Module: Secure Code Review](#module-secure-code-review)
    - [Purpose](#purpose)
    - [Process of secure code review](#process-of-secure-code-review)
    - [Web Security Code Review Checklist](#web-security-code-review-checklist)

<!-- /TOC -->

## Module: Six Foundational Truths of Application Security

1. Do not trust user input EVER
2. Shift left and start left - build security in the beginning, from the requirements phase
3. Default and hardcoded credentials are your enemy, force password changes on the first boot, and use a secure credetial store
4. Responsibility for third-part software belongs to YOU, own, review the code and define schedule to review and update all 3rd party software, make sure to stick to it.
5. Threat modeling reduces logical flaws - if you know the threats then you can develop application with those in mind.
6. Greatest tool is knowledge, teach engineers about application security and provide the tools to optimize.


## Module: Secure Design Principles

**Defn:** Industry best practice for building security in regardless of the platform or language.

Knowing these principles enables you and encourages you to secure design, yields is less vuln(vulnerabilities).

### Defence in depth

A security strategy establishing multiple layers and variable barriers across between layers in an architecture.

Example:

- Network layer: Firewall, Web App Firewall
- Runtime layer: Runtime Application Soft Protection
- Application layer:  E.g. in Docker/Podman, a Hardened container
- Build layer: Dependency checking
- Response layer: PSIRT

### Minimize attack surface

Limiting the interfaces available that an attacker could use to attempt to compromise.

E.g. on a linux server hosting your web applications, only run httpd, and not things like telnetd, ntpd, sendmail, snmpd, smbd. Having such additional things running provides attacker with more ways to attack.

### Security by obscurity

The reliance on the secrecy of the desing or implementation as the main method of providing security for a system, application or algorithm.

E.g. Moving SSH daemon from 22 to 24, its obscure but it can be still discovered by an attacker.

This is not the best way to try securing your apps.


### Keep security simple

Making design choice to simplify and eliminate complexity from security features. More complex it is, more difficult to review design, code etc.

- If your design is too complex, look for opportunities to break complex concepts or modules into smaller, more single purpose modules.

- Reuse vetted modules within your larger project. 

- Distribute vetted modiules for use across entire org.

- Simple security in an architecture is easily verifieable because of a lack of complexity.

### Make security usable

The application of hurman factors and user-centered design techniques to generate effective security.

E.g. Telling a normal user about insecure certificate authority.

### Fail Securely

If there is a failure, system should fail securely. 

E.g. If you request some kind of access and system fails, you should be denied the access, and not granted.

### Run with least privilege

Granting your users or applications only those accesses they need to perform their official duties.

E.g. Using root user vs non-privileged user in MySQL to grant access to your database to the web application.

### Separation of concern

Separate duties across multiple admin's and do not have a single admin with all the power.

### Don't trust services and infrastructure

Don't trust blindly in cloud and infra services. Always trust but verify.

E.g. One app can have bad security and if your app trusts input coming from that app, you are essentially opening yourself to a potential threat.

### Establish secure defaults

Make application or products secure by default.

E.g. Force changing default password or by default put a difficult password as default so user feels the need to change it and these passwords will be unique per installation. Like some companies have different admin passwords for each unit sold.


## Module: Input Validation

*Defn: Check input data to make sure it is safe for processing.*

We use this to drop/eliminate bad data.

Goal1: Ensure only properly formed data is entering an application.

Goal2: Prevent malformed data from persisting in a storage vehicle.

### Syntacting and Semantic validations
- Syntacting: recognizing bad data by format like if date is inputed as `a/b/wxyz` that's not valid.
- Semantic: If start date is after end date, that's bad semantic data. So validate data in the context of the application.

### Dangerous and safe lists

- Dangerous: "bad" inputs are included on a list and used to validate user input against it to check if the input is bad input.

- Safe list: "Good" inputs are included on a list and any input not found on the list is deemed not authorized. This approach is preffered, as we know what is good, but it is harder to predict what all should be considered bad as attackers are always looking for new ways to attack.

### Client side and server side validation

- Client side: Performed in the user's browser. User could turn off input validation. It is fine to use sometimes to increase performance.
- Server side: Performed inside the application or framework on the server. We have full control. User can't turn it off.


### Ways of input validation

1. Regular expressions and input validation
   1. Can be complicated to create and maintain
   2. When done correctly, lock in the exact data the application can receive
   3. Define the allowed set of chararcters to be accepted
   4. Define minimum and maximum length of data.
2. Frameworks
   1. Why:
      1. Use vetted libraries for input validation
      2. Don't reinvent the wheel
   2. E.g.
      1. Django - RegexValidator, EmailValidator, URLValidator
      2. Express Node.js/Javascrip - Express-validator
      3. Ruby on Rails - Active Record Validations


### Implementing input validation
- Invoke minimum and maximum value range checks for numerical parameters and dates; min and max len check for strings
- Utilize data type validation
- Perform schema validation against JSON and XML
- Execute type conversion(e.g. Integer.parseInt() for java or int() in python) with strict execption handling
- Employ an array of allowed values for small sets of string parameters(e.g. days of week)
- Use regular expressions for any other structured data

### Tips for input validations
- Assume all input is malicious until proven usable
- Use a framework that provides proper input validation
- Perform Attack surface reduction
- Duplicate any client-side input validation on the server-side
- Use static analysis tools to discover input validation errors


## Module: Output Encoding

**Encoding**: Translating special characters into some equivalent form that is no longer dangerous in the target interpreter.

- Encoding is a safety issue. The safety of your application's users is at stake. Improper encoding or escaping allows an attacker to change the commands that are sent to another component, inserting malicious commands instead.
  
- E.g. input: `<script>alert(document.cookie);</script> ` to output: `&lt;script&gt;alert(document.cookie);&lt;/script&gt;`

**Escaping**: Adding a special char before the char/string to avoid it being misinterpreted.


**Contextual Encoding**: Enforcing output encoding at every level of a user interface and encoding at the last moment before untrusted data is dynamically added to HTML.


### Goals:
- Goal1: Prevention of XSS stle attacks
- Goal2: Prevention of injection attacks such as command, XML, and LDAP.


### Tips to improve encoding:

1. Use a vetted library or framework that does not allow improper output encoding to occur.
2. Understand the context in which your data will be used and the expected encoding.
3. Use input validation as a defense-in-depth measure to reduce likelihood of output encoding errors.
4. When exchanging data, ensure that both components use the same character encoding.





## Module: Authentication Theory


Authentication is basic security feature of all application. If authentication is flawed, the door into your application is open. It is a process verifying the identity of a user, process or device before allowing access to resources in an information system.

Digital Identity is unique set of attributes describing a person. e.g. Username, Password, purchasing, DoB, SSN, Search Activity.


### Authentication Threats:
- Online Guessing : Try to guess password if the username is leaked.
- Offline Cracking : Download password hashes from a databreach and try to crack it.
- Click jacking : wrapping one site around another in order to make user enter their auth info such that you can capture it.
- Social Engineering: Try to call you on phone or email to gather info that can help them crack your login info.
- Theft : Acquiring your login creds using some form of theft.
- Duplication
- Phishing or Pharming : making fake site and redirecting user there
- Eavesdropping : looking over someone's shoulder in the physical env.
- Replay : Capture auth and replay it to gain access.
- Session Hijack : somehow get access to your session.
- Man-in-the-middle : attacker sitting between client and server and sniff the login creds.


### Authentication Weaknesses

1. Authentication bypass: Accidentally allow go around authentication.
2. Reflection attack: Challenge attack where server asks challenge, attacker tries to fool server into answering the own challenge.
3. Missing authentication for critical function, so some pages/parts on your appliation might be missing auth.
4. Use of client side authentication: If app does client side auth and client manages to shut it off, then client can access app with no auth.
5. Use of password instead of password hashes: In case of a data breach attacker gets hands on plain text password then.



### Authentication Data

1. Memorized Secret: Commonly referred to as a password, or PIN that is chosen and then memorized by the user.
2. One time password: valid only one time for one session
3. Recovery Keys: Secret stored by the user and sysstem for use in the event of a lost password or malfunction.
4. Biometric scanners
5. Cryptographic key: binary string used as a secret parameter by a cryptographic algorithm
6. Factors of Authentication: 1, 2 or multi factor, Something you know(username/password), Something you have(phone, smart card, computer) and something you are(facial scan, retinal or iris scan, fingerpring or palm scan, voice scan). 



## Module: Access Control and Authorization


- Authorization is act of granting access privileges to a user, program or process. This needs to be present in each system, program, application etc.


- Access control is process of granting or denying a request.

### Authorization threats

1. Elevation of privileges : Imagine an attacker gets higher like systems, admin, or root privileges.
2. Disclosure of Confidential data : Someone able to access something they shouldn't be able to see it.
3. Data tampering : Be able to modify data when they should not be
4. Token stealing : Token issued in the auth that get stolen.


### Authorization weaknesses

1. Improper authorization : Authorization check hasn't even been implemented
2. Incorrect authorization : Authorization attempted but didn't work properly
3. Authorization bypass : User able to get access without having to authorize.
4. Improper access control: RBAC is improperly configured


### Subjects and Objects 

Subject is an individual, process or devicecausing information to flow among objects or changes to the system state.

Object is a passive entity that contains or receives information.


### Types of Authorization

1. DAC(Discretionary access control) : 
   1. Define users and permissions for various users to files.
   2. E.g. is filesystem access controls(permissions)

2. MAC(Mandatory access control)
   1. Used in Military grade security systems previously but now making it to more common user systems
   2. Can't read anything above your access level, can't write anything below your access level. E.g. if you are Unclassified, you can't read confidential, secret or top secret, and if you are at top secret level, can't write anything to secret, confidential or unclassified docs(as you can mistakenly leak something that should be top secret)

3. RBAC(Role-based access control): Access is determined by roles, you define roles and then add users to those roles. 

4. ABAC(Attribute based access control) : Take various pieces of data about users and decideif they should be granted access based on complete set of attributes. E.g. *Permit managers* from *HR Dept* in *Boston* to access the *performance reports* during *normal business hours*. This is newer method.


### Design principles

1. Build it thoroughly up front
2. Force all request to go through access control check
3. Deny by default
4. Follow principle of least privilege
5. Do not hardcode roles
6. Log all access control events
7. Eliminate development/debug backdoors in the production code


## Module: Logging and Exception Handling


- **Logging**: Keeping chronological record of system or application activities.
- **Exception Handling**: Process of responding the exception gracefully, handle it well, and do not stop working abruptly.


Without proper logging, it is impossible to investifate an application compromise or data breach. Without solid exception handling, applications behave in unknown and unspecified ways.


### Threats to logging

1. Repudiation : bad actor can perform malicious activity on a system but without logging it is impossible to prove if anything happened.
2. Information disclosure: PII or passwords leaked in the logs.

### Logging weaknesses

1. Lack of security relevant information in the logging
2. Insuffiient logging
3. Logging excessive data
4. Unchecked error condition

### Which events to log
1. Input validation failures
2. Output validation failures
3. Authentication success and failures
4. Authorization(access control)failures
5. Session management and faillures
6. Application errors and system events
7. Application and related systems start-ups and shut downs, and logging initilization(starting, stopping or pausing)
8. User of higher risk functionality
9. Legal and other opt-ins

### Where should we log

1. Filesystem : Use separate partitions with proper file permissions
2. Database: Separate DB account with restrictive permissions
3. SIEM: Security info and event management, Consolidate all logs together


### 4 Ws of Logging

1. When: Log and Event date and time
2. Where: App ID, app address, Service, geolocation, window/form/page, location in the codebase
3. Who: Source address, user identity
4. What: Type of event, severity, security relevant, description


### Data to exclude from logs

1. Application source code
2. session id values
3. access tokens
4. Sensitive personal data and PII
5. authentication passwords 
6. database connection strings
7. encruption keys and other master secrets
8. bank account or payment card holder data
9. data of higher security classification than the logging system is allowed to store
10. commercially sensitive information
11. information that is illegal to collect in the relevant jurisdictions
12. information a user has opted out of collection or not consented to



### Tips for logging data at rest

1. Make data tamper-proof
2. Access to the logs must be recorded and monitored
3. Privileges to logs should be periodically reviewed and remove anyone who no longer needs access
   
### Tips for Protection of logging data in transit
1. use a secure transmission protocol
2. Consider whether the origin of the event data needs to be verified
3. Perform due dilligence checks (regulatory and security) before sending event data to third parties

### Monitoring of Events

1. Incorporate the application logging into any existing log management system/infra
2. Ensure event information is available to appropriate teams
3. Enable alerting and signal the responsible teams about more serious events immediately
4. Share relevant information with other non-competitive organizations

### Security concerns for exceptions

1. Prevent system information leakage that could aid a malicious user
2. Ensure application fails securely under all circumstances
3. Use a centralized error strategy to reduce points of failure and promote consistency
4. Log when exceptions are thrown and include sufficient details for security auditing



## Module: Crytography

Techniques for secure communication in the presence of adversaries.

When the crytography goes wrong, you see erros like "Your connection is not private" or "This site can't provide a secure connection".


### Key Terms

1. Key : Binary string used as a secret parameter used by cryptographic algorithm and measured using length in bits. It can be used to lock/unlock data that is encrypted or decrypted.
2. Cipher : special kind of algorithm that encrypts or decrypts data for you.
   1. Block Cipher : Works on fixed size of blocks, 8 or 16 bytes
   2. Stream Cipher: Works on continuos stream of bytes
3. Symmetric encryption : Uses same secret key for encryption and decryption
4. Asymmetric encryption : Public and private key concepts for encryption and decryption process
5. Certificates : Used by webservers and it contains set of data about identity of a site, their public key and signed by a trusted third party.
6. Hashing : Plaintext via hash function creates much smaller hash value.
7. Digital Signature : Asymmetric key operation. Private key is used to sign the data and public key is used to verify the signature, providing authenticity protection, integrity protection and non-repudiation.


### Different Ciphers

Over the time, computers have gotten stronger and they can crack the weak cipher algorithms. Hence we need to use stronger algos.

- Symmetric: 
  - Use: AES (Advanced Encryption Standard)
  - Caution: Triple DES
  - Don't Use: Data Encryption Standard(DES), Skipjack, RC4
- Asymmetric:
  - Use: RSA with at least 2048 bits, elliptic curve
  - Caution: Diffie-Hellman

### Rolling your crypto : BAD

Cryptography is difficult and people spend decades understanding the algorithms and improving them. Rolling your crypto would not likely match the same level of security unless you do the due dilligence equivalent of years of research.Anyone can create an algorithm that they themselves can't break and that is a bad algorithm.



## Module: Risk Management in AppSec

Risk management is a program and a process, that you are going to use to manage information security risk to operations, assets, individuals and other organizations.It includes establishing the context for risk-related activities, assessing risk, responding to risk once determined and monitoring risk over time.

### Process for risk management

1. Identify the risk
2. Analyze the risk
3. Evaluate or rank the risk
4. Treat the risk
5. Monitor and review the risk



### Risk management principles

1. Accept that there will always be uncertainty, make the best decision possible. if you make mistake, don't seek blame, learn from them.
2. Make security risk management "business as usual", it should be part of your work.
3. Know what you care about and why, understand what needs to be protected, it reflects in the approach you take to manage risk.
4. Understand what risks you are actually taking, achieve clear view of your compromises, and likeliness and severity of impact. Helps you prioritize things.
5. Appreciate fully how risks are being managed, decide how to deal with the risk.
6. Recognize the limitations of your risk management approach. All approaches have limitations.
7. Control and direct things you do to manage risk
8. Ensure systems are secure and usable
9. Make sensible and timely risk management decisions
10. Get assurance that security is working as you expect



## Module: The  Hacker(Problem Solver) Mindset

**Hacker** is a skilled computer expert that uses their technical knowledge to overcome a problem.

### Types of hackers

1. White Hat : Help companies eliminate vulnerabilities, even if they have enough knowledge to do bad things too, choose not to do it.
2. Black Hat : breaks into systems illegally, same kind of knowledge as white hat but do bad things.
3. Gray Hat : security consultants by the day but black hat hacker by night.

### Hacker Attitude

1. The world is full of fascinating problems waiting to be solved
2. No Problem should ever have to be solved twice
3. Boredom and drudgery are evil.
4. Freedom is good.
5. Attitude no substitute for competance.


### Hacker view

1. No such thing as secure
2. Always takes Least resistence, easy way to get into system
3. Outside of the box thinking


### Programmer, Developer, Hacker

1. Programmer : doesn't have to be professional, hobbyist too
2. Developer : Professional and more classically trained
3. Hacker : Knows how to take pieces of tech, put together to achieve something


### Applying hacker mindset

1. Extend your competance , be hungry to learn.
2. Use threat modeling, vulnerability scanning and penetration testing to discover the vulnerabilities in your project.
3. Utilize a white-hat approach to hacking.


## Module: OWASP Top 10

### What is OWASP top 10

Most comprehensive document for web application security risks. It is a data driven list. It has been gathered by collecting and analyzing data from various sources.

### Injection

Inserting malicious data into a program as an input. E.g. SQLInjection, CommandInjection, LDAP Injection. It applies to web or any other programs. 

E.g. input username as `SELECT 1 FROM [USERS] WHERE [USERNAME] = 'jsmith' OR 1=1 -- 'AND [PWD]=<user's password> ` this way attacker can inject SQL command into the program.

Mitigation:  use parametrized queries and use LIMIT to query database. So as to prevent attacker to not get more than one data record. Another thing you do is "White list" input validation on the server side. Move to Object Relational Mapping(ORM). E.g. Django ORM.

### Broken Authentication

Incorrectly implemented authentication allowing the compromise of passwords, keys or session tokens or to assume another's identity temporarily or permanently.

Credential stuffing: Attacker uses credentials from data breach or computer underground and use those to try to login to a web app using known username password combinations of hacked data. A smart application would stop attacker from trying more than a few times. 

Applies to any program/application written, web or non-web.

Mitigation:
- Multi-factored auth
- No Default creds
- Implement weak password check


### Sensitive Data Exposure

When disclosed information could identify a person or allow unauthorized acces.

E.g. File upload flaw in our app could allow attacker to download password database with unsalted or simple hashes, attacker cracks those hashes and gains access to user accounts.

Risk is data exposure as result of weak storage implementation, which could be PII as well as login creds or financial info. Data falls under privacy laws, protection regulation or others and result in massive fines and loss of trust for your company in the public.


Mitigations:
- Classify and identify sensitive data
- Use strong algos and keys to encrypt data with proper key management
- Encrypt all data at rest and in transit

### XML External Entity (XXE)

Untrusted XML input containing a reference to an external entity is processed by weakly configured XML parser. C/C++ does not suffer from that, as there are not a lot of webapps using C/C++ to parse XML.

Risks:
- Extraction of Data
- Execute a remote request from the server
- Scan Internal systems
- Perform denial-of-service attack
- Execute other attacks

Mitigations:
- Use JSON, XML slowly going away
- Patch or upgrade all XML processors and libraries
- Disable XML external entity and DTD processing in all XML parsers


### Broken Access Control

Attackers using browser to try all pages/apis and see if any of it is unprotected.Some developers don't check authentication/authorization on other places.

Risk:
- Data compromise, stolen or abused


Mitigation: 
- Implement access control as trusted server-side code
- Utilize single access control mechanism across the application
- Work hard to get it right from the very beginning, can't be done as an afterthought

### Security misconfiguration

Configuration of product or application results in security risk. E.g. Production server has application server platform installed and the sample application is left there to run on the system. The sample applications like Nginx/HTTP server default page applications can be risky and cause risk to the system if the attacker gains access to it.


Risk:
- Data could be exposed as a result of this vulnerability

Mitigations:
- Perform repeatable and identical hardening for all builds
- Build a minimal platform with only the pieces you need(e.g. build very small containers)
- Implement an automated process to verify the configurations and settings, identify drifts proactively.

### XSS

Attacker injects Evil javascript that is stored in the database of an application, and genuine user gets malicious javascript in the user's browser.

Risk:
- Steal admin sessions or sensitive data
- Rewriting customer or third-party web page if XSS is reflected through an application
- Redirect to a phishing or malware site if XSS is reflected through an application


Mitigations:
- Use frameworks that automatically escape XSS by design
- Perform contextual output encoding
- Enable a content security policy (CSP)


### Insecure Deserialization

Use of an object from an Untrusted source without proper verification

Risks:
- Attacker can modify objects and do malicious things

Mitigations:
- Do not accept serialized objects from untrusted sources
- Implement digital signature on any serialized objects
- Enforce strict type constraints during deserialization before object creation

### Using components with known vulnerabilities

If you build your software with a component that has vulnerability at the time of use.

Risks:
- User doesn't know and care if the issue is with your code or some library you use but someone else writes.
- Sometimes developers ignore Sev3 issues although attackers have sometimes made use of those.

Mitigations:
- Inventory versions of components and dependencies using tools
- Use software composition analysis to automate the process
- Monitor for libraries and components that are unmaintained or do not create security patches for older versions




### Insufficient logging and monitoring

Lack of logging and monitoring events. E.g. an attacker attempting one user/password combination every X amount of time, until he finally gets the correct creds of some user, that is a big risk. You need to log and monitor for any such patterns.

Risks:
- If an attack is undetected, there is more likelihood for success. Most attacks start with probing and gathering info which is not caught by application logging.
- Identifying breaches took avg 191 days in 2016, attacks maybe present within your system long before you realize.

Mitigations:
- Ensure all login access control failures and server-side input validation failures are logged.
- Ensure high-value transactions have an audit trail with integrity controls.
- Establish effective monitoring and alerting.



## Module: Buffer OverFlow and Remote code execution


### **Buffer OverFlow** 
When a program attempts to put more data into a buffer than it can handle. It could result in an attacker controlling the flow of a program on your computer. With control flow comes the ability to drop to a shell. Dropping to shell is bad.

**Threats**:
- Execute unauthorized code or commands
- Privilege Escalation
- Modify Memory
- Denial of service


### Types of Buffer OverFlow

- Stack based Bufer overflow: Buffer on the program's call stack outside of the intended data structure is overwritten with a new memory address.
- Heap based Buffer overflow: Buffer in the heap portion of memory is overwritten.
- Integer Overflow: Buffer storing a value is incremented to a value that is too large to store as an integer which cause the value to wrap and become a very small or negative number.


#### Mitigations
- Use coding language that does not have buffer overflow weakness.
  - E.g. With C language, use Safe C library
- Automatically provide a protection mechanism that mitigates or eliminates buffer overflows. 
- Practice input validation and check buffer sizes before use(hard to do.)
- Use a CPU and operating system that offers Data Execution Protection(NX).
- Run code with least of lowest privilege.

### **Shell code**

Small piece of code used as the payload in the exploitation of a software vulnerability

- Local : logged in as local user on some system and try to modify access and attack local system.
- Remote : Attacker is going to send from some other system
- Download and Execute : Downlod some malware and execute it on the target system.


**RCE - Remote code execution**: When an attacker executes any command on a target machine or in a target process across the Internet.



## Module: Denial of Service

Renders our product or application unusable. By definition, it is an attempt to make service or network application unusable.

In **Distributed Denial of service** where multiple compromised systems are used to target a single system.

**Threats**:
- Crashes, exit or restart of systems
- CPU resource exhaustion
- Memory resource exhaustion
- Network or disk resource exhaustion

**Facts about DDoS**:
- We are in a Terabit attack Era
- 6.13 million attacks yearly, 16794 attacks daily.
- Average cost of customer downtime is $221,836.80
- 91% of enterprises say one or more attacks completely saturated their internet bandwidth.


### Types of Attacks
- Protocol
- Recursive
- Volumetric
- Application Layer
- Low and slow attack
- R-U-Dead-Yet(RUDY) attack



### Mitigations:

- Detection - you can't stop what you can't see.
- Black hole routing/rate limiting
- Web app firewall(WAF)
- Content delivery network: AWS, Akamai, CloudFare



## Module: XSS Cross-Site Scripting

### What is XSS? 

Malicious code is inserted in your browser by malicious or sometimes benign looking websites. You need to care about it as losing your cookies, session tokens can let attacker access sites as if they were you.

### Threats

- Someone can grab your admin session cookies
- Rewrite a webpage
- Redirect to a phishing or malware site


### What is Stored or persistent XSS? 

A malicious script is permanently stored, causing a victim to retrieve it when requesting stored information.

- Attacker submits evil javascript to a web app
- Stored evil JS goes into database
- User requests a page from that web app
- User retrieves a page that contains malicious code
- User falls victim to that evil JS


### What is Reflected or non-persistent XSS?


An injected script is delivered via an e-mail or other web site and takes the victim to the vulnerable site, which reflects the attack back to the victim's browser.
- Attacker sends an email with link containing a malicious site
- User clicks it and downloads a malware by mistake
- It gets stored in user browser and eventually gets executed


### What is DOM based XSS?

Attacker injects a script into DOM(Document object model) environment and executes in the victim's browser.

- Sources : It is a property that is read from the DOM. Example, `document.URL`, `location.href`, `location.search`, etc.
- Sinks : It is a point in the flow of data where untrusted input gets outputted on the page or executed by JS within the page. Example, `eval`, `setTimeout`, `document.write`, `location.href`


### Mitigations

- Use framework that automatically escapes XSS by design
- Escape untrusted HTTP request data bawsed on the context in the HTML output
- Apply context sensitive encoding when modifying the browser document on the client side
- Review client side code for sinks and sources
- Enable Content Security policy (CSP)



## Module: Injection Attacks

Tricking an application into including unintended commands in the data sent to an interpreter.

Injection allows an attacker to execute commands within your app or product, outside of your control.

### Types:

- SQL Injection 
- OS Commands Injection
- LDAP Injection
- XSS Injection


### Threats:

- Execute unauthorized commands or code
- Read application data
- Bypass protection mechanism
- Modify application data

### Mitigation:

- Perform proper input validation
- Contextually escape user data
- LDAP: Use frameworks that automatically protect from injection
- OS: Avoid calling OS commands directly
- SQL: Utilize prepared statements with parameterized queries


## Module: CSRF - Cross Site request foregery

### What is CSRF? 

An attack that forces an end user to execute unwanted actions on a web application in which they're currently authenticated.

E.g. would be an attacker embed malicious `src` within an `image` tag of http and user is logged into a sensitive app, when this `image` tag is 
being rendered, it is calling the maclicious `src` and actually executing a harmful action without the user's knowledge.

### What is a Synchronizer token (CSRF Token)?

Whenever any state changing operation is to be performed, a CSRF token is added as a hidden field for forms or within URL, then server can reject any other requests that are not coming from that token for that particular session.


### What is SameSite cookies?

It is relatively new and defends against CSRF. You append this to your cookies. Currently not all browsers serve this correctly, so you would set this to `SameSite=Lax` but in the future you will be able to set it to `SameSite=Strict`.

- Strict : Prevent the cookie from being sent by the browser to the target site in all cross-site browsing context, even when following a regular link.
- Lax : Provides a reasonable balance between security and usability for websites that want to maintain user's logged-in session after the user arrives from an external link.Session cookies are allowed when following a regular link from an external website while blocking it in CSRF-prone request methods(e.g. POST).

 

 ### CSRF Risks

 - Successful CSRF attack can  force the user to transfer funds, change their email address and so forth.
 - If the victim is an admin, CSRF can compromise the entire WebApp.

### CSRF Mitigations
- Include an unpredictable CSRF token with each request.
- Use framework-provided CSRF defence.
- Enable `SameSite=Lax` for any cookies.



## Module: Insecure Communications

**Insecure Communication:**  is tranmission of sensitive data in the form of plain text over the any communication medium, which can be sniffed by an attacker.
**Network Sniffing:** A software can be used to monirot or sniff out the data flowing over computer networks in real time. E.g. Wireshark


**Threat:** Developer fails to adequately encrypt network traffic using strong cryptography and customer data is exposed and compromised.

### Mitigations:

- VPN
- TLS
  - SSL is no longer considered usable for security.
  - ALL pages must be served over HTTPS, including CSS, scripts, AJAX, images, POST.
  - HTTP strict transport security header instructs compatible browsers to use HTTPS even if requested to use HTTP.
  - Cookies must be marked as secure.

### Ciphers choices

- Key exchanges:
  - RSA, DH - proceed with caution
  - ECDH - most secure
- Authentication:
  - Use: RSA, ECDSA
- Bulk Encryption:
  - Use: AES(128/256 bits), ChaCha20(256), AESGCM(256)
  - Don't use: DES, RC4, SEED(128), 3DES(168) 
- Message Authentication:
  - Use: SHA256, SHA384, AEAD
  - Don't Use: MD5, SHA1


## Module: Social Engineering

Psychological manipulation of people into performing actions or divulging confidential information.


**Goals of a human attack:**
- Trick user to:
  - Click a link
  - Telling a secret
  - Open a door



|Method |Vector  | 
--- | --- |
|Phishing|Emails|
|Vishing|Phone|
|Smishing|SMS|
|Impersonation|In-person|



**Social engineering tactics:**
- Baiting
- Spear phishing
- Pretexting
- Shoulder Surfing
- Quid pro quo
- Phishing
- Tailgating
- Dumpster Driving
- Whaling 

### Social Engineering Process

- Gather Information - Learn about target
  - Telephone
  - Web Search
  - Social Media
  - Dumpster driving 
- Establish Rapport - Engage with them in some conversation so they believe you are genuine
  - Smiling and eye contact
  - Connect on the phone
  - Show family pictures to receptionist
  - Use a fake profile to build a relationship
- Exploitation - by asking for some info, or access or favor.
  - Open a door
  - Disclose a password
  - Plugin a USB w/malware
  - Open an infected attachment
- Execution - attack is conducted



## Module: AppSec in an Agile World

### Agile Terms:

* User Story: in consultation with the customer or product owner, the team divides up the work to be done into functional increments.
* Backlog: Ordered list of items representing everything that may be needed to deliver a specific outcome.
* Daily review: an opportunity for a team to get together on a regular basis.
* Incremental development: each successibe version of the product is usable and each builds upon the previous version by adding user-visible functionality.
* Scrum: a process framework used to manage the product development and other knowledge work.
* Sprint: Duration of time you use for your work. You should have security built into your each sprint and also have a sprint focused on security every 3-6 sprints.

### Highlight from Agile Manifesto

* Individuals and interactions over proceses and tools
* Working software over comprehensive documentation
* Customer collaboration over contract negotiation
* Responding to change over following a plan


### Agile principles impacting security


* Principle 1: Our highest priority is to satisfy the customer through early and continuous delivery of valuable software
  * W/security: Secure software satisfies customers.
* Principle 2: Welcome changing requirements, even late in development. Agile processes harness change for customer's competitive advantage.
  * w/Security: Flexible security activities that quickly include new work.
* Principle 3: Deliver working software frequently, from couple of weeks to a couple of months with a preference to shorter timescale.
  * w/Security: Automation of security tools is mandatory to move faster.
* Principle 4: Business people and developer should work together on daily basis.
  * w/Security: make sure to include security team members in this interaction.
* Principle 5: Build project around motivated individuals. Give them the environment and support they need, and trust them to get the job done.
  * w/Security: knowledge of security allows building of security trust.
* Principle 6: The most efficient and effective method of conveying information to and within a dev team is face-to-face convo.
  * w/Security: Use security champions as well during all conversations.
* Principle 7: Working software is the primary measure of progress.
  * w/Security: Basic security features and functionality must be included.
* Principle 8: Agile processes promote sustainable development. Team members should be able to maintain a constant pace indefinitely.
  * w/Security: Security champions help maintain a constant pace, while considering security.
* Principle 9: Continuous attention to technical excellence and good design enhances agility.
  * w/Security: Threat modeling improves design.
* Principle 10: Simplicity -- art of maximixing the amount of work not done -- is essential.
  * w/Security: Keep it simple is good advice for application security.
* Principle 11: The best architectures, requirements and designs emerge from self-organizing teams.
  * w/Security: Autonomy and individuality of a scrum team(security choices) requires strong security culture.
* Principle 12: At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.
  * W/security: Security must participate as part of the feedback process.


### Sprint with Security

1. Plan: Security requirements for the features are captured in the user stories.
2. Development: 
   1. Threat modeling and mitigation
   2. Secure coding
   3. Security code review
   4. Static analysis
3. Test:
   1. Dynamic analysis
   2. Vulnerability scanning
4. Deploy:
   1. 3rd party software
   2. PSIRT


### Definition of Done

Agreed upon list of activities deemed necessary to get a product increment, usually represented by a user story, to a done state by the end of a sprint.

- Threat modeled
- Security code review complete
- Code complete 
- Unit tests written and executed
- Integration tested
- Performance tested
- Security tested(static, dynamic and vulnerability)


### Security focused agile sprint

1. Plan: 
   1. Privacy assessment
   2. Product Security baseline review
   3. Attack surface reduction
2. Dev:
   1. Incident response plan
3. Test:
   1. Penetration testing
4. Deploy:
   1. PSIRT



## Module: AppSec in DevOps World

* Continuous Integration - Keep integrating your code to main repo frequently
* Continuous Delivery - automatically build, tested and prepared for a release to production
* Continuous Deployment - all changes to a testing and/or prod environment after the build and test phases are green

* Continuous Security - this is not defined properly but needs to be integrated. DevSecOps/SecDevOps or whatever you call it.

### DevSecOps

* Plan - Integrate security best practices/requirements into your plan phase.
* Design - in this phase you should be doing threat modeling.
* Development -
  * Secure code review - have someone with security mindsel review your code
  * software composition analysis - use appropriate tools to analyze the code
* Integration -
  * Static analysis - code check for syntax etc
  * Integration tests - functional/feature based automated security test
  * Container tests -  Test container builds with our software if security is violated somewhere
* Delivery -
  * Dynamic Analysis
  * Automated Tests - run full suite
* Deployment - 
  * Secret injection - Insert keys/passwords etc all.
* Production -
  * Vulnerability scanning - for code and infrastructure/networks etc.
  * Red teaming - Penetration testing


## Module: Security behaviors for DevOps

Manner of behaving that decreases danger, risk, threat.

- Clear Start and finish point
- Why and ROI
- Easily Repeatable
- Lightweight
- Well Defined

Goal is to reach security habits.


### Security Behaviors and Habits

* Build security left and starting left - Think about security best practice from the beginning. Habit will be generated when developers know why it matters.
* Uncover design security problems - Threat modeling, with desired outcome to choose the design decision that protects the confidentiality and integrity of customer data. Habit will be generated when we learn how to create a threat model, start threat modeling by getting hands-on with an active design.
* React to automated security bugs - Static, Dynamic analysis and vulnerability scanning produces bugs. Desired outcome is to interpret automated security notifications as a gift and not as a curse. Habit generation happens grasp all different types of vulnerabilities that the tools may find. Aggressively limit false positive - do not scan for everything in the beginning.
* Detect security flaws in others code - Secure code review, use it to find vulnerable pieces in the code. Make this a habit by force security code review in the commit process. Require a +1 from security guru on your team.
* Work towards eradication of 3rd party software vuln's - 3rd party software dependency checking, eliminate known vuln components at deploy time. Make it a habit to break the build on a sw composition analysis failure
* Be mean to your code - Red Teaming. Uncover flaws using active testing, fix those flaws and push the fixes to prod ASAP. Make this a habit by realize your code will be attacked, spend time attacking using tools and your brains.
* Respond in a timely and organized fashion - PSIRT. Partnership between dev and PSIRT to alleviate any security bugs in the shortest amount of time possible. Habit is made when you recognize the PSIRT mission, meet with customer and hear first hand why security matters.



## Module: Writing Security Requirements

### Uses:
1) Guidance/Best practices - checklist of what to build into security controls
2) Metric - A yardstick to assess and measure the degree of trust that can be places in a product or application
3) Procurement vehicle - Specifying security requirements in contracts

### The positive impact of security requirements

1) Basis for roadmap of product/application security improvements
2) repeatable and standard security
3) Clearly define what developers, system architects and designers need to build

### Sources for Security Requirements

* Industry Standards: Common Criteria, NIST, FIPS 140-2, App Security Verification standard, pci DSS compliance
* Applicable Laws: HIPAA, General Data Protection Regulation(GDPR)
* History: Heartbleed, SSLv3, shell shock

### Three Phases of security requirements

* Discovery and selection
* Investigation and documentation
* Implementation, test and measurement


## Module: Threat Modeling Basics

Apporach for analyzing the desing of a feature, application, or product and eliminating potential security flaws. This helps having fewer security bugs upto and after the release.

### Benefits:
1) Ensures that application security is built into the product as it's being developed.
2) Security problems are found and fixed early in the development process.
3) The security mideset is encouraged in developers and testers.

### Security Feedback loop

* Identify Threats
* Evaluate Mitigations
* Change the design

And then start over.

### Threat Modeling in the SDL

* Training
* Requirements
* Design
* Develop
* Test
* Release

### Threat Modeling Process

* Define Scope
* Draw diagrams or write down what you are modeling
* Analyze each item your wrote/drew
* Mitigate
* Document


### A "good" Threat Model
* Threat Model is not an exact science
* Threat Model is experience based
* Perfect is the enemy of good
* Threat modeling expands the mind
* Threat model is an iterative process
* Threat model is never done
* Re-visit threat model at appropriate frequency

### Threat Modeling Tools

* White Boards (old school)
* Microsoft TM Tool
* IriusRisk


### 4 questions for threat modeling

- What are we building?
  - Scope - Decide what are we going to threat model? Feature/Function? Subcomponent of a product or the entire product/application? Identify attacker(user/system/hacker), attack surface(network protocols,web interface, system daemon, network packets, cli, administration ).
  - Draw - Data flow Diagrams. External entity->trust boundary -> Our App Process -> Data store is a typical data flow would look like. Primarily look at trust boundary.
- What can go wrong? 
  - Analyze -DFD diagram elements map to each of these (use stride method, initials of each threat below forms the word stride. E.g. S for Spoofing.)
    - Spoofing
      - External Entity, Process
    - Tampering
      - Process, data store, data flow
    - Repudiation - Can someone modify any information within your system without anyone noticing?
      - Process, data store, external entity
    - Information Disclosure
      - process, data store, data flow
    - Denial of Service
      - - process, data store, data flow
    - Elevation of Privilege
      - Process
- What are we going to do about it?
  - Mitigate -
    - Spoofing - Strong Authentication
    - Tampering - Encryption and hashing of data
    - Repudiation - logging and strong authentication
    - Info Disclosure - Encryption
    - Denial of Service - Site/product scalability
    - Elevation of privilege - Authorization
- Did we do a good enough job?
  - Document - 
    - Write down mitigations for all threats
    - Test cases based on discovered threats
    - Did we do a good enough job?



### Threat Prioritization

2 Factors:
- Likelihood - draw a graph with
  - Y Axis: Easy or Hard to exploit
  - X Axis: Countermeasures few to many
- Impact - draw a graph
  - Y Axis: Customers few->many
  - X Axis: Damage potential minor->major

E.g. Equation would be:
Likelihood(high)+impact(high) = High Threat
Likelihood(medium)+impact(low) = Medium Threat
Likelihood(low)+impact(low) = Low Threat


### Threat Modeling Examples

- Telnet
  - Prone to:
    - Tampering as its not a secure protocol
    - Elevation of Privileges
    - Spoofing
    - Information Disclosure
  - Mitigation:
    - Use SSH to avoid spoofing
    - Use SSH also to avoid packet sniffing
    - Disable Telnetd
- A typical Web App
  - Prone to:
    - Client Side javascript - they can turn off javascript, and security would be broken if its implemented on client side JS
  - Mitigate:
    - Perform auth on server side and keep trust boundary on server side


## Module: Static Application Security Testing(SAST)

Like a spell checker for your code.
Set of tech, helps to scan source code and find vulnerabilities. Like an advanced grep for pattern matching the security issues.

SAST is focused on our code(custom code), not underlying libraries, frameworks or other components.

SAST is at Develop phase of secure development lifecycle(SDL). Checking every piece of code being merged to master.

### Benefits
- Finds critical defects and security vuln in code during development.
- Identifies problems immediately after code is written, when it is easiest and cheapest to remediate.
- Automation places the execution on the infra and not on the developers to read it.

### SAST Traits

- White box security testing
- Finds vuln's early, less expensive to fix
- Pinpoints exact code location of vuln
- Misses run time and environmental issues
- Requires source code
- Supports most languages
- Misses design related flaws
- High number of false positives

### SAST Use Cases
- One off execution
- Nightly running SAST
- CI/CD
- Running on Desktop/IDE while you are coding

### Developer Workflow

- Scan
- Triage
- Fix
- Document


## Module: Dynamic Application Security Testing (DAST)

**Defn**: Set of technologies, and tools to detect vulnerabilities while application is running.

**Fuzzing** is an automated software testing technique that involves providing invalid, unexpected, or random data as input.

**DAST** is focused on all layers of a typical web app, that is custom code, libraries, frameworks, application server, runtime platform. DAST does not applies to other products that are non web-app systems.

**Fuzzing** applies to Products or web application, and applies to layers of custom-code, libraries and Frameworks/packages.

DAST and fuzzing sit in between Develop and Test phase, but mostly people do it in testing phase. They could run one off, nightly or within CI/CD process.

### Benefits:

1) Find critical defects, security weakness and vuln.
2) Detect runtime vulns, like misconfig or defects in the business logic.
3) Quick and simple integration into security program, built with automation in mind.
4) Fuzz specific: test design is simple/free of preconceptions about system behavior.


### Traits
DAST Fuzz

[x] [x] Blackbox testing

[x] [x] Requires a running application

[x] [x] Finds vuln's toward the end of SDLC; more expensive to fix

[x] [x] Discovers run time and environmental issues

[x] [-] Focus on web app and web services

### Classes of Fuzz finding

- Faults
  - Vulnerabilities
  - Unstable States
  - Undesirable conditions
  - Crashes


## Module: Next Gen AppSec Tools

**IAST:** Interactive application security testing, a solution that assesses application security from within using software instrumentation in test. Primarily focused on WebApp.
- Runs in test phase

**RASP:** Runtime application self protection, a security technology built or linked into an application that is capable of preventing real-time attacks in production. Runs both with WebApps or Products.
- Post release - runs at real time


**SCA:** Software composition analysis. It is a set of technologies that build an inventory of open source and commercial components and detect known security vulnerabilities in those components. This is focused on WebApp(Libraries and Frameworks) and on product side( libraries and packages too).

**CWPP:** Cloud workflow protection platform. Help you secure virtual machine, serverless, containers in private or public cloud. Integrated into CI/CD process. It applies to all layers of web or system apps, except custom code. So, libraries, frameworks(or packages), application server and runtime platform(OS).


## Module: Vulnerability Scanning

Comprehensive evaluation of a system for any exposed vulnerabilities.

Focus is on Application Server and Runtime for webapps and for products(system apps) the scanner focuses on Packages, Application server and operating system.

It fits between test and release phases, although it can run anytime you want. You can scan things in development as well.

### Benefits

- Catch low hanging fruits kind of issues
- validate patching and hardening program
- establish security baseline
- identify known, surface level security issues and misconfigurations
- find and fix issues before your customers do

### Traits
- Black box security scanning
- Focus on infrastructure and system problems(VMs, OS, network devices, cloud)
- Scans for vulnerability, configuration and compliance problems
- Continuously updated library of vulnerabilities and configuration checks
- Can login to a product and scan from inside(credentialed vs non-credentialed scans)

### Process of Vuln Scanning

- Is host alive?
- Firewall detection
- TCP/UDP port scan
- OS Detection
- TCP/UDP Service Discovery
- Vuln Assessment

### How does it work?

- You define/tweak policy, scan engine
- It scans packages, app server and OS
- Produces the report that a developer can look at and act upon

### Developer workflow

- Define
- Execute
- Report
- Triage
- Fix/Remediate
- Re-scan


## Module: Penetration Testing and Bug Bounty

**Simulated attack** that is **authorized** to evaluate security of a system or application.

**Bug Bounty** is crowd sourcing initiative that pays security researchers to report security issues.

These two focus on entire systems or web apps.

These two pieces fit post release.

### Benefits

- Find weaknesses that tools and internal team missed
- Prepare staff to better handle a crisis
- Identify multiple points of failure in a breach or disclosure
- Document and remediate vuln
- Identify lateral and vertical exploitation vuln that may lead to privilege escalation and sensitive data loss
- Augment existing security testing efforts with external expert resources.

### Pen Testing Process

- Evaluate a pen testing partner(company that will do this for you)
- Scope and goal setting
- Discovery
- Exploitation
- Documentation and reporting

### How to choose a pen testing company

- Consider real knowledge/track record versus just certification
- Seek penetration testers(specialists) and not generalists
- Check the process along with resumes
- Review example reports to understand recommendation approach
- Avoid glorified vuln scans

### Bug bounty process
- Establish goals and set scope
- Engage participants
- Review and prioritize submissions
- pay for the results
- Fix the problems

## Module: Secure Code Review

Take questions about security and apply those to code review process.

### Purpose

- Refactor
- Detect and Fix Errors
- Expose Vulnerabilities

### Process of secure code review

- Analyze
- Review
- Triage
- Remediate
- Review again
- Close


### Web Security Code Review Checklist

- Data Validation
- User management and Authentication
- Session Management
- Authorization
- Cryptography
- Logging and Error Handling
- Security Configuration

