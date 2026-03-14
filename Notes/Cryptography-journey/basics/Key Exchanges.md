# Key Exchanges
`Key exchange` allows two parties to establish a `shared secret` over an unsecured medium.
`Shared secret` is a string of 1s and 0s known only by the involved parties. The `Shared secret` will be used as the `SEED Value`from which to generate symmetric secret keys.

Algorithms used for Key exchanges are: `RSA` and `DH.`

# RSA Key Exchange
`RSA` key exchange takes advantage of `RSA's` ability to encrypt and decrypt.
For the `RSA` key exchange to work;
One party must have the `RSA` asymmetric key pair. `Public key` is kept openly, and `Private Key` is kept secret.
The other party generates a random SEED value, which will later be used to generate symmetric encryption keys. 

# RSA Key Exchange Process
1. One user has an RSA key pair (Public Key and Private Key).
2. The public key is shared with the other user.
3. The other user generates a random SEED value.
4. The SEED value is encrypted using the RSA Public Key.
5. The resulting ciphertext is sent over the network.
6. Anyone listening on the network can capture the ciphertext.
7. The user who owns the RSA Private Key decrypts the ciphertext.
8. The decrypted value is the original SEED value, so both parties now share the same secret.
The shared secret (SEED) is then used to generate symmetric session keys for encryption.

# Security Limitation
The `RSA Private Key` must be kept secure forever. 
If compromised, the attacker can: Decrypt the captured ciphertext, recover the SEED value, recreate the session keys, and decrypt past communications
`RSA Key Exchange` does not provide `Forward Secrecy`

`Forward Secrecy` means that if a long-term private key is compromised, past communications sessions remain encrypted and secured.

Modern secure protocols prefer `Diffie-Hellman Key Exchange` or its variants because they provide forward secrecy.

# Deffie-Hellman Key Exchange (DH)
`DH` is a cryptographic algorithm used only for key exchange.
It allows two parties to create a shared secret over an insecure network without sending the secret directly.
1. Peers publicly agree on a mutual starting value.
2. Peers generate a private value (never shared).
3. Peers calculate a public value (shared with peer)
4. Combine the private value with the peer's public value

Note: Real Diffie-Hellman mathematics uses modular exponentiation to make it computationally hard for an attacker to determine the private values.

