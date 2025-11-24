#  Image Steganography with Encrypted Hiding & Auto-Expiring Keys

##  Overview

This project is a **browser-based image steganography system** that allows users to securely hide and extract messages inside images using multiple embedding strategies including **LSB, LCG-PRNG, and SHA256-PRNG**.
All messages can be optionally protected using **AES-GCM** encryption, password-derived keys.

Everything runs fully client-side using **JavaScript + Canvas**, ensuring zero data leaves the browser.

---

##  Key Features
-  **AES-GCM Encryption** – Encrypts hidden messages before embedding into images.
-  **BMP Image Support** – Converts all uploads to 24-bit BMP format for predictable pixel manipulation.
- **Client-Side Processing** – All encoding/decoding happens in the browser, with zero server dependency.
- **Auto-Expiring Keys** – Decryption keys expire after a set duration or usage count.
- **Data Integrity Verification** – SHA-256 hashing to prevent tampering or corruption.
- **End-Marker Detection** – Accurate message retrieval without length misinterpretation.
- **Cross-Platform** – Works on any modern browser (desktop or mobile).

---

## Multiple Embedding Modes
#### 1. Plain LSB

Simple sequential LSB embedding.

#### 2. Encrypted LSB

AES-encrypted message + LSB sequential embedding.

#### 3. Encrypted LCG-PRNG

Pseudo-random embedding using Linear Congruential Generator
Deterministic positions based on password-derived seed.

#### 4. Encrypted SHA256-PRNG

Cryptographically strong PRNG using SHA-256(seed||counter)
Improved unpredictability & collision resistance.


##  Tech Stack
**Frontend:**
- HTML5 Canvas API
- JavaScript (ES6+)
- Tailwind CSS (for UI)

**Cryptography:**
- Web Crypto API (AES-GCM, SHA-256)
- PBKDF2 for key derivation

**Image Processing:**
- Custom BMP parser & pixel manipulator
- LSB encoding/decoding algorithm, LCG PRNG, SHA256 PRNG

---

##  Architecture
[User Input]
→ [AES-GCM Encryption]
→ [BMP Conversion]
→ [LSB / LCG PRNG / SHA256 PRNG Embedding]
→ [Download Encoded Image]

[Encoded Image + Key]
→ [Marker Detection]
→ [Matching Decoder]
→ [AES-GCM Decryption]
→ [Original Message Output]

## Encoding
- Upload an image (any format – auto-converted to 24-bit BMP).
- Enter your secret message.
- Set a password (used for AES-GCM encryption & key derivation).
- (Optional) Set expiry rules for the decryption key.
- Download the encoded BMP image.

## Decoding
- Upload the encoded BMP image.
- Enter the password.
- View or copy the decoded message.

## Future Enhancements
- **Progressive Web App (PWA) support** for offline usage and installation on devices.
- **Inbuilt image sharing system** for secure transmission of encoded images without third-party platforms.
- Drag-and-drop image upload for improved usability.
- Support for larger payloads through multi-image segmentation and linking.
