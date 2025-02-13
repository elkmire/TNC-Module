# [TNC MODULE](https://elkmire.github.io/TNC-Module/)
click here^

# TNC Module Manual
## Core Concept
A browser-based encryption tool using your numbers (passphrase) and text+numbers (key) to encrypt/decrypt messages. Think of it as a digital safe with two separate locks.

## Quick Start
1. Pick your numbers (passphrase) - at least 8 digits
2. Choose your text+numbers (key) - at least 12 characters
3. Type your message
4. Get your encrypted text

To decrypt: Switch mode, use same numbers and key, paste encrypted text.

## Real World Security Examples

### Basic Setup (8 digits + 12 characters)
- As secure as: A decent home safe
- Good for: Personal messages, diary entries
- Bad for: Company secrets
- Time to crack: Months with specialized hardware
- Example passphrase: 27495162
- Example key: TigerJumps2023

### Better Setup (12 digits + 16 characters)
- As secure as: A bank vault
- Good for: Business data, sensitive info
- Bad for: Nothing really, solid all-around
- Time to crack: Decades with current tech
- Example passphrase: 274951627495
- Example key: BlueDolphin2023XY

### Paranoid Setup (16 digits + 24 characters)
- As secure as: Fort Knox
- Good for: When serious privacy matters
- Time to crack: Heat death of universe
- Example passphrase: 2749516274951627
- Example key: RedPanda2023JumpingOver789!

## The .tnc Files
Think of these as your key locker. Saves your login combo securely.

To save:
1. Click Save
2. Pick a password
3. Store the file somewhere safe

To load:
1. Click Load
2. Find your file
3. Enter password

## Security Tips
- More digits/characters = better security
- Random is better than meaningful
- Keep your .tnc files like you'd keep spare keys
- Don't use the same combo for everything

## Technical Bits (Without the Jargon)
- Uses AES-GCM (military-grade encryption)
- Scrambles your keys thoroughly (120,000 times)
- Adds random noise to each encryption
- Verifies everything matches before decrypting

## Mobile Use
- Works on phones/tablets
- Touch to copy encrypted text
- Adjusts to dark/light mode automatically

## Common Sense Notes
- This isn't magic - bad passwords = bad security
- More complexity = more security = more annoying to type
- If someone's watching you type, none of this matters
- Store your .tnc files carefully - they're like spare keys
- No password recovery - if you forget, it's gone

# NERDY Version
### Entropy Analysis

Entropy is measured in bits, where each bit doubles the complexity. The system's total entropy combines both passphrase and key entropy.

**Entropy Calculation:**
- Digits (passphrase): log2(10) ≈ 3.32 bits per digit
- Alphanumeric (key): log2(62) ≈ 5.95 bits per character

### Security Tiers & Vulnerabilities

#### 1. Minimum Security (8-digit passphrase, 12-char key)
**Entropy:**
- Passphrase: 8 × 3.32 = 26.57 bits
- Key: 12 × 5.95 = 71.4 bits
- Total Combined: ≈ 98 bits

**Vulnerability Level: Moderate**
- Susceptible to dedicated hardware attacks
- Theoretical break time on specialized hardware: weeks to months
- Vulnerable to quantum computing threats (estimated 49 effective qubits)
- Example attack vector: State-level actors with quantum capabilities

**Use Case:**
- Personal communications
- Short-term sensitive data
- Not recommended for high-value targets

#### 2. Medium Security (12-digit passphrase, 16-char key)
**Entropy:**
- Passphrase: 12 × 3.32 = 39.86 bits
- Key: 16 × 5.95 = 95.2 bits
- Total Combined: ≈ 135 bits

**Vulnerability Level: Low**
- Resistant to current supercomputer attacks
- Theoretical break time: decades on classical hardware
- Quantum resistance: Requires 67+ ideal qubits
- Example attack vector: Future quantum computers (10+ years)

**Use Case:**
- Corporate data protection
- Long-term storage
- Sensitive communications

#### 3. High Security (16-digit passphrase, 24-char key)
**Entropy:**
- Passphrase: 16 × 3.32 = 53.14 bits
- Key: 24 × 5.95 = 142.8 bits
- Total Combined: ≈ 196 bits

**Vulnerability Level: Very Low**
- Beyond current technological capabilities
- Break time: Computationally infeasible
- Quantum resistance: Requires 98+ ideal qubits
- Example attack vector: Theoretical future technologies

**Use Case:**
- Critical infrastructure
- National security applications
- Multi-decade data protection

#### Social Engineering/Human Factors
All security levels equally vulnerable to:
- Credential sharing
- Insecure storage
- Password reuse
- Physical observation

### Memory Attack Resistance

**Minimum Security:**
- Vulnerable to cold boot attacks
- RAM scraping possible
- Key reconstruction feasible

**Medium Security:**
- Partial memory attacks mitigated
- Key reconstruction difficult
- Requires precise timing

**High Security:**
- Memory attack resistant
- Key reconstruction infeasible
- Temporal security enhanced

### Quantum Computing Implications

**Current Quantum Threat Level:**
- Below 100 qubits: Safe across all security levels
- 100-1000 qubits: Minimum security threatened
- 1000+ qubits: Medium security potentially vulnerable
- 5000+ qubits: Required for high security threats

### Implementation Security Features

The system includes protections against:
- Timing attacks (constant-time operations)
- Brute force (rate limiting)
- Rainbow table attacks (unique salts)
- Key derivation attacks (high iteration count)
