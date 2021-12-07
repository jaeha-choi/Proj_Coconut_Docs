# Capstone Report 8

#### Date: Dec 6, 2021

#### **Desktop**
- `main.go`
    - `main` fix keyPath and dataPath directory bugs and add reading of contacts file
- `client.go`
    - `CLient Structure` Add peerChan, a channel used to pause and resume the UDP command handler during peer-to-peer connections.
    - `UDPCommandHandler` Add disconnecting from peer, read deadline, nil message handling, and handling oof pause command.
    - `UDPDiscconect` Add disconnecting from peer connection.
    - `DoRequestPubkey` Add writing of new contact to contact map.
    - `DoSendFile` Fix bug causing function to not return. Add writing of pause command to peer.
    - `HandleGetFile` Add resuming of UDPCommandHandler. Write quit command to peer.
    - `OpenHolePunch` Add handling of holepunch if both peers are under the same NAT.
- `ui.go`
  - `UIStatus Structure` Add keyMap containing a map of known keys. 
  - `KeyListOrder` Remove unused date row.
  - `Start` Fix opening of keys to create new keys if not found.
  - `handleAddCodeDone` Add addition of name. Save key under *name*.key.
  - `handleShowContacts` Add showing of contacts in contacts tab.
  - `handleSendFile` Add initialization and sending of selected files to selected contacts.
  - `removeFile` Add removing of previously sent file from files list.
  - `getEntryWithID` Add function to get entry box with specified ID.
  - `getTreeViewColumnWithID` Add function to get tree view column with specified ID.
#### **Server**
- `server.go`
  - Add general bulletproofing and error handling
#### **Util**
- `util.go`
  - `ReadFilePacketUDP` Add function to read UDP packet and convert it into a `UDPMessage structure`.
  - `ReadFileUDP` Add writing of acknowledgement packets helping to ensure data is delivered successfully.
  - `WriteFileUDP` Remove threading from function. Allow for reading of acknowledgment packets.
  - `ReadAckUDP` Add general function for reading acknowledgment packets.
  - `WriteFilePacketUDP` Add function to construct and send UDP packet.
- `aes_gcm_chunks.go`
  - `EncryptFileUDP` Add function to encrypt and send UDP file packets to peer.
  - `DecryptFileUDP` Add function to receive and decrypt file packets from peer.
 
### In Progress
- Creating poster and abstract to be reviewed and submitted.
- Fixing bugs in client.
- Bulletproofing demo to be shown during presentation.