# みんなのゲーセンメモリー 法務ページ公開手順

作成日: 2026-06-05  
更新日: 2026-06-10  
対象アプリ: みんなのゲーセンメモリー  
運営名: Arcade Memory Studio  
サポートメール: gacenmemory@gmail.com

このリポジトリは、App Store Connect / Google Play Console に入力する公開URL用の静的サイトです。

## 公開ページ

- `index.html`
- `privacy.html`
- `terms.html`
- `community-guidelines.html`
- `support.html`
- `assets/style.css`

## 公開URL

```text
Marketing URL:
https://fuwarin2.github.io/gacen-memory-legal/

Privacy Policy URL:
https://fuwarin2.github.io/gacen-memory-legal/privacy.html

Terms URL:
https://fuwarin2.github.io/gacen-memory-legal/terms.html

Community Guidelines URL:
https://fuwarin2.github.io/gacen-memory-legal/community-guidelines.html

Support URL:
https://fuwarin2.github.io/gacen-memory-legal/support.html
```

## App Store Connect 入力欄

```text
Privacy Policy URL:
https://fuwarin2.github.io/gacen-memory-legal/privacy.html

Support URL:
https://fuwarin2.github.io/gacen-memory-legal/support.html

Marketing URL:
https://fuwarin2.github.io/gacen-memory-legal/

Terms URL:
https://fuwarin2.github.io/gacen-memory-legal/terms.html
```

App Store Connect に専用の Terms URL 欄がない場合は、サポートURL、審査メモ、またはカスタム利用許諾欄の要否を運営者が判断してください。

## Google Play Console 入力欄

```text
Privacy Policy URL:
https://fuwarin2.github.io/gacen-memory-legal/privacy.html

Developer contact / Support:
https://fuwarin2.github.io/gacen-memory-legal/support.html

Terms:
https://fuwarin2.github.io/gacen-memory-legal/terms.html
```

## 公開手順

1. `main` ブランチでHTML/CSSを更新します。
2. `git status --short` で変更内容を確認します。
3. `git grep` または `Select-String` で未完成表示や仮URLが残っていないことを確認します。
4. `git commit` します。
5. `git push origin main` します。
6. GitHub Pages の反映を数分待ちます。
7. 上記の公開URLをブラウザで開き、各ページとナビゲーションリンクを確認します。

## 公開後確認

- `privacy.html` / `terms.html` / `community-guidelines.html` / `support.html` が HTTPS で開ける。
- 各ページのナビゲーションリンクが正しく動く。
- サポートメール `gacenmemory@gmail.com` の `mailto:` リンクがある。
- App Store Connect / Google Play Console に入力するURLがログイン不要で開ける。
- ページ内に未完成表示、仮URL、秘密情報が残っていない。

## 実装実態メモ

- 写真は「自分だけ」メモに添付され、現在は端末内保存です。全国公開や友達限定投稿には写真を含めません。
- 店舗写真機能は準備中です。
- ログイン認証、プロフィール、全国公開メモ、全国公開店舗メモ、友達機能、問い合わせ、通報、店舗・機種の各種申請、設置・撤去・カテゴリ修正報告は Supabase へ送信されます。
- 使用金額、プレイ記録、預けメダル、カウンター、カウンタータイマー、お気に入りは現在の画面実装では端末内の自己記録です。
- 位置情報は地図画面でアプリ使用中に取得し、近くの店舗表示に使います。現在地を Supabase へ保存する実装は確認していません。
- 広告、アプリ内課金、プッシュ通知、解析トラッキング用SDKの導入は確認していません。
- アカウント削除はアプリ内から実行できます。公開寄与は匿名化して保持し、投稿者名は「退会済みユーザー」と表示します。

## Data Safety 入力時の要点

最終入力は Google Play Console の最新設問を確認しながら運営者が確定してください。

| 項目 | 入力方針メモ |
|---|---|
| データ収集 | ログイン、投稿、友達、申請、問い合わせ、通報で Supabase へ送信されるデータがあります。 |
| 個人情報 | メールアドレス、表示名、ユーザーID、プロフィール、問い合わせ返信用メールアドレスを扱う場合があります。 |
| ユーザー生成コンテンツ | 全国公開メモ、全国公開店舗メモ、友達限定メモ、問い合わせ、通報、各種申請内容があります。 |
| 位置情報 | 現在地は端末上で近くの店舗表示に利用します。Supabase 保存は確認していません。 |
| 写真 | 現在は端末内の「自分だけ」メモ用です。外部送信・公開はしません。 |
| 広告・課金・通知 | 現時点で導入確認なし。 |
| データ削除 | アプリ内からアカウント削除可能。公開寄与は匿名化して保持します。 |
| 通信時の保護 | Supabase との通信は HTTPS です。 |
