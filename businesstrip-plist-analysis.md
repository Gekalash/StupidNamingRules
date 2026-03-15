# Analysis: BusinessTrip OTA Plist

**Date:** 2026-03-15
**Source URL:** `https://a.t-bnk.ru/r/6757154572/baff3252aeb32328dc0d0b3d3f1587aaf90945cf12ce8bc864c2d419cbac892a.plist`

---

## What this actually is

This is a **real App Store app** (App Store Item ID `6757154572`) that has been **downloaded from the App Store and redistributed via OTA (Over-the-Air installation)** — bypassing Apple's normal distribution entirely.

---

## How OTA Installation Works

Opening the link on an iPhone triggers the following redirect chain:

```
https://a.t-bnk.ru/r/... → itms-services://?action=download-manifest&url=https://download.cdn.srv-hub.org/...plist
```

- The first URL is a **tracker/redirect link** (note `/r/` path + user ID `6757154572`)
- It redirects to the `itms-services://` protocol, handled natively by iOS
- iOS fetches the `.plist` manifest and offers to install the app described in it
- iOS then downloads and installs the `.ipa` from the URL in the manifest

---

## The Manifest Plist

```xml
<key>bundle-identifier</key> <string>com.tatsiana.khamichonak.trip</string>
<key>bundle-version</key>    <string>1.0</string>
<key>title</key>             <string>BusinessTrip</string>
<key>url</key>               <string>https://download.cdn.srv-hub.org/ipas/6757154572/baff3252aeb32328dc0d0b3d3f1587aaf90945cf12ce8bc864c2d419cbac892a.ipa</string>
```

---

## Key Discrepancies

| Field | Plist claims | Actual metadata |
|---|---|---|
| Title | `BusinessTrip` | `TouchT` / `Business Touch Trip` |
| Version | `1.0` | `1.17.1` (build 2) |

The plist is **misrepresenting the app name and version** to appear innocuous.

---

## What We Know About the App

| Field | Value |
|---|---|
| Real name | `TouchT` / `Business Touch Trip` |
| Bundle ID | `com.tatsiana.khamichonak.trip` |
| Listed developer | `Aleksandr Pridacha` |
| Developer email | `vawgrfmoqy038@outlook.com` |
| App Store Item ID | `6757154572` |
| Release date | 2026-01-03 |
| Category | Business |
| Version history | 4 external version identifiers (actively maintained) |
| Rating descriptor | *"User or Machine Generated Content and Messaging and Chat"* |

**Notable:** The bundle ID is registered under a different person's name ("Tatsiana Khamichonak") than the listed developer ("Aleksandr Pridacha"), suggesting multiple identities were used in development/registration.

---

## Why Distribute an App Store App via OTA?

1. The app was **removed from the App Store** (policy violations, fraud reports, Apple review action)
2. To **reach users in regions where it's geo-restricted**
3. To avoid Apple's tracking of who downloads and installs it

---

## Conclusion

This is a previously App Store-listed app, now being kept alive via covert OTA distribution using a tracked redirect link. The combination of factors below strongly suggests this is a **scam or fraud app** — likely a fake business/banking tool used for credential harvesting — that was pulled from the App Store and is now being distributed to specific targets via individually tracked links:

- Mismatched app name between plist and actual metadata (deliberate obfuscation)
- Random-looking generated developer email address
- Bundle ID registered to a different person than the listed developer
- Chat/messaging capabilities (`itms-games` rating system, messaging descriptor)
- Distribution via a redirect tracker with an embedded target user ID
- Hosted on `srv-hub.org` (not an official Apple or known enterprise domain)
