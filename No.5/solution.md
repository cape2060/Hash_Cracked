# Solution for Hash Cracking Challenge #5

## Hash Information
- **Hash**: `d5e085772469d544a447bc8250890949`
- **Hash Type**: SHA1
- **Cracked Password**: `uoy ot miws ot em rof peed oot ro ediw oot si revir oN`

## Solution Steps

### Step 1: Hash Identification
Used hash-identifier tool to determine the hash type:
```bash
hash-identifier
```
- Input the hash: `d5e085772469d544a447bc8250890949`
- Result: Identified as md5 hash

### Step 2: Wordlist Preparation
Used the lyricspass tool to generate lyrics wordlist:
```bash
lyricspass
```
This tool creates `lyrics.txt` containing song lyrics for password cracking.

### Step 3: John the Ripper Custom Rule - reverse
Created a custom rule to reverse strings:

```
[List.Rules:reverse]
r
```

The `r` rule reverses each word in the wordlist.

### Step 4: Cracking Command
Used John the Ripper command:

```bash
john challenge5 --format=raw-md5 --rules=reverse --wordlist=lyrics.txt
```

### Step 5: Result
The hash was successfully cracked, revealing the password: **uoy ot miws ot em rof peed oot ro ediw oot si revir oN**

## Analysis
- The password is a reversed lyric: "No river is too wide or too deep for me to swim to you"
- The reverse rule `r` transformed the original lyric into the cracked password
- Demonstrates the effectiveness of text transformation rules with lyrics-based wordlists

## Tools Used
- hash-identifier - For hash type identification
- lyricspass - For generating lyrics wordlist
- John the Ripper - For hash cracking with reverse rule
- Custom reverse rule - To reverse text strings