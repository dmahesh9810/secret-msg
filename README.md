# 🔐 CYBER•STEGO — Advanced LSB Steganography Engine

A modern, cyber-themed, fully client-side Steganography Web Application built with **HTML5 Canvas**, **Tailwind CSS**, and **Vanilla JavaScript**. 

Conceal confidential messages within image pixels using **Least Significant Bit (LSB)** steganography with optional **PBKDF2 + HMAC-SHA256 authenticated encryption** and strict lossless PNG export.

![Cyber Stego Preview](https://img.shields.io/badge/Security-LSB%20Steganography-00f0ff?style=for-the-badge&logo=security)
![JavaScript](https://img.shields.io/badge/JavaScript-Vanilla%20ES6+-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![TailwindCSS](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)
![Client-Side](https://img.shields.io/badge/Privacy-100%25%20Client--Side-00ff9d?style=for-the-badge)

---

## ⚡ Key Features

- **Cyber-Themed Dark Mode UI:** High-tech cyberpunk aesthetic with neon cyan and matrix green glowing accents, live status badges, and smooth tab switching.
- **Tab 1: Hide Message (Encode):**
  - Drag-and-drop or click to upload cover images (PNG, JPG, BMP, WebP).
  - Built-in **"Use Sample Cover"** button to generate a 900×600 procedural cyber canvas cover with 1 click.
  - Live resolution calculation ($W \times H$), available pixels, and maximum secret character capacity meter.
  - Real-time payload capacity tracking progress bar.
  - Optional **Stego Password / Key** for military-grade PBKDF2 & HMAC-SHA256 authenticated stream cipher protection.
  - One-click **"Encode & Download Stego PNG"** strictly downloading lossless PNG.
  - Instant handoff button to immediately test revelation in the Decode tab.
- **Tab 2: Reveal Message (Decode):**
  - Drag-and-drop or click to upload the Stego PNG.
  - Automatic warning if a lossy JPEG image is accidentally uploaded.
  - Optional password input for encrypted stego files.
  - Decrypted Payload Terminal with word/character counts, verified key status badges, **Copy to Clipboard**, and **Save as .txt**.
- **100% Client-Side:** No external servers, no cloud APIs, zero data leaves your browser.

---

## 🔬 How LSB Steganography Works

1. **32-Bit Length Header:** The first 32 bits across the RGB pixel channels store a 32-bit unsigned integer $L$ representing the payload byte length. The decoder reads this in microseconds and stops scanning once the exact message length has been retrieved.
2. **RGB 3-Channel Embedding:**
   - $\text{Red Channel LSB} \rightarrow \text{Bit } 0$
   - $\text{Green Channel LSB} \rightarrow \text{Bit } 1$
   - $\text{Blue Channel LSB} \rightarrow \text{Bit } 2$
   - $\text{Alpha Channel} \rightarrow \text{Fixed at } 255$ (untouched to eliminate browser canvas alpha-premultiplication artifacts).
3. **Lossless PNG:** JPEG and WebP apply lossy discrete cosine transform compression that alters pixel values and corrupts LSB bits. Lossless PNG preserves raw RGBA scanlines with 100% fidelity.

---

## 🚀 Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/dmahesh9810/secret-msg.git
   ```
2. Open `index.html` in any modern web browser (Chrome, Edge, Firefox, Safari):
   - No installation, Node.js, or local server required.
   - Simply double-click `index.html`!

### Deploying to GitHub Pages (Free Instant Hosting)
1. In your GitHub repository, go to **Settings** > **Pages**.
2. Under **Build and deployment** > **Branch**, select `main` and root `/`.
3. Click **Save**. Your steganography tool will be live at `https://dmahesh9810.github.io/secret-msg/`!

---

## 🛡️ Cryptographic Specification

| Component | Standard / Algorithm |
| :--- | :--- |
| **Key Derivation** | PBKDF2-HMAC-SHA256 (800 iterations) |
| **Salt** | 16-byte cryptographically secure random salt |
| **Keystream** | HMAC-SHA256 Counter (CTR) Mode |
| **Authentication Tag** | 16-byte HMAC-SHA256 tag (constant-time verification) |
| **Bit Embedding** | LSB on RGB channels, Big-Endian Network Byte Order |

---

## 📄 License
This project is open source and available under the [MIT License](LICENSE).
