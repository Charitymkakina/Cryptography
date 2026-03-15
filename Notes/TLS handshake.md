# key Players
`Client`- Initiates the TLS handshake. Example Web Browser (Google Chrome)

`Server`- Receives the TLS handshake. Example Webserver (Apache)

`Certificate Authority`- Governing authority that issues certificates trusted by a client and server. Provides a trust anchor.

# THE TLS HANDSHAKE
# Client Hello
The handshake starts when the client sends a ClientHello message to the server.
The message includes;
   1. `TLS version supported by the client.`
   2. `Client random used later to generate encryption keys.`
   3. `Session ID used for session resumption.`
   4. `Cipher suites the client supports.`
   5. `Extensions.`

The message basically says: Here are the encryption methods I support; choose one.

# Server Hello
The server responds with a ServerHello.
The server chooses security parameters and sends;
 1. `The TLS version selected.`
 2. `Server Random.`
 3. `Session ID.`
 4. `Chosen Cipher suite.`
 5. `Extensions.`

This message means: I selected this encryption method for our communication.

# Server Sends Certificates
The server then sends its digital certificate. The certificate contains;
1. `server identity.`
2. `The public key.`

# Server Hello Done
After sending the certificate, the server sends: `ServerHelloDone.`
Indicating that the server has finished sending the handshake messages
Some handshake variants, such as `ServerKeyExchange`  and  `CertificateRequest`, may also be sent depending on the cipher suite.

NOTE: After receiving the certificate from the server, the client asks the following questions;
    Is the certificate valid? which is validated by using the Certificate Authority's (CA's) public key
    Does the Domain match? This is validated by checking the domain name in the certificate.

# Client Key Exchange
Proves the server is the true owner of the certificate and establishes mutual keying material (SEED value)
Now the client generates a `Premaster Secret`.
The client encrypts this secret using the server's public key(the client has the public key because the server sent its certificate) and sends it to the server.
Only the server can decrypt it because the server has the private key. The premaster Secret will be the SEED value from which additional session keys
from the session will be calculated.

# Session Key Generation
Both sides now have the `client random`, `server random`, and the `Premaster secret`. These 3 items derive the `Master secret key.`
The `Master secret key`, combined with `Key expansion`, `Client random`, and `Server random`, generates 2 sets of session keys.
The session keys are `symmetric encryption keys`. They include:
  1. `Client Encryption Key`- Used by the client to encrypt data sent to the server.
      
      `Client HMAC KEY` - Used to ensure the integrity of data sent by the client.
    
  2. `Server Encryption Key`- Used by the server to encrypt data sent to the client.
     
     `Server HMAC key`- Used to ensure the integrity of data sent by the server.

Why 2 sets of keys?
  - Traffic can be protected independently.
  - Cryptographic attacks become harder.

# Change Cipher Spec
The Client sends: `ChangeCipherSpec.`
meaning: From now on, we will use encrypted communication.

# Finished Message
The client sends a finished message encrypted with a new session key. The server then responds with its own.
server's response: `ChangeCipherSpec`
                   `Finished`
Once this is complete, the handshake is done.


