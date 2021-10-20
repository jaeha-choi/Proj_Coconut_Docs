# Capstone Report 4

#### Date: Sep 30, 2021


## Changes

### Implementation

#### **Mobile**
- util.dart
    - 
- aes_gcm_encryption.dart
    - `encryptSetup` : Opens file using file path and determines number of chunks.
    
    - `decryptSetup` : Creates temporary file to store decrypted file.

    - `encrypt` : Encrypts file with receiver's pub key and sign with senders' private key.

    - `_encryptChunk`, `_encryptBytes` : Helper function for `encrypt`.

    - `_decryptChunk`, `_decryptBytes` : Helper function for `decrypt`.
    
    - `decrypt` : Decrypts encrypted data from connection. Receiver's private key is required to decrypt symmetric encryption key.

    - `close` : closes the file.


- front_page.dart
    **Key Features**
    - BottomNavigationBarItem - Creates the bottom taps(Contacts, Photos, Files) to switch the tap

    - IndexedStack - Holds a stack of widget but shows only one at a time. All the state is preserved. Example case: user types other user name and switch to different tap and came back to tap again. It still saves the previously entered text

- contacts_page.dart
    - **Please look at the bottom image**
    - Added feature that prevents multiple clicks on button
<p align="middle">
  <img src="imgs/add_contacts.png" width="300"/>
  <img src="imgs/contacts_page.png" width="300"/>
</p>

- phots_page.dart
    - **Please look at the bottom image**
<p align="middle">
  <img src="imgs/photos_page.png" width="300"/>
</p>



- files_page.dart
    - **Please look at the bottom image**
<p align="middle">
  <img src="imgs/files_page.png" width="300"/>
</p>








