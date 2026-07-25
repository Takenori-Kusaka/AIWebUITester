# ADR-0001: テスト対象ブラウザの制御方式 — ver1.0.0 は Playwright サイドカー並走

- Status: Accepted
- Date: 2026-07-25

## Context

本ツールの中核は「AI と人間が同じ画面を見ながらテスト対象 Web UI を操作・記録・レビューする」体験であり、操作記録・スクリーンショット・ネットワーク(HAR)収集・GIF 生成には CDP (Chrome DevTools Protocol) 相当の制御が必要。アプリ本体は Tauri 2 + TypeScript(QuickScribe と同系)を採用予定。

テスト対象の表示方式は2案ある。

### 案A: Tauri ウィンドウ内に埋め込み

Tauri 2 の multiwebview(`unstable` feature)で外部サイト用の子 webview を同一ウィンドウに配置する。Windows では WebView2 に `--remote-debugging-port` を渡すことで CDP が有効になり、Playwright の `connectOverCDP` で制御可能(実証例: [Haprog/tauri-cdp](https://github.com/Haprog/tauri-cdp), [Playwright WebView2 docs](https://playwright.dev/docs/webview2))。

- 難点1: multiwebview は unstable であり、描画([#11376](https://github.com/tauri-apps/tauri/issues/11376))・配置([#10420](https://github.com/tauri-apps/tauri/issues/10420))・リサイズ([#10131](https://github.com/tauri-apps/tauri/issues/10131))のバグ報告が継続している(2026-07 時点)
- 難点2: CDP は WebView2(Windows)限定。macOS の WKWebView では使えず、クロスプラットフォーム化を阻む

### 案B: Playwright サイドカー並走

Playwright がサイドカーとして実 Chromium を別ウィンドウで起動し、Tauri アプリはテストチャート・操作/レビューモード・AI チャット・レポート生成のコントロールパネルに徹する。

- 記録系(操作ログ / スクショ / HAR / video→GIF)は Playwright の標準機能でそのまま実現できる
- 安定 API のみで構成でき、クロスプラットフォーム
- 難点: 「同一ウィンドウ」の一体感はなくなる(ウィンドウ並置で代替)

## Decision

**ver1.0.0 は案B(サイドカー並走)を本線とする。** 案A(埋め込み)は `spike/embedded-webview` ブランチで検証し、multiwebview の安定化と Windows 先行リリース方針が確認できた時点で昇格を再検討する。

## Consequences

- コア機能(記録・レポート)を Tauri の unstable API に依存させずに ver1.0.0 へ到達できる
- UI 設計はウィンドウ並置前提で行う(Tauri 側から対象ウィンドウの位置・サイズを制御して擬似的な一体感を作る)
- 案A へ移行してもPlaywright `connectOverCDP` ベースの記録層はほぼ再利用できるため、手戻りは表示層に限定される
