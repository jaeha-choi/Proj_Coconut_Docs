# Capstone Report 2

#### Date: Jul 10, 2021

## Changes

### Environment Setup
- **Code Coverage Page**
    - Desktop: https://app.codecov.io/gh/jaeha-choi/Proj_Coconut_Desktop

### Design
- Encryption: Current plan is to implement asymmetric encryption to exchange symmetric encryption keys, and encrypt files that are shared between clients with a symmetric encryption key. This design allows us to achieve end-to-end encryption, which means no one else (including the server) other than both clients can access the file.

### Implementation
- **Utility**
  - `log` package is complete
  - `util` package is a work-in-progress. The following functions are done, but we may need to revise the following functions as we're making changes to the design (specifically the encryption).
    - `ReadString`: Reads string from a reader
    - `ReadBinary`: Reads a binary file (images, videos, etc) from remote and save it locally
    - `WriteString`: Writes string to writer
      - Found a bug which seems to be related to carriage return. Windows handles carriage returns differently, so we may need to convert them to fix this issue.
    - `WriteBinary`: Reads a binary file (images, videos, etc) from local and write it to remote writer

- **Desktop**
  - `client` contains methods for encryptions. (Will be moved to `Utility` project once encryption implementation is complete)
    - The following functions are done:
      - `PemToSha256`: Generates sha256sum of the public key to use it as an ID when connected to the server
      - `BytesToBase64`: Encode raw byte slices to base64 byte slices 

    - The following functions are done, but requires more testing:
      - `createRSAKey`: Helper function for `OpenKeys` to create keys
      - `OpenKeys`: Open an asymmetrical encryption key pair in PEM block format or create one if not found
      - `PemToKeys`: Convert PEM blocks to key pairs
      - `genSymKey`: Generates asymmetrical encryption key pair (private/public key)
      - `encryptSignSymKey`: Encrypts symmetric encryption keys with asymmetric key pair to implement hybrid encryption
      - `decryptVerifySymKey`: Decrypts symmetric encryption keys with asymmetric key pair to implement hybrid encryption

## Planned
- Encryption (Client-Server): Instead of using raw TCP, we are considering TLS.
- GUI (Client): `GTK` toolkit will be used for GUI. If we choose `AGPL` for our license, we might consider `qt` instead.
- License: `AGPL` or `ISC` licenses are being considered.

## Encountered Issues
- We have noticed some of the issues while implementing some encryption functions, such as some built-in functions lacking support for stream interfaces which is necessary for large files.
- Features requiring encryption implementation by non-cryptographer can be questionable, but I am trying my best to follow the standard encryption procedure. I (Jaeha Choi) am not a cryptographer nor have learned these in any of the classes that I've taken, so it's taking longer than expected to implement functions that use encryption.
- Number of required unit tests is quite overwhelming.