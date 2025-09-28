# Solution for Hash Cracking Challenge #7

## Hash Information
- **Hash**: `ba6e8f9cd4140ac8b8d2bf96c9acd2fb58c0827d556b78e331d1113fcbfe425ca9299fe917f6015978f7e1644382d1ea45fd581aed6298acde2fa01e7d83cdbd`
- **Hash Type**: SHA3-512
- **Cracked Password**: `!@#redrose!@#`

## Solution Steps

### Step 1: Hash Identification
Used hash-identifier tool to determine the hash type:
```bash
hash-identifier
```
- Input the hash (128 hex characters)
- Result: Identified as SHA3-512 hash

### Step 2: Image Analysis
The image provided hints about:
- Hash format confirmation (SHA3)
- Wordlist selection (rockyou.txt)
- Password pattern structure

### Step 3: Cracking Command
Used John the Ripper with rockyou wordlist:

```bash
john challenge7 --format=raw-sha3 --wordlist=/usr/share/wordlists/rockyou.txt
```

### Step 4: Result
The hash was successfully cracked, revealing the password: **!@#redrose!@#**

## Analysis
- The password follows pattern: symbols + word + symbols (!@#redrose!@#)
- Found in rockyou.txt wordlist without needing custom rules
- Demonstrates effectiveness of comprehensive wordlists for common password patterns

## Tools Used
- hash-identifier - For hash type identification
- John the Ripper - For SHA3 hash cracking
- rockyou.txt wordlist - Comprehensive password database