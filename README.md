# MediTrack — tightened web starter

## Run locally
Serve this folder from localhost (for example `python -m http.server 8000`) and open `http://localhost:8000`. Web Crypto requires HTTPS or localhost.

## Security improvements in this build
- A password is required before the app opens.
- Medication records, allergy notes, and dose history are encrypted in browser storage using AES-GCM 256-bit encryption.
- The encryption key is derived from the password using PBKDF2-SHA-256 with a random salt and 310,000 iterations.
- The password is not stored or transmitted.
- Content Security Policy blocks third-party scripts, external fonts, and external connections.
- The app locks after five minutes without interaction.

## Important limitations
This is a single-device prototype, not a production-ready health-data service. The browser's local storage is encrypted by this app, but the device, browser profile, hosting environment, and user's password remain security dependencies. Anyone with access to an unlocked device/session may view data. A forgotten password cannot be reset; encrypted records cannot be recovered. Do not use real sensitive health data in this prototype.

Before public release: commission a security review; add secure server-side account management and encrypted database storage; implement account recovery carefully; protect APIs with authorization and rate limiting; configure HTTPS and security headers at the host; test backup/deletion controls and accessibility; publish a clear privacy policy and terms; obtain legal/regulatory review. Do not claim HIPAA compliance without a qualified assessment and appropriate agreements.

## Medical safety
MediTrack stores user-entered instructions. It does not recommend doses, assess drug interactions, verify allergies, or determine medication safety. Users must follow their prescription label and ask their prescriber or pharmacist questions. Browser reminders are not dependable if the page is closed or the device is offline.
