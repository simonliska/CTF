# Emdee five for life
## Description
Can you encrypt fast enough?
## Motivation
Wanted to create 1-line solution :)
## Solution
``` bash
HASH=$(curl -s -c cookie.txt http://ip_address:port/ | grep -o "<h3 align='center'>.*</h3>" | sed -n 's/<h3.*>\(.*\)<\/h3>/\1/ip;T;q') && MD5="$(echo -n "$HASH" | md5sum |awk '{print $1}' )" && curl -s -b cookie.txt -d "hash=$MD5&submit=Submit" -X POST http://ip_address:port/ | grep -o "<p align='center'>.*</p>" | sed -n 's/<p.*>\(.*\)<\/p>/\1/ip;T;q'
HTB{result}
```
## Sources
https://app.hackthebox.com/challenges/67