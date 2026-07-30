# TFTP (Trivial File Transfer Protocol) using C

## Overview

This project implements the Trivial File Transfer Protocol (TFTP) using the C programming language on Linux. It follows a client-server architecture and uses UDP sockets for communication.

The application supports reliable file transfer through acknowledgements (ACKs), packet retransmission, and multiple transfer modes similar to the TFTP protocol.

---

## Features

- UDP Socket Communication
- Client-Server Architecture
- File Upload (PUT)
- File Download (GET)
- ACK-based Reliable Data Transfer
- Packet Retransmission
- Multiple Transfer Modes
  - Normal Mode
  - Octal Mode
  - NetASCII Mode
- IP Address Validation
- Linux System Calls
- Error Handling

---

## Technologies Used

- C Programming
- Linux
- UDP Socket Programming
- POSIX System Calls
- GCC Compiler

---

## Project Structure

```
.
├── client.c
├── server.c
├── README.md
├── sample_input_files/
└── sample_output_files/
```

---

## Working

### Client

- Connects to server using IP address and Port Number
- Uploads files to server (PUT)
- Downloads files from server (GET)
- Allows user to select transfer mode
- Waits for ACK after every packet

### Server

- Receives client requests
- Creates or opens requested files
- Sends file contents
- Receives uploaded files
- Sends acknowledgement after every packet

---

## Supported Operations

### PUT

Transfers a file from Client to Server.

Flow:

```
Client
   |
Connect
   |
Send Filename
   |
Send Data Packet
   |
Wait for ACK
   |
Next Packet
   |
EOF
```

---

### GET

Transfers a file from Server to Client.

Flow:

```
Client Request
      |
Server Opens File
      |
Send Packet
      |
Client Sends ACK
      |
Next Packet
      |
EOF
```

---

## Transfer Modes

### Normal Mode

Transfers data in blocks of 512 bytes.

### Octal Mode

Transfers data byte-by-byte.

### NetASCII Mode

Transfers text data while handling ASCII formatting.

---

## Linux System Calls Used

- socket()
- bind()
- sendto()
- recvfrom()
- open()
- read()
- write()
- close()

---

## Reliability

Since UDP does not guarantee delivery, this implementation provides reliability by

- ACK mechanism
- Packet retransmission
- EOF indication
- File validation

---

## How to Compile

### Server

```bash
gcc server.c -o server
```

### Client

```bash
gcc client.c -o client
```

---

## Run

### Start Server

```bash
./server
```

### Start Client

```bash
./client
```

---

## Sample Menu

```
========== TFTP CLIENT ==========
1. Connect
2. Put
3. Get
4. Mode
5. Exit
```

---

## Learning Outcomes

Through this project I learned

- UDP Socket Programming
- Client-Server Architecture
- File Transfer Protocols
- Reliable communication over UDP
- Linux Networking APIs
- Linux File System APIs
- Error Handling
- Network Programming Fundamentals

---

## Future Improvements

- Timeout using select()
- Multi-client support
- Thread-based server
- Sliding Window Protocol
- CRC Error Detection
- Authentication
