# Password Recovery

*- hash reversal.*

## Cracking

### Hash Extraction

- 7z:
    ```sh
    7z2john <FILE> 2> /dev/null | cut -d ';' -f 2-
    ```
- PDF:
    ```sh
    pdf2john <FILE> 2> /dev/null | cut -d ';' -f 2-
    ```
- RAR
    ```sh
    rar2john <FILE> 2> /dev/null | cut -d ';' -f 2-
    ```
- ZIP:
    ```sh
    zip2john <FILE> 2> /dev/null | cut -d ';' -f 2-
    ```

### Hash Identification

1. [Identify hash](https://hashcat.net/wiki/doku.php?id=example_hashes):
    ```sh
    hashcat --identify <HASH>
    ```
1. Benchmark hashrate:
    ```sh
    hashcat -O -b -m <HASH-TYPE>
    ```

### Hash Cracking

1. Choose crack method:
    - [Rule attack](https://hashcat.net/wiki/doku.php?id=rule_based_attack):
        | Example | Description |  Input   | Output     |
        |:--------|:------------|:---------|:-----------|
        | `:`     | Nothing.    | p@ssW0rd | p@ssW0rd   |
        | `l`     | Lowercase.  | p@ssW0rd | p@ssw0rd   |
        | `u`     | Upercase.   | p@ssW0rd | P@SSW0rd   |
        | `r`     | Reverse.    | p@ssW0rd | dr0Wss@p   |
        | `^2^1`  | Prepend.    | p@ssW0rd | 12p@ssW0rd |
        | `$1$2`  | Append.     | p@ssW0rd | p@ssW0rd12 |
        | `ss$`   | Substitute. | p@ssW0rd | p@$$W0rd   |
        ```sh
        hashcat -O -a 0 -m <HASH-TYPE> <HASH> -j ':' <WORDLIST>
        ```
    - [Combinator attack](https://hashcat.net/wiki/doku.php?id=combinator_attack):
        ```sh
        hashcat -0 -a 1 -m <HASH-TYPE> <HASH> -j ':' <WORDLIST1> -k ':' <WORDLIST2>
        ```
    - [Mask attack](https://hashcat.net/wiki/doku.php?id=mask_attack):
        | ?    | Charset    |
        |:-----|:-----------|
        | `?l` | a..z       |
        | `?u` | A..Z       |
        | `?d` | 0..9       |
        | `?s` | special    |
        | `?a` | ?l?u?d?s   |
        | `?b` | 0x00..0xff |
        ```sh
        hashcat -O -a 3 -m <HASH-TYPE> <HASH> -1 ?l?u?d -i --increment-min 1 --increment-max 8 <MASK>
        ```
    - [Hybrid attack](https://hashcat.net/wiki/doku.php?id=hybrid_attack):
        ```sh
        hashcat -O -a 6 -m <HASH-TYPE> <HASH> -j ':' <WORDLIST> -1 ?l?u?d <MASK>
        hashcat -O -a 7 -m <HASH-TYPE> <HASH> -1 ?l?u?d <MASK> -k ':' <WORDLIST>
        ```
1. View cracked hash (`~/.local/share/hashcat/hashcat.potfile`):
    ```sh
    hashcat --show -m <HASH-TYPE> <HASH>
    ```

## Resources

### Tools

- [hashcat](https://github.com/hashcat/hashcat/)
- [john](https://github.com/openwall/john/)

### Wordlists

- [SecLists](https://github.com/danielmiessler/SecLists/)
- [Weakpass](https://weakpass.com/wordlists/)
