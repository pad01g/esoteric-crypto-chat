# esoteric-crypto-chat

**Esoteric Crypto Chat** — distribution site (GitHub Pages).

- Web app: https://pad01g.github.io/esoteric-crypto-chat/
- OTA bundles for the Android build: `dist/`

A teaching chat app that pairs unusual cryptography (genus-2 Kummer surfaces,
imaginary quadratic class groups, SLH-DSA) with standard schemes (X25519, Ed25519)
in a hybrid construction, and shows per message how slow and how large each
algorithm is. Transport rides on public Nostr relays; there is no server of our own.
The interface is available in Japanese (default) and English.

**Teaching material only.** Secret keys are stored unencrypted on the device and the
cryptography is not constant time.

Everything here is generated and pushed by the CI of `esoteric-crypto-chat-frontend`
(private). **Do not edit by hand.** OTA bundles are signed with Ed25519 and the app
only applies bundles whose signature verifies.

```
dist/version_info-<x.y>.json   pointer to the latest bundle {"version": "...", "url": "..."}
dist/<x.y.z>/<x.y.z>.zip       build output (dist/ zipped)
dist/<x.y.z>/<x.y.z>.zip.sig   Ed25519 signature of the zip (raw, 64 bytes)
```

---

Esoteric Crypto Chat の配信先 (GitHub Pages)。root が Web 版、`dist/` が Android 版の OTA バンドル。
中身は `esoteric-crypto-chat-frontend` (private) の CI が自動生成して push する。**手で編集しない。**

標準的でない暗号 (種数2 Kummer 曲面、虚二次体の類群、SLH-DSA) を標準的な暗号
(X25519 / Ed25519) と組み合わせたハイブリッドで、実際に 1 対 1 のチャットをする教材アプリ。
1 通ごとに所要時間と大きさを表示する。表示は日本語 (既定) と英語を切り替えられる。
**教材です。** 秘密鍵は端末に平文で保存され、暗号処理は定数時間ではありません。
