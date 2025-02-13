# [TNC MODULE](https://elkmire.github.io/TNC-Module/)
click here^

# TNC Module Manual
## Core Concept
A browser-based encryption tool using alphanumeric passphrases and mixed-character keys to encrypt/decrypt messages. Designed to provide a minimum of 128-bit entropy for guaranteed security.

## Quick Start
1. Create your passphrase - at least 22 alphanumeric characters with mixed case and numbers
2. Choose your key - at least 20 characters with mixed case, numbers, and special characters
3. Type your message
4. Get your encrypted text

To decrypt: Switch mode, use same passphrase and key, paste encrypted text.

## Real World Security Examples

### Standard Setup (22+ alphanumeric chars + 20+ mixed chars)
- As secure as: Military-grade encryption
- Good for: Everything from personal to enterprise use
- Minimum entropy: 130.99 bits
- Time to crack: Computationally infeasible with current technology
- Example passphrase: TigerJumps2023BlueSkies45
- Example key: RedPanda2023!JumpHigh$

### Enhanced Setup (32 alphanumeric chars + 32 mixed chars)
- As secure as: Post-quantum cryptographic standards
- Good for: Nation-state level security
- Entropy: ~190 bits
- Time to crack: Beyond foreseeable technology
- Example passphrase: TigerJumps2023BlueSkies45GreenEarth89
- Example key: RedPanda2023!JumpHigh$BlueMoon#2024@

### Maximum Setup (64 chars each)
- As secure as: Beyond current theoretical limits
- Practical entropy: 512 bits (limited by cryptographic primitives)
- Theoretical maximum: ~800 bits combined
- Note: Anything beyond 43 characters per input doesn't meaningfully increase security
- Good for: Future-proofing against quantum computing

## The .tnc Files
Secure storage for your credentials, encrypted with AES-GCM.

To save:
1. Click Save
2. Set a strong password
3. Store securely

To load:
1. Click Load
2. Select your file
3. Enter password

## Manual Entry Security Tips
- Quality over quantity: Mix uppercase, lowercase, and numbers in passphrase
- Use special characters in your key
- Keep your .tnc files secure
- Use unique combinations for different purposes
- Remember: Both passphrase and key must meet minimum requirements

## Technical Specifications
- Modified AES-GCM with 128-bit minimum entropy
- PBKDF2-SHA-512 key derivation (150,000 iterations)
- 64-byte salt
- 24-byte Initialization Vector
- 128-bit authentication tag
- Constant-time comparison for hash verification

## Mobile Use
- Full mobile compatibility
- Touch-to-copy functionality
- Automatic dark/light mode adaptation

## Important Notes
- System enforces minimum 130.99 bits of entropy
- Passphrase requires uppercase, lowercase, and numbers
- Key requires uppercase, lowercase, numbers, and special characters
- No recovery mechanism - store credentials securely
- Physical security is your responsibility

# Technical Details
### Entropy Analysis

Current system entropy is calculated as follows:

**Passphrase (minimum requirements):**
- Length: 22 characters
- Character set: 62 (a-z, A-Z, 0-9)
- Entropy: log2(62^22) = 130.99 bits

**Key (minimum requirements):**
- Length: 20 characters
- Character set: 94 (alphanumeric + special)
- Entropy: log2(94^20) = 131.09 bits

**System Entropy:**
- Minimum: 130.99 bits (limited by passphrase)
- Maximum practical: 512 bits (limited by PBKDF2-SHA-512)
- Theoretical maximum: ~800 bits (with 64-character inputs)

## TNC Module Credential Generator

The GEN button provides secure random credential generation that meets the TNC module's requirements while ensuring high entropy:

## Passphrase Generation
- Creates a 30-character string (~178 bits of entropy)
- Uses a mix of:
  - Uppercase letters (A-Z)
  - Lowercase letters (a-z)
  - Numbers (0-9)
- Guarantees at least one character from each required type
- Final string is randomly shuffled to prevent patterns

## Key Generation
- Creates a 64-character string (~384 bits of entropy)
- Uses a mix of:
  - Uppercase letters (A-Z)
  - Lowercase letters (a-z)
  - Numbers (0-9)
  - Special characters (!@#$%^&*()_+-=[]{}|;:,.<>?)
- Guarantees at least one character from each required type
- Final string is randomly shuffled to prevent patterns

## Security Features
- Uses the Web Crypto API's `crypto.getRandomValues()` for cryptographically secure random number generation
- Combined entropy exceeds 512 bits (passphrase + key = ~562 bits)
- Meets all TNC module validation requirements for both fields
- Automatically triggers input validation after generation

The generated credentials can be immediately used for encryption/decryption or saved to a credential file.

### Security Features

**Cryptographic Implementation:**
- PBKDF2-SHA-512 key derivation
- 150,000 iteration count
- 64-byte salt for key derivation
- 24-byte IV for encryption
- AES-GCM with 128-bit authentication tag
- Constant-time hash comparison

**Quantum Resistance:**
- Current minimum entropy (130.99 bits) provides adequate protection against near-term quantum threats
- Maximum practical entropy (512 bits) provides long-term quantum resistance
- System design allows for future entropy increases if needed

### Memory Attack Mitigation
- Constant-time operations
- No plaintext storage
- Secure key derivation
- Memory zeroing
- Input validation
- Error sanitization

### Implementation Security
Protected against:
- Timing attacks
- Brute force attempts
- Rainbow table attacks
- Key derivation attacks
- Memory inspection
- Side-channel leakage
