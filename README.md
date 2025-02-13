# [TNC MODULE](https://elkmire.github.io/TNC-Module/)
click here^

# TNC Module Encryption Guide

## Overview
The TNC Module uses a dual-factor encryption system combining a 6-digit passphrase with a variable-length numeric key. Let's analyze the total security space created by these combinations.

## Security Level Analysis

### Basic Security
```
Passphrase: 6 digits (e.g., 123456)
Key: 5 digits (e.g., 12345)
```
Total combination space:
- Passphrase possibilities: 10^6 (1,000,000)
- Key possibilities: 10^5 (100,000)
- Combined possibilities: 10^6 × 10^5 = 10^11 (100 billion) combinations
- Equivalent to ~37 bits of entropy

### Medium Security
```
Passphrase: 6 digits (e.g., 847593)
Key: 11 digits (e.g., 27384923847)
```
Total combination space:
- Passphrase possibilities: 10^6 (1,000,000)
- Key possibilities: 10^11 (100 billion)
- Combined possibilities: 10^6 × 10^11 = 10^17 (100 quadrillion) combinations
- Equivalent to ~56 bits of entropy

### High Security
```
Passphrase: 6 digits (e.g., 947284)
Key: 16 digits (e.g., 2738492384729384)
```
Total combination space:
- Passphrase possibilities: 10^6 (1,000,000)
- Key possibilities: 10^16 (10 quadrillion)
- Combined possibilities: 10^6 × 10^16 = 10^22 (10 sextillion) combinations
- Equivalent to ~73 bits of entropy

## Security Enhancement Factors

### PBKDF2 Protection
The system's use of PBKDF2 with 100,000 iterations adds significant computational cost to each attempt:
- Each guess requires two PBKDF2 operations (one for passphrase, one for key)
- The 100,000 iteration count means each guess takes milliseconds even on modern hardware
- Example: Testing 1 million combinations could take hours instead of seconds

### Effective Security by Key Length

| Key Length | Combined Possibilities | Entropy (bits) | Security Level |
|------------|----------------------|----------------|----------------|
| 4 digits   | 10^10 (10 billion)  | ~33 bits       | Very Low      |
| 8 digits   | 10^14 (100 trillion)| ~46 bits       | Low           |
| 12 digits  | 10^18 (1 quintillion)| ~60 bits      | Medium        |
| 16 digits  | 10^22 (10 sextillion)| ~73 bits      | High          |

## Practical Security Implications

1. **Basic Security (5-digit key)**
   - 100 billion total combinations
   - Vulnerable to dedicated cracking attempts
   - Suitable only for temporary or low-value data

2. **Medium Security (11-digit key)**
   - 100 quadrillion total combinations
   - Resistant to standard cracking attempts
   - Suitable for personal sensitive data

3. **Maximum Security (16-digit key)**
   - 10 sextillion total combinations
   - Highly resistant to all practical cracking attempts
   - Suitable for highly sensitive data

## Security Recommendations

1. **Key Length Selection**
   - Always use maximum key length (16 digits) for sensitive data
   - Minimum recommended key length: 12 digits
   - Remember: each additional digit multiplies total combinations by 10

2. **Randomization**
   - Use truly random digits for both passphrase and key
   - Avoid patterns or sequential numbers
   - Consider using a random number generator for key generation

3. **Combined Factor Strength**
   - The fixed 6-digit passphrase provides baseline security
   - The variable key length allows scaling security needs
   - Total security is multiplicative: passphrase combinations × key combinations

The system's security is robust when used with longer keys, despite the fixed passphrase length. The combination of AES-GCM encryption, PBKDF2 key derivation, and the multiplicative effect of two independent factors provides strong protection when properly configured with maximum key length.

# TNC Module Configuration Guide

## Understanding .tnc Files

A .tnc file is a secure configuration file that stores your encryption credentials (passphrase and key combinations). These files are themselves encrypted, adding an extra layer of security to your stored credentials.

## How Configuration Storage Works

### Basic Concept
When you save a configuration, the TNC Module:
1. Takes your current passphrase and key
2. Encrypts them with a password you provide
3. Saves them as a .tnc file

### Security Features
- Each .tnc file is independently encrypted
- Uses the same AES-GCM encryption as the main system
- Requires a separate password for access
- Generates unique security elements for each file

## Using Configurations

### Saving a New Configuration
1. Set up your passphrase and key in the TNC Module
2. Click the "💾 Save" button
3. Enter a password for this configuration
4. Choose where to save your .tnc file

### Loading a Configuration
1. Click the "📤 Load" button
2. Select your saved .tnc file
3. Enter the password for this configuration
4. Your credentials will automatically load if correct

## Best Practices

### File Management
- Keep different configurations for different purposes
- Use meaningful names for your .tnc files
- Examples:
  - `personal.tnc` - for personal encryption
  - `work.tnc` - for professional use
  - `secure.tnc` - for highly sensitive data

### Password Selection
- Use strong, unique passwords for each .tnc file
- Make passwords memorable but secure
- Don't reuse passwords from your encryption credentials

### Storage Security
- Store .tnc files separately from encrypted data
- Keep secure backups of important configurations
- Consider offline storage for sensitive configs
- Delete unused or outdated configurations

## Security Considerations

### Protection Layers
1. **File Encryption**
   - .tnc files are encrypted with AES-GCM
   - Each file has its own encryption elements
   - Password protection prevents unauthorized access

2. **Access Requirements**
   - The .tnc file itself
   - The correct password for that file
   - Both needed to recover credentials

### Risk Management
- Don't share .tnc files over unsecured channels
- Keep passwords separate from .tnc files
- Consider using a password manager for .tnc passwords
- Regular backups of critical configurations

## Recovery Planning

### Essential Elements
To recover stored credentials, you need:
- Access to the .tnc file
- The password used to create it
- A working copy of the TNC Module

### Backup Strategy
1. **File Security**
   - Multiple copies of critical .tnc files
   - Secure, separate storage locations
   - Regular verification of backups

2. **Password Recovery**
   - Secure documentation of passwords
   - Trusted backup contacts if needed
   - Emergency access procedures

## Organization Tips

### File Structure
- Group related configurations together
- Use consistent naming conventions
- Document which config is used where

### Usage Tracking
- Keep a secure log of active configurations
- Note which systems use which configs
- Record when configurations are created or updated

## Maintenance

### Regular Tasks
- Review and update configurations periodically
- Verify backup copies are accessible
- Remove outdated or unused configurations
- Test recovery procedures occasionally

### Security Updates
- Check for any security advisories
- Update configurations if security practices change
- Maintain current backup procedures

The .tnc configuration system provides a secure and convenient way to manage multiple sets of encryption credentials while maintaining strong security through encryption and password protection. When used properly, it allows for efficient management of different security levels and use cases while keeping your encryption credentials safe.
