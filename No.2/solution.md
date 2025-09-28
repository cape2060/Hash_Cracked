# Solution for Hash Cracking Challenge #2

## Hash Information
- **Hash**: `7463fcb720de92803d179e7f83070f97`
- **Hash Type**: MD5 (identified using hash-identifier tool)
- **Cracked Password**: `Angelita35`

## Solution Steps

### Step 1: Hash Identification
Used hash-identifier tool to determine the hash type:
```bash
hash-identifier
```
- Input the hash: `7463fcb720de92803d179e7f83070f97`
- Result: Identified as MD5 hash

### Step 2: Wordlist Research
Based on the hint in the image (likely mentioning "daughter" or female context), searched for female names using wordlistctl:

```bash
python3 wordlistctl.py search female
```

This command provided a list of available female name wordlists.

### Step 3: Download Female Names Wordlist
Selected and downloaded the female names wordlist:

```bash
python3 wordlistctl.py --fetch fetch_term -l "female names" -d
```

### Step 4: John the Ripper Rule Creation
Used the same custom rule from Challenge #1 in John the Ripper configuration named `[List.Rules:cthl2.1]`:

```
[List.Rules:cthl2.1]
c$[0-9~`!@#$%^&*()_+-=]
c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]
c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]
c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]
c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]c$[0-9~`!@#$%^&*()_+-=]
c^[0-9~`!@#$%^&*()_+-=]
c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]
c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]
c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]
c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]c^[0-9~`!@#$%^&*()_+-=]
```

### Step 5: Rule Explanation
The custom rule `cthl2.1` works as follows:
- `c$[0-9~`!@#$%^&*()_+-=]` - Appends characters/numbers to the end of words
- `c^[0-9~`!@#$%^&*()_+-=]` - Prepends characters/numbers to the beginning of words
- Multiple combinations create variations with 1-5 characters appended/prepended
- This comprehensive rule covers various password mutation patterns

### Step 6: Cracking Process
Used John the Ripper with the custom rule and female names wordlist:

```bash
john --rules=cthl2.1 --wordlist=female_names.txt hash.txt --format=Raw-MD5
```

### Step 7: Result
The hash was successfully cracked, revealing the password: **Angelita35**

## Analysis
- The password follows the pattern: `[Female Name][Numbers]`
- "Angelita" - A female name from the wordlist
- "35" - Two-digit number appended using the cthl2.1 rule
- This demonstrates the effectiveness of using the same comprehensive rule set across different challenges
- The cthl2.1 rule successfully handled both simple numbers and complex character combinations

## Tools Used
- hash-identifier - For hash type identification
- wordlistctl - For finding and downloading female name wordlists
- John the Ripper - For hash cracking with the cthl2.1 custom rule

## Key Learning Points
1. Context clues in images can guide wordlist selection (male vs female names)
2. The same comprehensive rule set (cthl2.1) can work across different password patterns
3. Consistent methodology across challenges improves efficiency
4. Female names with numbers follow similar patterns to male names but require different wordlists

## Comparison to Challenge #1
- Both used MD5 hashes
- Both used the same cthl2.1 rule set
- Challenge #1: Male name + complex characters (`Zachariah1234*`)
- Challenge #2: Female name + simple numbers (`Angelita35`)
- Shows that the same rule can handle both simple and complex password mutations