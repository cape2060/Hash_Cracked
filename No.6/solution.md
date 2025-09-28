# Solution for Hash Cracking Challenge #6

## Hash Information
- **Hash**: `377081d69d23759c5946a95d1b757adc`
- **Hash Type**: MD5
- **Cracked Password**: `+17215440375`

## Solution Steps

### Step 1: Hash Identification
Used hash-identifier tool to determine the hash type:
```bash
hash-identifier
```
- Input the hash: `377081d69d23759c5946a95d1b757adc`
- Result: Identified as MD5 hash

### Step 2: Wordlist Preparation
Used the provided `passlist.txt` wordlist containing:
```
+1721
```

### Step 3: John the Ripper Rule - number
Used John the Ripper's `number` rule to append numbers to the base string:

```
[List.Rules:number]

$[0-9]$[0-9]$[0-9]$[0-9]$[0-9]$[0-9]$[0-9]
```

### Step 4: Cracking Command
Used John the Ripper command:

```bash
john challenge6 --rules=number --wordlist=passlist.txt --format=raw-md5
```

### Step 5: Result
The hash was successfully cracked, revealing the password: **+17215440375**

## Analysis
- The password is derived from "+1721" with additional numbers "5440375" appended by the number rule
- The number rule generated various numerical combinations until finding the correct sequence
- Demonstrates the effectiveness of number appending rules with phone number patterns

## Tools Used
- hash-identifier - For hash type identification
- John the Ripper - For hash cracking with number rules
- Custom wordlist - passlist.txt containing base phone number pattern