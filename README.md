# Project: UDP/TCP Client-Server Communication

This project implements a UDP/TCP-based client-server communication system in Python. It is designed to support concurrent connections and efficient data transfer using both TCP and UDP protocols. The system is modular, with clear separations for packet handling, client-side functionality, and server-side operations.

## Overview

- **Client Side**: Listens for broadcast offers from the server, establishes TCP/UDP connections, and manages data transfers.
- **Server Side**: Broadcasts offers, accepts incoming client requests, and handles data transmission via TCP and UDP.
- **Packet Structure**: Encodes and decodes UDP packets for communication between the client and server.

## File Descriptions

### 1. `Client_Side.py`
This file implements the client-side logic. Key features include:
- **Listening for Broadcasts**: Uses UDP to discover available servers via Scapy or raw sockets.
- **Connection Management**: Supports multiple concurrent TCP and UDP connections.
- **Data Transfer**: Measures speed and success rates of data transfers.
- **File Size Parsing**: Converts file size inputs (e.g., `5GB`, `1024Kb`) to bits.

### 2. `Server_Side.py`
This file contains the server-side implementation. Key features include:
- **Broadcasting Offers**: Sends periodic UDP broadcasts to announce server availability.
- **Connection Handling**: Accepts and manages TCP and UDP connections concurrently.
- **Data Transmission**: Sends data chunks to clients and reports progress.
- **Cleanup**: Ensures sockets are closed properly when shutting down.

### 3. `UDP_Packet.py`
A utility module for handling UDP packets. Key features include:
- **Packet Encoding**: Converts fields (e.g., message type, magic cookie) into byte representations.
- **Packet Decoding**: Parses raw byte data into structured packet objects.
- **Packet Types**:
  - Offer: Broadcast from server to clients.
  - Request: Client request for data.
  - Payload: Server response with data chunks.

## How to Run

### Server
1. Run the server script:
   ```bash
   python Server_Side.py
2. The server will automatically determine its IP address or prompt for manual input if needed.
3. It will start broadcasting offers and listening for incoming connections.

Client
1. Run the client script:
   python Client_Side.py
2. Enter the required details:
   File size (e.g., 5GB, 1024Kb).
   Number of TCP and UDP connections.
3. The client will listen for server offers and establish connections as specified.

Features - 
  Scalable Connections: Supports multiple simultaneous TCP and UDP connections.
  Dynamic Packet Handling: Flexible encoding and decoding for various packet types.
  Performance Metrics: Tracks transfer speed and success rates.
  Cross-Network Compatibility: Works across local networks with proper IP configuration.

Dependencies - 
  Python 3.x
  Scapy: For advanced packet sniffing and filtering on the client-side.

Install dependencies using pip:
  pip install scapy

ANSI Color Codes:
  Used for better terminal readability during execution. Example:
  Green: Indicates success.
  Red: Indicates errors or failures.
  Cyan/Purple: Indicates progress updates.

Known Limitations:
  The server assumes a stable local network setup.
  UDP transmission may result in packet loss, which is reflected in the success rate.
  Client-side packet decoding may fail silently for malformed packets.

Future Enhancements:
  Implement retries for lost UDP packets.
  Add encryption for secure communication.
  Enhance error logging with detailed stack traces.

Authors:
  Avi Elbaz & Lidor Mashiah
