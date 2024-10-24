# Smart Push-to-Talk (PTT) Web Application for Real-Time Class Discussions using Websockets.

## Goal: 
Design and implement a Push-to-Talk (PTT) web application using WebSockets. The application will allow multiple clients (students) to press a button to stream live audio (their voice) to a server (instructor’s machine). 

## Requirements:
1. Client-Side (Student’s Device):
- A web-based client where the student can press a button (PTT) to start streaming their voice to the server.
- Audio is captured from the device’s microphone.
- The audio stream is sent to the server using WebSockets.
- Only one student can speak at a time (First-Come-First-Served basis).
2. Server-Side (Professor’s Device):
- A web-based server that receives the audio stream from connected clients.
- The server processes and plays the audio live through the professor’s 
computer speakers.
- The server handles only one client connection at a time and streams audio 
from the client (based on who pressed the button first). For all other clients 
the connection can be rejected.
- The audio may be stored (optional), and streaming stops when the button is 
released.
3. Concurrency Control:
- Only one client (student) can speak at a time.
- If multiple clients press the PTT button at the same time, the server should 
reject the requests until the current client which is streaming stops the 
stream/connection.
4. WebSocket Integration:
- WebSockets must be used for real-time communication between clients and 
the server.
- Implement the connection setup, message passing, and stream handling over 
WebSocket protocol.

## Deliverables:
- A working web-based Push-to-Talk application with both client and server 
components.
- A report explaining the architecture, design choices, implementation, and testing.
- A short demonstration video showcasing the working application.

## Features:
- Push-to-Talk Button: Pressing and holding the button streams the audio to the 
server.
- Audio Streaming: Voice is captured from the client's microphone and transmitted via 
WebSockets.
- Concurrency Control: Only one client can stream at a time.
- Error Handling: The system should handle potential errors like multiple clients 
attempting to speak simultaneously.
- Optional: Implement a basic UI/UX design for the web application to make it 
intuitive for students to use. The UI can ask for the students name at the beginning. 
If the audio is stored at the server side, the student name with some additional serial 
number should be used as filename. 

## Suggested Architecture [You are not required to use the same architecture or sample codes]:
1. **Client-Side Architecture**:
  - Use HTML5 Web Audio API to capture microphone input.
  - Use WebSockets for streaming audio data to the server.
  - Implement a PTT (Push-to-Talk) button in the client interface to control the audio stream.

2. **Server-Side Architecture (Option A: Python)**:
  - Use the `websockets` library to create a WebSocket server in Python that listens for client connections.
  - The server will maintain a queue (FCFS model) to ensure only one client can talk at a time.
  - When a client sends an audio stream, the server will play it live using PyAudio.

3. **Server-Side Architecture (Option B: Node.js)**:
  - Use Node.js with the `ws` WebSocket library to handle WebSocket connections.
  - Use Web Audio API or native system functions to play received audio on the server side (professor’s computer).
  - Implement logic to ensure that only one client’s audio is streamed at a time.
