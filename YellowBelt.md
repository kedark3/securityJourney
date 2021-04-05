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