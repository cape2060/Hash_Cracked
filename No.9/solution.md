# Solution for Hash Cracking Challenge #9

## Hash Information
- **Hash**: `$6$kI6VJ0a31.SNRsLR$Wk30X8w8iEC2FpasTo0Z5U7wke0TpfbDtSwayrNebqKjYWC4gjKoNEJxO/DkP.YFTLVFirQ5PEh4glQIHuKfA/`
- **Hash Type**: SHA-512 Crypt ($6$)
- **Cracked Password**: `kakashi1`

## Solution Steps

### Step 1: Hash Identification
Analyzed the hash format:
- **Format**: `$6$salt$hash`
- **Prefix**: `$6$` indicates SHA-512 Crypt
- **Salt**: `kI6VJ0a31.SNRsLR`
- **Hash**: Remainder of the string

### Step 2: Tool Selection
Used Hashcat instead of John the Ripper:
- **Mode**: `-m 1800` (SHA-512 Crypt format)
- **Wordlist**: rockyou.txt for comprehensive password coverage

### Step 3: Cracking Command
Used Hashcat command:

```bash
hashcat -m 1800 challenge9 /usr/share/wordlists/rockyou.txt
```

### Step 4: Result
The hash was successfully cracked, revealing the password: **kakashi1**

## Analysis
- The password "kakashi1" follows a common pattern: character name + number
- "Kakashi" is a popular anime character from Naruto series
- Found in rockyou.txt wordlist without needing custom rules
- Demonstrates effectiveness of comprehensive wordlists for pop culture references

## Tools Used
- Hashcat - For SHA-512 Crypt hash cracking
- rockyou.txt wordlist - Comprehensive password database