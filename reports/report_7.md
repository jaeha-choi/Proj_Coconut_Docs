# Capstone Report 7

#### Date: Nov 20, 2021

#### **Desktop**
- `client.go`
  - `Client` Structure: add use of client specific logger; implement use of the logger throughout, save current connected peer's public key hash to find peer in contact structure.
  - `Contact` Structure: remove pubkey hash and pubkey block. add path to pubkey file for encryption.
  - `commandHandler`: add support for using `UDPCommandHandler` after requesting a P2P connection.
  - `UDPCommandHandler`: similar to the `commandHandler` but looks at the current udp packet stream with functionality limited to `Quit`, `RequestPubKey`, and `File`.
  - `handleGetPubKey`: fix bug not allowing the client to write to the server. Implement writing `Pause` command to server.
  - `DoRequestPubkey`: fix bug where client would receive packets out of order.
  - `DoSendFile`: implement sending of a fully encrypted file over the UDP connection.
  - Fix other minor bugs.
#### **Server**
- `server.go`
  - `connectionHandler`: implement use of pause command pausing use of current connection in connectionHandler allowing other functions to read and write to the open connection.
  - `handleRequestPubKey`: fix bug not allowing server to read messages from seconds connection.
#### **Util**
- `util.go`
  - `ReadMessageUDP`: Reads a message from the UDP packet stream and breaks it down into a Message structure.
  - `ReadFileUDP`: implements a TCP-like reading of a file over the UDP packet stream with acknowledgment packets being sent back to the peer.
  - `WriteMessageUDP`: Creates a message structure to be sent over the UDP packet stream and writes to the writer.
  - `WriteFileUDP`: implements the breaking down of files into chunks and send them over the UDP packet stream. Waits for acknowledgment packets and resend any packets that have not been acknowledged. 
- `aes_gcm_chunks.go`
  - `EncryptUDP`: implement encryption and writing of UDP packets to UDP writer. 

### In Progress
- Implementation of fully encrypted file sharing using the peer-to-peer connection
- Implementation of peer-to-peer file sharing in the UI
- Implementation of peer-to-peer file sharing in the mobile app