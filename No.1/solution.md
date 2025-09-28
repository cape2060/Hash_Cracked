# Solution for Hash Cracking Challenge #1

## Hash Information
- **Hash**: `b16f211a8ad7f97778e5006c7cecdf31`
- **Hash Type**: MD5 (identified using hash-identifier tool)
- **Cracked Password**: `Zachariah1234*`

## Solution Steps

### Step 1: Hash Identification
Used hash-identifier tool to determine the hash type:
```bash
hash-identifier
```
- Input the hash: `b16f211a8ad7f97778e5006c7cecdf31`
- Result: Identified as MD5 hash

### Step 2: Wordlist Research
Based on the hint in the image mentioning "son", searched for male names using wordlistctl:

```bash
python3 wordlistctl.py search male
```

This command provided a list of available male name wordlists.

### Step 3: Download Male Names Wordlist
Selected and downloaded the top 100 male names wordlist:

```bash
python3 wordlistctl.py --fetch fetch_term -l "top 100 male names" -d
```

### Step 4: John the Ripper Rule Creation
Created a custom rule in John the Ripper configuration named `[List.Rules:cthl2.1]` to append and prepend various characters and numbers:

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

### Step 6: Cracking Process
Used John the Ripper with the custom rule and male names wordlist:

```bash
john --rules=cthl2.1 --wordlist=male_names.txt hash.txt --format=Raw-MD5
```

### Step 7: Result
The hash was successfully cracked, revealing the password: **Zachariah1234***

## Analysis
- The password follows the pattern: `[Male Name][Numbers][Special Character]`
- "Zachariah" - A male name from the wordlist
- "1234" - Sequential numbers
- "*" - Special character
- This demonstrates the effectiveness of using targeted wordlists combined with rule-based mutations

## Tools Used
- hash-identifier - For hash type identification
- wordlistctl - For finding and downloading wordlists
- John the Ripper - For hash cracking with custom rules

## Key Learning Points
1. Proper hash identification is crucial for selecting the right cracking approach
2. Contextual clues (like "son" in the image) can guide wordlist selection
3. Custom rules in John the Ripper can effectively handle common password patterns
4. Combining multiple techniques (wordlists + rules) increases cracking success rates