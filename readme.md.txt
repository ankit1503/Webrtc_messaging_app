WebRTC Peer-to-Peer Chat and Screen Share (Firewall-Safe Manual Signaling)

This version of the WebRTC application is designed to bypass office firewalls and proxies that block external signaling servers. It uses Manual Signaling (copy/paste) for connection setup.

Why this version works in the office:

No External Server Dependency: The previous version failed because the firewall blocked the connection to the public PeerJS server. This version requires zero external connections during the critical signaling phase, ensuring the connection is established purely over your LAN.

Simple Deployment: You still only need to serve the single HTML file over HTTP.

Prerequisites

Python: Installed on the host computer (Laptop A) to run the HTTP server.

Local Network: Both devices must be on the same LAN (Wi-Fi or Ethernet).

Setup Instructions

Step 1: File Preparation & Server Start

Create a new folder and save the webrtc_manual_signaling.html file inside it.

On Laptop A (Host): Open your terminal, navigate to the folder, and start the server:

python3 -m http.server 8000


Access on Both Laptops:

Laptop A: http://localhost:8000/webrtc_manual_signaling.html

Laptop B: http://[Laptop A's IP Address]:8000/webrtc_manual_signaling.html

Step 2: Manual Signaling (The Only Way to Fix CORS/Firewall Issues)

Follow these steps precisely to establish the connection:

Step

Laptop A (Offerer)

Laptop B (Answerer)

1. Offer

Click "1. Create Offer". Copy the JSON from the SDP Input box.

N/A

2. Answer

N/A

Paste Offer into SDP Input. Click "3. Set Offer & Create Answer". Copy the resulting Answer JSON from the SDP Input.

3. Finalize SDP

Paste Answer into SDP Input. Click "2. Set Answer".

N/A

4. Exchange ICE

Copy all JSON from Laptop A's ICE Candidates box.

Paste into Laptop B's ICE Candidates box. Click "4. Add ICE Candidates".

5. Finalize ICE

Copy all JSON from Laptop B's ICE Candidates box (which now contains both sets).

Paste into Laptop A's ICE Candidates box. Click "4. Add ICE Candidates".

Step 3: Screen Sharing

Once the Status shows Connected on both devices:

To Share: The device that wants to share its screen clicks the "Start Screen Share" button. The browser will prompt for screen selection.

To View: The remote device will automatically start displaying the shared screen in the black video area.

To Stop: Click "Stop Sharing".
Important Note: If you start or stop screen sharing, the connection data changes. If the connection fails after a share, repeat Step 2 (exchange SDP/ICE again) to re-establish the link.
