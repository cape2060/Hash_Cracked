# Solution for Hash Cracking Challenge #8

## Hash Information
- **Hash**: `9f7376709d3fe09b389a27876834a13c6f275ed9a806d4c8df78f0ce1aad8fb343316133e810096e0999eaf1d2bca37c336e1b7726b213e001333d636e896617`
- **Hash Type**: BLAKE2
- **Cracked Password**: `hackinghackinghackinghacking`

## Solution Steps

### Step 1: Hash Identification
Used hash-identifier tool to determine the hash type:
```bash
hash-identifier
```
- Input the hash (128 hex characters)
- Result: Identified as BLAKE2 hash

### Step 2: Web Scraping with CeWL
Used CeWL tool to scrape words from a website:

```bash
cewl -d 2 -w webscrap.txt link_of_website
```

- `-d 2` - Sets the depth to 2 levels of crawling
- `-w webscrap.txt` - Outputs wordlist to webscrap.txt file
- `link_of_website` - Target website URL to scrape

### Step 3: John the Ripper Rule - repeat
Used John the Ripper's `repeat` rule to duplicate words:

```
[List.Rules:repeat]
:
d
dX0zz
dd
ddX0zz
```

This rule creates various duplications and transformations of words.

### Step 4: Cracking Command
Used John the Ripper command:

```bash
john challenge8 --rules=repeat --format=raw-blake2 --wordlist=webscrap.txt
```

### Step 5: Result
The hash was successfully cracked, revealing the password: **hackinghackinghackinghacking**

## Analysis
- The password is "hacking" repeated 4 times
- The word "hacking" was found in the webscrap.txt from web scraping
- The repeat rule transformed "hacking" into "hackinghackinghackinghacking"
- Demonstrates effectiveness of web scraping for domain-specific wordlists

## Tools Used
- hash-identifier - For hash type identification
- CeWL (Custom Word List generator) - For web scraping wordlists
- John the Ripper - For BLAKE2 hash cracking with repeat rules
- webscrap.txt - Web-scraped wordlist