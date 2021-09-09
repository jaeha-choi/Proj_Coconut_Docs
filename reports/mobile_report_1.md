# Capstone Report #

### Date: Sep 9, 2021


### Implementation
- **util.dart**
    - `util` package is a work-in-progress. Here is the following functions that are done.
        -  `readString`: Reads string from a reader
        -  `readNString`: Reads a binary file (images, videos, etc) 
        -  `writeString`: Writes message to writer
        -  `writeBinary`: Opens file and write byte date to sender 

- **front_page.dart**
    - `build Widget`: Builds UI part for opening page (planned to improve UI soon)

- **select_page.dart**
    - `getFile`: Gets any types of files (single or multiple) from mobile devices
    - `getImage`: Gets images (single or multiple) from mobile devices
    - `sendFile`: Connects to a socket and ready to deploy file  
    - `writeFileBin`: Calls `util.writeString` and `util.writeBinary` to send file

- **Planned**
    - `checkIPAddress`: Checks if the IP address is valid 
    - Integrate continuous integration for Flutter to automated build package, and test applications.
    -  Encryption is my next step. Our current design for encryption is to implement asymmetric encryption to exchange symmetric encryption keys, and encrypt files that are shared between clients with a symmetric encryption key.
        - For more information: https://github.com/jaeha-choi/Proj_Coconut_Docs/blob/master/reports/report_2.md
    - I tested sending file to a server. However, I wasn't able to test if receiving file working properly.
    - Create a button for `Receiving File`