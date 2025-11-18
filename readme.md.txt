WebRTC Peer-to-Peer Chat Application

This project is a simple, single-file WebRTC application that allows two devices on the same local network (LAN) to communicate using a peer-to-peer data connection.

It uses the PeerJS library and its public signaling server to handle the necessary WebRTC handshake (SDP and ICE exchange) automatically, making the connection a simple "Host" and "Client" process.

Prerequisites

To run this application and access it over your LAN, you must serve the HTML file using a local web server. The simplest way is using Python's built-in HTTP server.

Python: Ensure you have Python installed on the host computer (Laptop A). Python 3 is preferred.

Local Network: Both devices (Laptop A and Laptop B) must be connected to the same Wi-Fi or Ethernet network.

Setup Instructions

Step 1: File Preparation

Create a new folder for the project (e.g., webrtc-chat).

Save the webrtc_messaging_app.html file into this folder.

Step 2: Start the Web Server (On Laptop A)

The host device (Laptop A) needs to run a web server to make the file accessible to the client device (Laptop B) over the network.

Open your Terminal (or Command Prompt/PowerShell).

Navigate to the project folder (webrtc-chat).

Run the following command to start the server on port 8000:

# For Python 3
python3 -m http.server 8000

# For Python 2
# python -m SimpleHTTPServer 8000


You should see output similar to Serving HTTP on 0.0.0.0 port 8000 .... Keep this terminal window open.

Step 3: Find the Host's IP Address (On Laptop A)

The client device needs the host's IP address to connect.

Find the Host IP:

Windows: Open Command Prompt and type ipconfig. Look for the "IPv4 Address" under your active network adapter (e.g., 192.168.1.100).

Mac/Linux: Open Terminal and type ifconfig or ip a. Look for the IP address under your active network interface (e.g., en0 or wlan0).

Step 4: Access the Application (On Both Devices)

Host Access (Laptop A): Open your browser and go to:

http://localhost:8000/webrtc_messaging_app.html


Client Access (Laptop B): Open your browser and go to:

http://[Host IP Address]:8000/webrtc_messaging_app.html


(e.g., http://192.168.1.100:8000/webrtc_messaging_app.html)

Step 5: Connect the Peers

Follow these steps for a successful WebRTC connection:

Enter a Common ID: On both Laptop A and Laptop B, enter the exact same unique ID into the input box (e.g., AlphaChatDemo).

Start as Host (Laptop A):

Click "1. Start as Host (Create ID)".

The status will show Connecting. The ID will be displayed, and the host will now wait for the client.

Connect as Client (Laptop B):

Click "2. Connect to Host (Use ID)".

The client will attempt to connect to the host ID.

Connection Finalization

The WebRTC handshake (signaling) will happen automatically in the background via the PeerJS service.

When the connection is successful, the Status badge on both screens will turn Connected, and the chat input will become active. You can now send messages peer-to-peer!