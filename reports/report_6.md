# Capstone Report 6

#### Date: Nov 5, 2021

## Changes

#### **Mobile**
 ## Encountered Issues ##
  - This week, we encountered issues when we tested encryption and decryption on cross platforms (mobile, desktop). This happened because Dart(mobile) and Go(desktop) were not compatible due to a different version of RSA encryption. Go supports RFC 8017 (PKCS #1 2.2) whereas pointycastle(Dart RSA package) supports RFC 2437 (PKCS #1 2.0). So, we decided to use FFI (foreign function interface). FFI uses a code written in one language to access packages/methods in a different language. In a short example, we are using Go (host language) RSA implementation, a higher version than Dart RSA, and give Dart (guest language) the ability to read and use Go's implementation. To make it work, we had to write Go implementation first and let `ffi_rsa.dart`, written in C, call Go's implementation for creating RSA keys.

- UI
  - `shared preferences`: stores the data(contact list) in a file on the device.


#### **Desktop**
- client.go
  - `commandHandler`: facilitates the reading of messages and distribution of packets into the correct correlating channel.
  - `DoRequestP2P`: Now functionally requests and receives all the data from the server necessary to initiate a holepunched peer-to-peer connection.
  - `handleRequestP2P`: Now functionally receives all data necessary as the peer to initiate a holepunched peer-to-peer connection.
  - `openHolePunchClient`: Previously `DoOpenHolePunch` now instantiates the opening of UDP listeners to open a holepunched connection with a peer. 
  - `ChanMap` has been added to the `Client` structure. This consists of a map of open networking channels. This allows for multiple threads to be operating and using networking functions at the same time.
  - Contacts now uses a map structure instead of a slice.
  - `Connect`: Now resolves IP address in the case of users entering a URL or if a DNS lookup is needed.
- client_test.go
  - Added tests for opening a holepunch and sending a file among peers

#### **Server**
- server.go
  - `handleDoRequestP2P`: Now sends all necessary information to both peers when a peer-to-peer request is initiated.
  - `connectionHandler`: Added support for `handleDoRequestP2P`

#### **Util**
  - `ReadMessage`: Replaces `readNBinary`, `readErrorCode`, `ReadString`, `ReadBytes`, `ReadBytesErr`, and `ReadBinary` by making all messages contain a nullable `Data`, `ErrorCode`, and `CommandCode`  
  - `WriteMessage`: Replaces `WriteString`, `WriteBytes`, `WriteBytesErr`, and `WriteBinary` by making all sent messages contain a nullable `Data`, `ErrorCode`, and `CommandCode`****

### In Progress

- server.go
  - Implementing a fix where the recipient client cannot write to the server during peer-to-peer initialization
