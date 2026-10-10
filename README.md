# esoteric-crypto-chat

**Esoteric Crypto Chat** の配信先 (GitHub Pages)。

- Web 版: https://pad01g.github.io/esoteric-crypto-chat/
- OTA バンドル (Android 版の更新): `dist/`

中身は `esoteric-crypto-chat-frontend` (private) の CI が自動生成して push する。**手で編集しない。**
配布物のうち OTA バンドルは Ed25519 で署名されており、アプリ側は署名検証に通ったバンドルしか適用しない。

```
dist/version_info-<x.y>.json   最新版のポインタ {"version": "...", "url": "..."}
dist/<x.y.z>/<x.y.z>.zip       ビルド成果物 (dist/ を zip 化したもの)
dist/<x.y.z>/<x.y.z>.zip.sig   上記の Ed25519 署名 (raw, 64 bytes)
```

## これは何か

標準的でない暗号 (種数2 Kummer 曲面、虚二次体の類群、SLH-DSA) を標準的な暗号
(X25519 / Ed25519) と組み合わせたハイブリッドで、実際に 1 対 1 のチャットをする教材アプリ。
1 通ごとに所要時間と大きさを表示する。通信は Nostr の公開リレーに相乗りし、自前サーバは無い。

**教材です。** 秘密鍵は端末に平文で保存され、暗号処理は定数時間ではありません。
