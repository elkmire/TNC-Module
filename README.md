# [TNC MODULE](https://elkmire.github.io/TNC-Module/)
click here^

# True Novel-Crypt (TNC) Encryption System

## What Is It?
The TNC encryption system is a backup tool for sending sensitive information when normal secure methods (like encrypted email or secure messaging) aren't available. Think of it as a digital safe that requires two separate keys to open, making it extremely difficult to break into.

## How Strong Is It?
The system uses military-grade encryption (AES-256 bit) with additional security features that make it even stronger:

1. **Two-Part Security:**
   - Requires both a passphrase and a key
   - Each part must be shared separately
   - If one part is exposed, the data remains secure

2. **Enhanced Protection:**
   - Uses longer random numbers than standard systems
   - Adds extra verification steps
   - Includes multiple layers of security checks

## What Makes It Unique?
1. **Dual-Key System**
   - Most systems use one password
   - TNC requires two separate components
   - Both must be correct to access the data

2. **Portable Security**
   - Credentials can be safely stored in .tnc files
   - Files are themselves encrypted
   - Easy to securely share with intended recipients

3. **Backup-Focused Design**
   - Made for occasional, critical use
   - Works through any communication channel
   - Doesn't require special software at both ends

## How Secure Is It?

### Strength Level
- Uses the strongest commercially available encryption
- Adds extra security through the two-part system
- Matches or exceeds banking and military-grade security standards

### Breaking the Encryption
To break this encryption, an attacker would need:
1. Supercomputers running for millions of years, or
2. Both the passphrase AND key components, or
3. A currently unknown mathematical breakthrough

### Real-World Security
The system is protected against:
- Password guessing attacks
- Computer-based cracking attempts
- Quantum computer threats
- Interception during transmission

## Using It Safely
For maximum security:
1. Generate credentials using the built-in generator
2. If manually generating credentials, store the passphrase and key separately
3. Share components through different channels
4. Use fresh credentials for different purposes
5. Keep .tnc files in secure storage

## Technical Details (For Those Interested)
- Base Encryption: AES-GCM 256-bit
- Nonce Size: 24 bytes (longer than standard)
- Salt Size: 64 bytes (extra long for security)
- Key Derivation: PBKDF2-HMAC-SHA512
- Iterations: 150,000 (very high for security)
