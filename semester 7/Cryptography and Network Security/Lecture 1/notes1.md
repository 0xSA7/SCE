## Aspects of Security

* Consider 3 aspects of information security
    * security attack
    * security mechanism
    * security service
* **Threat**: A potential for violation of security
* **Attack**: An assault on system security, a deliberate attempt to evade security services.

## CIA triad

* Confidentiality
    * Ensures that sensitive information is accessible only to authorized individuals.
    * Protects data from unauthorized access, disclosure, or exposure.
    * Prevents malicious actions that compromise private or classified information.
    * Common measures: encryption, access control, authentication, and data classification.
    
* Integrity
    * Ensures information is accurate, consistent, and unaltered by unauthorized entities.
    * Allows only authorized users or processes to modify data.
    * Protects against unauthorized modification, deletion, or corruption.
    * Common measures: hashing, checksums, digital signatures, and access controls.

* Availability
    * Ensures information and resources are accessible to authorized users when needed.
    * Prevents disruptions from failures, attacks, or overloads.
    * Maintained through redundancy, backups, and robust network design.
    * Protects against threats like DoS attacks or hardware failures.

## 1.2 Attacks

### 1.2.1 Attacks Threatening Confidentiality

* **Snooping**: unauthorized access to or interception of data.
* **Traffic analysis**: Obtainig some other type of information by monitoring online traffic.

### 1.2.2 Attacks Threating Integrity

* **Modification**: The attacker intercepts the message and changes it.
* **Masquerading**: known as **Spoofing** when the attacker impersonates somebody else.
* **Replaying**: means the attacker obtains a copy of a message sent by a user and later tries to replay it.
* **Repudiation**:
    * the sender of the message might later deny that she has sent the message.
    * The receiver of the message might later deny that he has received the message.

### 1.2.3  Attacks Threatening Availability

Denial of Service (DoS) & Distributed Denial of Service (DDoS)
* **DoS attack**: aims to slow down or completely disrupt a system’s service.
* **DDoS attack**: a more severe form using thousands or millions of coordinated machines.
* **Goal**: overwhelm the target’s resources (bandwidth, CPU, memory) so legitimate users can’t access the service.

###  1.2.4  Passive vs Active Attacks

* **Passive Attacks:** monitor or gather information without altering data.
  1. **Release of message contents (Snooping):** unauthorized reading of messages.
  2. **Traffic analysis:** observing communication patterns to infer sensitive information.

* **Active Attacks:** involve altering, disrupting, or forging communication.

  1. **Masquerade:** impersonating another user or entity.
  2. **Replay:** capturing and retransmitting messages to gain unauthorized access.
  3. **Modification of messages:** altering, adding, or deleting message contents.
  4. **Repudiation:** denying sending or receiving a message.
  5. **Denial of Service (DoS):** disrupting or blocking legitimate access to resources.

## 1.3 Services and mechanisms

###  1.3.1  Security Services
* Security services are mechanisms that provide protection to system resources and ensure secure communication between entities.

According to RFC 2828, a security service is:

> A processing or communication service provided by a system to give a specific kind of protection to system resources.

The main security services include:

* **Authentication**: Ensures that the communicating entity is who it claims to be.
    * **Peer-entity authentication**: verifies identity during connection setup.
    * **Data origin authentication**: verifies the source of received data.
* **Access Control**: Prevents unauthorized use of system resources.
* **Data Confidentiality**: Protects data from unauthorized disclosure.
* **Data Integrity**: Ensures that data is received exactly as sent, without alteration, by an authorized entity.
* **Non-Repudiation**: Prevents denial by any party involved in communication (sender or receiver).
* **Availability**: Ensures that system resources remain accessible and usable when needed.
###  1.3.2  Security Mechanisms 
#### Specific Security Mechanisms (X.800)
1. **Encryption**
2. **Digital Signatures**
3. **Access Controls**
4. **Data Integrity**
5. **Authentication Exchange**
6. **Traffic Padding**
7. **Routing Control**
8. **Notarization**

**Characteristics of a Security Service**
1. Enhances system security.
2. Counters security attacks.
3. Uses one or more mechanisms.
4. Replicates physical safeguards (signatures, dates, confidentiality, etc.).

## Implementation Techniques

#### Cryptography
* From Greek “secret writing.”
* Science of securing information by transforming it to unreadable format.
* Ensures confidentiality, authenticity, and integrity.

#### Steganography
* From Greek “covered writing.”
* Hides existence of data within another medium (e.g., image, audio, video).
* Example process:
  1. Convert data to bits.
  2. Choose a carrier file.
  3. Replace least significant bits (LSB) with data bits.
  4. Send the modified carrier.
  5. Extract bits in reverse to recover hidden data.

## Model for Network Security

* Framework for securing data during transmission.
* Key steps:
  1. Design secure algorithm.
  2. Generate secret keys.
  3. Distribute/manage keys.
  4. Define protocol for secure communication.

## Model for Network Access Security

* Controls access to internal systems.
* **Firewall (Gatekeeper):** filters traffic.
* **Internal Controls:** authenticate users (passwords, biometrics).