# Solution for Hash Cracking Challenge #4

## Hash Information
- **Hash**: `a3a321e1c246c773177363200a6c0466a5030afc`
- **Hash Type**: SHA1
- **Cracked Password**: `DavIDgUEtTApA`

## Solution Steps

### Step 1: Hash Identification
Used hash-identifier tool to determine the hash type:
```bash
hash-identifier
```
- Input the hash: `a3a321e1c246c773177363200a6c0466a5030afc`
- Result: Identified as SHA1 hash

### Step 2: Wordlist Preparation
Used the provided `pass.txt` wordlist containing:
```
David 
Guettapan
Eminem
Davidguettapan
David Guettapan
```

### Step 3: John the Ripper Rule - NT
Used John the Ripper's default `NT` rule for case variations and character transformations.

### Step 4: Cracking Command
Used John the Ripper command:

```bash
john challenge4 --format=raw-sha1 --rules=NT --wordlist=pass.txt
```

### Step 5: Result
The hash was successfully cracked, revealing the password: **DavIDgUEtTApA**

## Analysis
- The password is derived from "Davidguettapan" with case variations applied by the NT rule
- The NT rule created mixed case transformations turning "davidguettapan" into "DavIDgUEtTApA"
- Demonstrates the effectiveness of case variation rules with custom wordlists

## Tools Used
- hash-identifier - For hash type identification
- John the Ripper - For hash cracking with NT rules
- Custom wordlist - pass.txt containing target variations