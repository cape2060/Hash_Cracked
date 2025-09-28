# Solution for Hash Cracking Challenge #3

## Hash Information
- **Hash**: `f4476669333651be5b37ec6d81ef526f`
- **Hash Type**: MD5
- **Cracked Password**: `Tl@xc@l@ncing0`

## Solution Steps

### Step 1: Hash Identification
Used hash-identifier tool to determine the hash type:
```bash
hash-identifier
```
- Input the hash: `f4476669333651be5b37ec6d81ef526f`
- Result: Identified as MD5 hash

### Step 2: Wordlist Preparation
Gathered all cities of Mexico and created `mexico.txt` wordlist file containing Mexican cities including Tlaxcalancingo.

### Step 3: John the Ripper Rule - l33t
Used John the Ripper's default `l33t` rule for leetspeak character substitutions.

### Step 4: Cracking Command
Used John the Ripper command:

```bash
john challenge3 --format=raw-md5 --rules=l33t --wordlist=mexico.txt
```

### Step 5: Result
The hash was successfully cracked, revealing the password: **Tl@xc@l@ncing0**

## Analysis
- The password is "Tlaxcalancingo" (a city in Mexico) with l33t transformations
- `a` → `@` and `o` → `0` applied by the l33t rule
- Demonstrates the effectiveness of geographic wordlists with character substitution rules

## Tools Used
- hash-identifier - For hash type identification
- John the Ripper - For hash cracking with l33t rules
- Geographic research - For building Mexico cities wordlist