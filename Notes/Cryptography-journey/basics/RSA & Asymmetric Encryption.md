# Asymmetric Encryption
Uses 2 different keys: `Public key for encryption` and `Private key for decryption.`
The purpose of `Asymmetric encryption` is that only one with the `Private key` can read the original message`(Confidentiality).`

`RSA` is the most widely used algorithm that can be used to perform `Asymmetric encryption`
`RSA` algorithm is only suitable for small and limited data sets. It is computationally expensive and inefficient for encrypting large amounts of data.
`RSA` has a mathematical property where operations using the public and private keys can be applied in either order.
`Encrypt with Public Key → Decrypt with Private Key`
`Encrypt with Private Key → Decrypt with Public Key`; however, no confidentiality as anyone can decrypt with the public key. This property can be used by another operation (Digital Signatures).

