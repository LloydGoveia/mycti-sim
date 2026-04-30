Service Cloud CTI Simulation Widget (v1.5.0)

A professional-grade simulation tool designed to test and validate Computer Telephony Integration (CTI) implementations within Service Cloud environments. This widget allows developers and administrators to simulate complex communication events across multiple channels (Call, Chat, Message, Email) without requiring a live telephony provider.

🚀 Key Features

Multi-Channel Support: Simulate Voice (Phone Call), Live Web Chat, Social Messaging (WhatsApp, Facebook, Instagram, Twitter, SMS), and Email Push.

Dynamic Payload Generation: Real-time mirroring between JSON and XML formats.

CAD Field Management: Add and manage Call Attached Data (CAD) including custom and system fields (Ticket ID, Customer ID, etc.).

Quick Controls: One-click simulations for NOTIFY (Ring), ACCEPT (Answer), and END (Hangup) events.

Transcript Templates: Save and reuse chat transcripts using integrated Cloud Storage (Firebase).

Responsive UI: Modern, dark-mode ready interface built with React and Tailwind CSS.

Guid Management: Automatic generation of unique ExternalReferenceID and RecordingID.

🛠 Tech Stack

Frontend: React (Hooks)

Styling: Tailwind CSS

Icons: Lucide-React

Backend/Storage: Firebase (Auth & Firestore)

Deployment: Single-file artifact capability

📁 Repository Structure

├── index.jsx  # Main Application Logic (React)

├── style.css # Custom CSS and Utility overrides

├── enhancements/

│   └── payloadFormatter.js # Logic for XML/JSON mirroring

└── README.md # Project Documentation


⚙️ Configuration

The widget requires a Firebase configuration to handle transcript templates. Ensure your environment provides the __firebase_config object:

const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};


📖 Usage

Simulating an Inbound Call
Select Type: Phone Call.
Select Event: Inbound.
Set ANI: Enter the caller's phone number.
Click Notify in Quick Controls to simulate a ringing event.
Click Send Payload to transmit the data to the Service Cloud parent window.
Managing Transcripts
For CHAT or MESSAGE types:
Type a transcript in the text area.
Click Save Current to store it in the cloud.
Use the dropdown to reload saved templates during testing.

📡 Payload Integration

The widget communicates with the parent window using window.parent.postMessage(). To listen for events in your application:

window.addEventListener("message", (event) => {
  // Validate origin if necessary
  const payload = typeof event.data === 'string' ? JSON.parse(event.data) : event.data;
  console.log("CTI Event Received:", payload);
}, false);


⚖️ Legal Notice

This tool is provided "AS-IS" for simulation and testing purposes. It is not an official SAP or Salesforce product. Use in production environments is at your own risk.

Developed by Lloyd Goveia
