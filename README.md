# ProxyPilot — Official APK Releases

This **public repository** hosts Android installer APKs and the in-app update feed for ProxyPilot.

**Source code stays private** in `hassananwarul11-rgb/ProxyPilot-Android`. Never store proxy credentials, Android signing keystores, signing passwords, or GitHub access tokens here.

## Install and update

Once a stable signed release is published:

1. Open [Releases](https://github.com/hassananwarul11-rgb/ProxyPilot-Releases/releases).
2. Install the latest **signed** `ProxyPilot-*.apk` once.
3. Inside ProxyPilot, tap **Check for Updates**. The app downloads the next APK, checks its SHA-256, package identity and signing certificate, and opens the Android installer for confirmation.
4. Future signed APKs must use the **same private Android release signing key**.

**Update feed:** `https://raw.githubusercontent.com/hassananwarul11-rgb/ProxyPilot-Releases/main/latest.json`

Until signed releases are configured, `latest.json` contains `{"available": false}`, so the app must show a friendly "No stable update published" message instead of attempting a nonexistent download.

## Release format

When signed APK files have been uploaded, publish a `latest.json` object like:

```json
{
  "available": true,
  "versionCode": 4,
  "versionName": "0.1.3",
  "apkUrl": "https://github.com/hassananwarul11-rgb/ProxyPilot-Releases/releases/download/v0.1.3/ProxyPilot-0.1.3.apk",
  "sha256": "<64 lowercase hex digits of the APK, NOT the ZIP>",
  "notes": "Release notes."
}
```

A publish workflow can generate this file automatically after successfully building and verifying the signed APK. Do not publish the debug build as an updatable stable version; temporary GitHub runners may have inconsistent debug signing certificates.

**Status:** Public repository initialized; stable signing and first public APK release are **not yet configured**.
