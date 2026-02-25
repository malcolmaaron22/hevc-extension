# Install HEVC Codec on Windows 11 via GitHub (No Microsoft Store)

This method installs the **official Microsoft HEVC Video Extension** using a Microsoft‑signed APPX package hosted on GitHub. It is suitable for **offline, enterprise, or restricted environments** where Microsoft Store access is limited or disabled.

---

## ✅ What This Enables

- Native playback of **HEVC (H.265) videos** in Windows Media Player and Movies & TV
- Required decoding support for **HEIC images** (when used together with HEIF Image Extension)
- Explorer thumbnails and Photos app support

---

## 📦 Prerequisites

- Windows 11 (x64)
- PowerShell

---

## 📥 Step 1: Download the HEVC APPX Package

GitHub repository:

https://github.com/ngkoi/hevc-extension

Download the following file:
click code, then download zip

```
Microsoft.HEVCVideoExtension_1.0.40203.0_x64__8wekyb3d8bbwe.Appx
```

> ℹ️ This is a **Microsoft‑signed** package identical to the Microsoft Store version.

---

## ⚙️ Step 2: Install Using PowerShell

1. Open PowerShell
2. Navigate to the folder containing the downloaded APPX file
    *
    Then run this:
    ```powershell
    cd C:\Users\Mekem\Downloads\hevc-extension-main\hevc-extension-main
    ```
    Your Powershell should have changed its path to the copied path
3. Run:

```powershell
Add-AppxPackage -Path "Microsoft.HEVCVideoExtension_1.0.40203.0_x64__8wekyb3d8bbwe.Appx"
```

---

## 🔍 Step 3: Verify Installation

Run:

```powershell
Get-AppxPackage | Where-Object {$_.Name -like "*HEVC*"}
```

Expected output includes:

```
Name   : Microsoft.HEVCVideoExtension
Status : Ok
Publisher : Microsoft Corporation
```

---

## ⚠️ Important Note for HEIC Images

HEIC image support requires **both**:

- ✅ HEVC Video Extension (this step)
- ⬜ HEIF Image Extension (install separately if missing)

To check HEIF:

```powershell
Get-AppxPackage | Where-Object {$_.Name -like "*HEIF*"}
```

---

## 🔄 Final Step: Restart Explorer

Explorer caches codecs. Restart it to enable thumbnails:

```powershell
taskkill /f /im explorer.exe
start explorer.exe
```

---

## ✅ Result

After completing these steps:

- HEVC (H.265) videos play natively in Windows apps
- HEIC images open correctly in Photos (with HEIF installed)
- Explorer thumbnails are enabled

---

## 📌 Use Cases

- Enterprise / corporate Windows images
- Offline or air‑gapped systems
- Devices with Microsoft Store disabled

---

**Document maintained for internal deployment and troubleshooting.**
