
# 🦩 Flamingo Pay – Technical Documentation

**Version:** 1.0  
**Maintainer:** SahanTech Solutions  
**Contact:** jebrildomenico@gmail.com

---

## 📌 Overview

**Flamingo Pay** is a **voice-first Unified Payment Interface (UPI)** app that empowers **visually impaired and digitally excluded users** to access and control their finances through **spoken commands**, **secure eKYC onboarding**, and **multilingual accessibility**.

Flamingo is built in Ethiopia for Africa — focused on dignity, access, and inclusion.

---

## 🧱 System Architecture

```text
Flutter Mobile App
    ↕︎
Google Cloud Speech-to-Text (STT)
Google Cloud Text-to-Speech (TTS)
    ↕︎
Backend API (Node.js + Express)
    ↕︎
UPI Engine (custom logic + EthSwitch gateway)
    ↕︎
Database (MongoDB Atlas)
    ↕︎
eKYC Engine (OCR, voice biometric, liveness)
```

---

## 🧠 Core Modules & Technologies

### 🎙️ 1. Voice Interaction (No Screen Required)
- **Google Cloud Speech-to-Text** – Processes user voice commands
- **Google Cloud Text-to-Speech** – Reads system responses aloud
- **Flutter** – Front-end built with cross-platform UI toolkit
- **Amharic + English** – Language selection via voice

### 🔐 2. Authentication & eKYC
- **Voice PIN** – Spoken numeric PIN used to log in
- **Voice Biometrics** – Used to confirm user identity
- **eKYC Document Capture** – Via phone camera
- **OCR** – Custom backend with Tesseract.js for ID scanning
- **Liveness Check** – Randomized voice phrase matching

### 💸 3. UPI Transaction Engine
- Built in **Node.js (Express)**
- Handles:
  - `check_balance`
  - `send_money`
  - `transaction_history`
- Future-ready integration with **EthSwitch API**

---

## 🔐 Security Stack

| Layer | Tool |
|-------|------|
| HTTPS | TLS 1.3 via Nginx Reverse Proxy |
| Data encryption | AES-256 for at-rest, TLS for in-transit |
| Auth | JWT Tokens (signed + expiring) |
| Biometric Handling | Stored as encrypted voice hash |
| Logging | Winston logger + audit trail per transaction |

---

## 📊 API Overview

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/login` | POST | Authenticate via voice PIN |
| `/api/balance` | GET | Voice-commanded balance check |
| `/api/send` | POST | Voice-triggered money transfer |
| `/api/ekyc` | POST | Upload ID + voice sample |
| `/api/history` | GET | Get spoken list of past transactions |

---

## 🧪 Example Voice Flow

```
User: "Log in"
System: "Say your voice PIN"
User: "One two three four"
✅ Authenticated

User: "Check balance"
System: "Your current balance is 3,200 birr."

User: "Send 200 birr to Amina"
System: "Confirm sending 200 birr to Amina Yusuf?"
User: "Yes"
✅ Transfer completed
```

---

## 🛠️ Development Stack

| Component | Tech Used |
|-----------|-----------|
| Front-End | Flutter |
| Backend | Node.js (Express.js) |
| Voice Engine | Google Cloud STT & TTS |
| Database | MongoDB Atlas |
| Hosting | DeployPad Cloud + Nginx |
| CI/CD | GitHub Actions |
| DevOps | Docker + PM2 |
| Monitoring | Sentry (mobile), basic logs backend |

---

## 🌍 Accessibility & Inclusion

- Built with **WCAG 2.1** in mind
- Voice-only mode for full app flow
- High-contrast, text-scaling UI fallback
- Voice guidance for every screen
- Amharic + English dynamic support
- USSD/IVR fallback in roadmap (for feature phones)

---

## 🧾 Database Schema (Simplified)

### `users`
| Field | Type |
|-------|------|
| _id | ObjectId |
| name | String |
| phone | String |
| voice_pin_hash | String |
| voice_biometric_hash | String |
| language | Enum (am/eng) |
| ekyc_status | Enum (pending/verified/rejected) |

### `transactions`
| Field | Type |
|-------|------|
| _id | ObjectId |
| sender_id | ObjectId |
| recipient_id | ObjectId |
| amount | Number |
| timestamp | ISODate |
| status | Enum |

---

## 🔌 Integrations

- 🔊 **Google Cloud Speech & TTS** – Real-time speech interface
- 🔐 **EthSwitch (Planned)** – UPI connection
- 🧠 **Tesseract.js (OCR)** – For local ID recognition
- 📡 **DeployPad Hosting** – Secure deployment platform

---

## 👥 Roles & Permissions

- **User**: Perform voice transactions
- **Compliance Officer**: Review KYC entries
- **Admin**: Manage user logs, audit access

---

## 📬 Contact

**Maintained by**: SahanTech Solutions  
**Founder**: Dr. Jibril Mohamed Ahmed  
📧 jebrildomenico@gmail.com  
📞 +251 937 099 779  
🔗 [LinkedIn](https://linkedin.com/in/jibril-mohamed-ahmed)

---

> 🦩 *“Flamingo started with one blind father.  
Now it belongs to everyone the system left behind.”*
