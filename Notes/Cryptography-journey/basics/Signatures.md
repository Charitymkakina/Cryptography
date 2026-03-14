# Signatures
A `Digital signature`is an operation that guarantees the data has not changed since it was signed.
Signatures are an asymmetric crypto Operation, meaning 2 keys are involved: one key for signing and another key for verification.
`Private Key`- used for Signing
`Public Key` - used for Verification
Signatures are computationally expensive.
Signatures provide Integrity and Authentication for what is signed.
Algorithms that can create signatures: `RSA` and `DSA.`

# RSA Signatures
The process to create and verify signatures takes advantage of RSA's ability to perform cryptographic operations with either key.

# RSA Signature Generation Process
1. Hash the data to be signed to create a digest.
2. Encrypt the digest with`RSA Private key.`
3. The result is the signature.
4. The signature is attached to the data.

# RSA Signature Verification Process
1. Separate the data and the signature.
2. Recalculate the hash on the data, providing a digest
3. Decrypt the signature with the `RSA Public Key.`
4. Compare results
NOTE: If the digests match: Data has not been modified since it was signed. Therefore, the signature is valid.
