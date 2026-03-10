# Keys and Secret Keys
A cryptographic key is a sequence of bits (0s and 1s) used by cryptographic algorithms to encrypt, decrypt, or authenticate data.
Keys control how the algorithm behaves. Without the key, the algorithm cannot properly encrypt or decrypt the data.

# Key size
Keys are sized in number of bits.
1- bit key size has 2 possible keys (0,1)
2- bits key size has 4 possible keys (00,01,10,11)
3-bit key size has 8 possible keys (000,001,010,011,100,101,110,111)
The formula used is n bits= 2^n possible keys

# Example of Key Length
Example of real key sizes:
56-bit used by `Data Encryption Standard` (now insecure)
128-bit/192-bit/256-bit used by `Advanced Encryption Standard`
2048-bit or 4096-bit used by `RSA`

Any cryptographic key can be discovered using a brute-force attack, where an attacker tries every possible key. However, as key size increases, the number of possible keys grows exponentially, making brute-force attacks computationally impractical.
Modern cryptographic systems rely on large key sizes to make brute-force attacks infeasible.

# Why Keys Are Used
Cryptographic systems use publicly known algorithms combined with secret keys. The security of the system depends on keeping the key secret rather than hiding the algorithm.
Keys used by these algorithms can be:
1. `Symmetric Cryptography`- Uses the same secret key for both encryption and decryption.
Example algorithms: `Advanced Encryption Standard` and `Data Encryption Standard`
2. `Asymmetric Cryptography` - Uses a pair of mathematically related keys: a public key and a private key. One key is used to encrypt data, and the other is used to decrypt it.
Example algorithm: `RSA`

