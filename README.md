# esoteric-crypto-chat

> 日本語: [README.ja.md](README.ja.md)

**Esoteric Crypto Chat** — distribution site (GitHub Pages).

- Web app: https://pad01g.github.io/esoteric-crypto-chat/
- OTA bundles for the Android build: `dist/`
- Android (F-Droid): listed in the self-hosted repository `pad01g's apps`
  (https://pad01g.github.io/wordquiz-fdroid/)

## What it is

A teaching chat app that pairs unusual cryptography with standard schemes in a hybrid
construction and shows, per message, how slow and how large each algorithm is:

| Key type | Key exchange | Signatures |
|---|---|---|
| Genus-2 curve | Gaudry–Schost Kummer surface + X25519 | qDSA + Ed25519 |
| Imaginary quadratic class group | class group DH (1827-bit discriminant) + X25519 | Schnorr in a group of unknown order + Ed25519 |
| SLH-DSA | X25519 | SLH-DSA-SHA2-128s + Ed25519 |

Transport rides on public Nostr relays; there is no server of our own. Key exchange is an
explicit hello/ack round trip with ephemeral keys on both sides; nothing is sent before it
completes. The interface is available in Japanese (default) and English.

**Teaching material only.** Secret keys are stored unencrypted on the device and the
cryptography is not constant time. Do not use it for anything that needs real secrecy.

## How to try it

1. Open the web app on two devices (or two browsers) and create a key bundle of the same key
   type on each. Bundles are published to relays automatically.
2. On one device, show the contact string / QR code of the bundle. On the other, "Add contact"
   and paste or scan it.
3. Opening the chat starts the key exchange. Once it completes, send a message and expand
   "Breakdown" to see the cost of each algorithm.

## Contents of this repository

Everything here is generated and pushed by the CI of `esoteric-crypto-chat-frontend`
(private). **Do not edit by hand.** OTA bundles are signed with Ed25519 and the app only applies
bundles whose signature verifies.

```
index.html, assets/            the web app
build.json                     build id, used by open tabs to notice a newer build
dist/version_info-<x.y>.json   pointer to the latest OTA bundle {"version": "...", "url": "..."}
dist/<x.y.z>/<x.y.z>.zip       build output (dist/ zipped)
dist/<x.y.z>/<x.y.z>.zip.sig   Ed25519 signature of the zip (raw, 64 bytes)
```

## References

- Bos, Costello, Hisil, Lauter. Fast Cryptography in Genus 2. eprint 2012/670
- Renes, Smith. qDSA: Small and Secure Digital Signatures with Curve-based Diffie–Hellman Key Pairs. eprint 2017/518
- Buchmann, Williams. A key-exchange system based on imaginary quadratic fields. 1988
- FIPS 205 (SLH-DSA)
