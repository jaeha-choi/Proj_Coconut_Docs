# Capstone Report 4

#### Date: Sep 30, 2021


## Changes

### Implementation

#### **Mobile**
- util.dart
  - `util` package is a work-in-progress. Here is the following functions that are done.
      -  `readString`: Reads string from a reader
      -  `readNString`: Reads a binary file (images, videos, etc) 
      -  `writeString`: Writes message to writer
      -  `writeBinary`: Opens file and write byte date to sender 
      -  `createPemFile`: Creates RSAPublickey and RSAPrivateKey and save them locally
      - `encodePublicKeyToPemPKCS1`: Converts public key to PEM format string

- front_page.dart
  - `build Widget`: Builds UI part for opening page (planned to improve UI soon)

- select_page.dart
  - `getFile`: Gets any types of files (single or multiple) from mobile devices
  - `getImage`: Gets images (single or multiple) from mobile devices
  - `sendFile`: Connects to a socket and ready to deploy file  
  - `writeFileBin`: Calls `util.writeString` and `util.writeBinary` to send file

- client.dart
  - `Client`: It contains client's features
    - `serverIP`: IP address
    - `serverPort`: Port Number
    - `SecureSocket`: TCP Socket using TLS
    - `pubKeyBlock`: [String] format of public key block
    - `addCode`: [String] 6 digits of add code
    - `privKey`: [RSAPrivate] Private key
    - `Stream`: [StreamSubscription] stream method to listen data from the sever
    - `dataBuilder`: [BytesBuilder] listening message from the sever and save into `dataBuilder`
    - `isDataReady`: [Boolean] is data ready to read
  - `newClient`: Creates new Client and return `Clients`
  - `connect`: Connects to the server using [SecureSocket]
  - `onDataHelper`: Parses data from the server
  - `doGetAddCode`: Sends the command to the server and receives the addCode from the server
  - `writeBytes`: Writes message to writer 
  

## Planned
#### **Mobile**
  - `checkIPAddress`: Checks if the IP address is valid 
  - Integrate continuous integration for Flutter to automated build package, and test applications.
  -  Encryption is my next step. Our current design for encryption is to implement asymmetric encryption to exchange symmetric encryption keys, and encrypt files that are shared between clients with a symmetric encryption key.
      - For more information: https://github.com/jaeha-choi/Proj_Coconut_Docs/blob/master/reports/report_2.md
  - I tested sending and receiving the message to/from a server. However, we decided to use a different method to receive message to increase efficiency. Right now, it constantly listens messages from the server, and we want to implement the way we can start and stop listening from the server.
  - Create a button for `Receiving File`
