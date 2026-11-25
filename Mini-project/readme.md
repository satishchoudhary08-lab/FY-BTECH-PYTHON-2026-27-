# MITIn — Verified Campus Talent Portal (MIT-WPU)

**MITIn** is a dedicated campus recruitment and talent discovery platform built exclusively for **Dr. Vishwanath Karad MIT World Peace University (MIT-WPU), Pune**. It connects verified MIT-WPU engineering students with recruiters through natural-language AI search, live GitHub portfolios, end-to-end encrypted messaging, and a native Android experience.

🌐 **Live Web App:** [mitinofficial.pythonanywhere.com](https://mitinofficial.pythonanywhere.com/)

---

## Key Features

### Dual-Role Campus Ecosystem
* **Verified Student Profiles:** Students showcase their PRN, department/branch, CGPA, graduation year, skills, bio, cropped profile photo (`Cropper.js`), and live **Open to Internships** availability badge.
* **Focused Recruiter Workspace:** Recruiters explore a 100% MIT-WPU talent pool with zero outside clutter, filter candidates instantly, and initiate direct outreach.
* **Admin Dashboard:** Built-in Django Admin panel for platform oversight, user verification, and 5-star feedback analytics.

### Natural-Language AI Candidate Search
* Powered by the **Google Gemini API** (`gemini-4-hydrogen`) with a strict Python semantic fallback engine.
* Recruiters can search in plain English using multi-condition queries—such as *"AI-DS students above 8.5 CGPA knowing Python"* or *"Mechanical Engineering students open to internships"*—with strict `AND` constraint enforcement across CGPA ranges, branches, and skills.

### Live Developer Portfolios
* Moves beyond static PDF resumes by integrating directly with the **GitHub API** to display real-time repositories and project work on student profiles.

### Private End-to-End Encrypted (E2EE) Messaging
* **Client-Side Encryption (`ENCv1`):** Messages are encrypted in the browser/app before leaving the user's device, ensuring the database only stores ciphertext.
* **Consent-First Outreach:** Students approve or decline incoming recruiter chat requests before conversations open.
* **Rich Chat Controls:** Supports browser/app **Voice Notes** (`MediaRecorder` API), message editing, deletion, and silent user blocking.

### Security, Privacy & Native Android Experience
* **Multi-Layer Authentication:** Supports Email/Password and Google Sign-In, 4-digit role-based Security PINs, and optional **Native Android Fingerprint / Biometric Unlock** (`BiometricPrompt`).
* **OTP Credential Recovery:** 6-digit email verification codes via SMTP for resetting Security PINs and passwords.
* **Session Hardening:** Server-side `@never_cache` headers paired with client-side auth guards prevent back-button access to protected dashboards after logout or account deletion.
* **Adaptive Light & Dark Mode:** Seamless theme switching synchronized with native Android status and navigation bars.
* **Native Android App:** Kotlin WebView wrapper featuring custom external link handling, offline detection with reconnect UI, and locked brand typography (`Inter`).

---

## System Architecture & Tech Stack

| Layer | Technology | Responsibility |
| :--- | :--- | :--- |
| **Backend** | Python 3, Django (MVT) | Routing, JSON REST APIs, ORM models, Admin panel |
| **Database** | SQLite (`db.sqlite3`) | Student/Recruiter profiles, encrypted chats, OTPs, feedback |
| **AI Search** | Google Gemini API | Natural-language query understanding & candidate ranking |
| **Frontend** | HTML5, Tailwind CSS, JavaScript | Responsive UI, E2EE cipher, Cropper.js, Dark Mode |
| **Mobile App** | Kotlin, Android WebView, AndroidX Biometric | Native APK, Google Credential Manager, Fingerprint unlock |
| **Deployment** | PythonAnywhere | Live cloud web hosting |

---

## Core Data Models (`profiles/models.py`)

* `StudentProfile` — Stores verified student academic details, PRN, CGPA, skills, GitHub/LinkedIn links, and internship availability.
* `RecruiterProfile` — Stores recruiter work details, company name, designation, and role-level Security PIN.
* `ChatConnection` — Manages recruiter-student connection status (`pending`, `accepted`, `declined`) and silent block flags.
* `EncryptedMessage` — Stores `ENCv1` encrypted text payloads, Base64 voice notes, edit flags, and timestamps.
* `VerificationCode` — Handles time-limited 6-digit OTPs for PIN and password recovery.
* `UserFeedback` — Collects 5-star platform ratings and user reviews.

---

## Repository & Security Note

To protect real user privacy and API credentials, sensitive files—including environment secrets (`.env`), production `settings.py` keys, API credentials, and the live `db.sqlite3` database—are intentionally excluded from this public repository.

If running locally with the full source tree, configure the following environment variables in a `.env` file:

```env
DJANGO_SECRET_KEY=your_django_secret_key
GEMINI_API_KEY=your_gemini_api_key
MITIN_GMAIL_APP_PASSWORD=your_gmail_app_password
```

---

## Engineering Team

Built by First-Year **B.Tech CSE (Artificial Intelligence & Data Science)** students at **MIT World Peace University (MIT-WPU), Pune**:

* **Aishwarya Godbole** — Full-Stack Architecture, E2EE Messaging, Android App & Security
* **Tanmay** — Gemini AI Candidate Search Engine
* **Yash** — Live GitHub API Integration
* **Ayush** — UI/UX Design & Testing
* **Satish** — Documentation & Deployment