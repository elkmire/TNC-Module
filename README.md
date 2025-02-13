# TNC Security Module Manual

## Overview
The TNC Security Module is a browser-based encryption tool that implements AES-GCM (Advanced Encryption Standard in Galois/Counter Mode) for secure message encryption and decryption. The application uses the Web Crypto API to perform cryptographic operations with a two-factor authentication system consisting of a passphrase and key.

## Security Components

### Authentication Factors
1. **Passphrase**
   - 6-digit numeric code
   - Used as the primary input for key derivation
   - Must be exactly 6 digits, no other characters allowed

2. **Key**
   - Numeric-only string (variable length)
   - Acts as a secondary authentication factor
   - Used in conjunction with the passphrase

### Cryptographic Implementation

#### Key Derivation (PBKDF2)
- The 6-digit passphrase is processed through PBKDF2
- Uses SHA-256 as the hash function
- Performs 100,000 iterations for enhanced security
- Generates a 256-bit derived key
- A unique random 32-byte salt is generated for each encryption

#### AES-GCM Encryption
- Uses the derived 256-bit key for AES-GCM
- Implements a 12-byte (96-bit) random Initialization Vector (IV)
- Provides both confidentiality and authenticity
- Automatically handles authentication tag management

#### Encrypted Output Structure
The final encrypted message contains three concatenated components:
1. IV (12 bytes)
2. Salt (32 bytes)
3. Encrypted data (variable length)

The entire output is Base64 encoded for safe transmission.

## Credential Management

### Saving Credentials
- Credentials can be saved to a .tnc file
- Requires an additional password for file encryption
- The saved file contains both the passphrase and key in encrypted form
- Uses the same AES-GCM encryption for credential storage

### Loading Credentials
- Supports loading saved credentials from .tnc files
- Requires the original password used during saving
- Automatically populates both passphrase and key fields
- Validates credentials upon loading

## Security Considerations

### Advantages
- Uses standard cryptographic primitives (AES-GCM, PBKDF2)
- Implements proper key derivation with salt
- Ensures message authenticity through GCM
- Two-factor authentication system

### Important Notes
- Security depends on both passphrase and key secrecy
- Each encryption generates unique salt and IV
- Browser-based implementation ensures no server communication
- All cryptographic operations occur client-side

## Usage Best Practices

1. Always use unique passphrases and keys for different messages
2. Store credentials securely when saved to files
3. Use strong passwords for credential file protection
4. Clear all fields using the reset button after use
5. Verify successful decryption by testing immediately after encryption

## Technical Specifications

### Encryption Details
- Key Size: 256 bits
- Mode: Galois/Counter Mode (GCM)
- Salt Size: 256 bits (32 bytes)
- IV Size: 96 bits (12 bytes)
- Key Derivation: PBKDF2-SHA256
- Iteration Count: 100,000

### Supported Operations
- Text encryption/decryption
- Credential file export/import
- Real-time operation mode switching
- Automatic input validation

This implementation provides a robust security solution while maintaining usability through a simple interface. The use of AES-GCM ensures both confidentiality and authenticity of the encrypted messages, while the two-factor system adds an additional layer of security.
