# Symmetric Encryption

### Definition
* Also called conventional, private-key, or single-key encryption.  
* Sender and receiver share the same secret key.  
* Includes all classical ciphers and is still widely used.  
* Predates public-key cryptography (1970s).

### Basic Terminology

| Term | Meaning |
| - | - |
| Plaintext | Original readable message |
| Ciphertext | Encrypted message |
| Cipher | Algorithm: plaintext → ciphertext |
| Key | Secret shared info for encryption/decryption |
| Encryption (Encipher) | Convert plaintext → ciphertext |
| Decryption (Decipher) | Recover plaintext from ciphertext |
| Cryptography | Study of encryption methods |
| Cryptanalysis | Study of breaking ciphers without the key |
| Cryptology | Cryptography + cryptanalysis |

## Symmetric Cipher Model

### Requirements
1. Strong algorithm  
2. Secret key known only to both parties

Mathematically:
```
Y = E(K, X)
X = D(K, Y)
```
Secure key distribution is essential.

### Cryptography Types
* By operation: substitution, transposition, product (both)  
* By keys: single-key (private), two-key (public)  
* By processing: block ciphers, stream ciphers

## Cryptanalysis
Goal: recover the key (not just the message).

### Attack Types

| Type | Description |
| - | - |
| Ciphertext-only | Only ciphertext available (hardest) |
| Known-plaintext | Some plaintext–ciphertext pairs known |
| Chosen-plaintext | Attacker selects plaintext, sees ciphertext |
| Chosen-ciphertext | Attacker selects ciphertext, sees plaintext |
| Chosen-text | Combination of the above (easiest) |

## Security Concepts
* Unconditional security: unbreakable even with unlimited resources.  
* Computational security: infeasible to break in practical time.

## Brute Force Search
* Try every key; effort grows with key size.  
* Success depends on recognizing valid plaintext.

## Classical Substitution Ciphers

### Caesar Cipher
* Shift letters by fixed k (e.g., +3).
Example:
```
Plain:  meet me after the toga party
Cipher: PHHW PH DIWHU WKH WRJD SDUWB
```
Math:
```
c = (p + k) mod 26
p = (c - k) mod 26
```
Only 26 keys → easy brute-force.

## Polyalphabetic Ciphers

### Vigenère Cipher
* Multiple Caesar shifts; key repeats.
Example:
```
Key: COME → shifts (2,14,12,4)
Plain: doyouunderstand
Cipher: FCKSWIZHGFEXCBP
```
Stronger than monoalphabetic but breakable by analysis.

### Vigenère Autokey
* Key = keyword + plaintext; more complex but still vulnerable statistically.

## Monoalphabetic Cipher
* Each letter maps to a fixed random letter.
Example key:
```
Plain:  abcdefghijklmnopqrstuvwxyz
Cipher: DKVQFIBJWPESCXHTMYAUOLRGZN
```
Keyspace 26! ≈ 4×10^26, yet frequency analysis can break it.

## Language Redundancy & Cryptanalysis
* Letter frequencies are uneven (common: E, T, R, N, I, O, A, S; rare: Z, J, K, Q, X).  
* Frequency analysis exploits redundancy; developed by 9th-century Arabian cryptanalysts.

## Example Cryptanalysis
Ciphertext:
```
UZQSOVUOHXMOPVGPOZPEVSGZWSZOPFPESXUDBMETSXAIZ...
```
Using frequency and patterns yields:
```
it was disclosed yesterday that several informal...
```

## One-Time Pad (OTP)
* Security: provably secure if key is truly random, as long as message, and used once. Ciphertext gives no info about plaintext.  
* Limitations: key must be single-use, truly random, and securely distributed; best for low-bandwidth/high-security.

Encryption/decryption (bitwise XOR):
```
cipher = plaintext XOR key
plain  = cipher XOR key
```
Example (alphabet mapped to 3-bit groups):
Plain bits: 001 000 010 100 001 010 111 100 000 101  
Key bits:   111 101 110 101 111 100 000 101 110 000  
Cipher bits:110 101 100 001 110 110 111 001 110 101 → "s m l w s s p w s m"  
Decryption XORs key back to recover plaintext.

Summary:
* Provably secure if conditions met.  
* Key size = message size; distribution is the main challenge.

## Transposition Ciphers
* Rearrange letter order without changing letters; preserves frequency distribution.
* Row Transposition: write plaintext in rows under fixed column count, permute columns by key, read columns to form ciphertext.

Example (7-column key: 4 3 1 2 5 6 7):
Plaintext: "attackpostponeduntiltwoamxyz"
Grid (4 rows × 7 cols), reorder columns and read column-wise:
Ciphertext: "TTNAAPTMTSUOAODWCOIXKNLYPETZ"

Decryption: split ciphertext into column groups (by row count), place under sorted key, read row-wise.

## Product Ciphers
* Combine substitution and transposition to strengthen security.  
* Alternating types (substitution ↔ transposition) produce much harder ciphers.

## Steganography
* Hides existence of a message (not just content): e.g., subsets of letters/words, invisible ink, LSB in images/audio.  
* Drawbacks: high overhead for small data; detectable if suspected.  
* Advantage: conceals that encryption is being used; often used with encryption (encrypt, then hide).
