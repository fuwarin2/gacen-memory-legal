# みんなのゲーセンメモリー 法務ページ公開手順

作成日: 2026-06-05  
対象アプリ: みんなのゲーセンメモリー  
運営名: Arcade Memory Studio  
サポートメール: gacenmemory@gmail.com

このディレクトリは、App Store Connect / Google Play Console に入力する公開URL向けの静的サイトです。内容は実装実態に合わせた法務確認前の下書きです。公開前に人間が内容を確認してください。

## 作成ページ

- `index.html`
- `privacy.html`
- `terms.html`
- `community-guidelines.html`
- `support.html`
- `assets/style.css`

## 実装実態メモ

- 写真は「自分だけ」のメモにだけ添付され、現在は端末内保存です。全国公開・友達限定投稿には写真を含めません。
- 店舗写真機能は準備中です。
- 使用金額、プレイ記録、預けメダル、カウンター、カウンタータイマー、お気に入りは現在の画面実装では端末内の自己記録です。
- ログイン認証、プロフィール、全国公開メモ、全国公開店舗メモ、友達限定メモ、友達申請、友達関係、問い合わせ、通報、店舗・機種の各種申請、設置・撤去・カテゴリ修正報告はSupabaseへ送信されます。
- 位置情報は地図画面でアプリ使用中に取得し、近くの店舗表示に使います。現在地をSupabaseへ保存する実装は確認していません。
- 広告、アプリ内課金、プッシュ通知、解析・トラッキング用SDKの導入は確認していません。
- アカウント削除はアプリ内から実行できます。公開寄与は匿名化して保持し、投稿者名は「退会済みユーザー」と表示します。

## GitHub Pagesで公開する手順

1. 任意のGitHubリポジトリを用意します。
2. この `legal-site` ディレクトリの中身を、公開したいパスへ配置します。例: リポジトリ直下、または `docs/`。
3. GitHubのリポジトリ設定から Pages を開きます。
4. Source を `Deploy from a branch` にし、公開ブランチと公開フォルダを選択します。
5. 公開後、次のようなURLへアクセスできることを確認します。

```text
https://xxxx.github.io/gacen-memory/privacy.html
https://xxxx.github.io/gacen-memory/terms.html
https://xxxx.github.io/gacen-memory/community-guidelines.html
https://xxxx.github.io/gacen-memory/support.html
```

## Netlifyで公開する手順

1. Netlifyで新しいサイトを作成します。
2. Git連携する場合は、この静的サイトを含むリポジトリを選択します。
3. Publish directory に `legal-site` を指定します。リポジトリ上の配置に合わせて `リリース準備中/legal-site` や `docs/legal-site` などへ読み替えてください。
4. ビルドコマンドは不要です。
5. Netlifyが発行したURL、または独自ドメインで `privacy.html` 等が開けることを確認します。

## Vercelで公開する手順

1. Vercelで新しいプロジェクトを作成します。
2. 静的サイトを含むリポジトリを選択します。
3. Framework Preset は `Other` または静的サイト相当を選びます。
4. Output Directory にこのディレクトリを指定します。配置に合わせてパスは調整してください。
5. ビルドコマンドは不要です。
6. 発行URLで `privacy.html` 等が開けることを確認します。

## Google Sitesで手動作成する場合

HTMLファイルをそのまま置けない場合があります。その場合は次の代替手順にしてください。

1. Google Sitesで新しいサイトを作成します。
2. ページを4つ作成します。
   - プライバシーポリシー
   - 利用規約
   - 投稿・撮影ルール
   - サポート
3. 各HTMLの本文をGoogle Sites上へ貼り付け、見出しとリンクを整えます。
4. 公開URLを取得します。
5. App Store / Google Playへ入力するURLは、各ページの公開URLを使います。

## App Store Connectに入力するURL案

最終URLは公開後に人間が置換してください。

```text
Privacy Policy URL:
https://xxxx.github.io/gacen-memory/privacy.html

Support URL:
https://xxxx.github.io/gacen-memory/support.html

Marketing URL:
https://xxxx.github.io/gacen-memory/

Terms URL:
https://xxxx.github.io/gacen-memory/terms.html
```

App Store Connect上に「利用規約」専用欄がない場合は、サポートURLや審査メモ、またはカスタム利用許諾が必要かを人間が判断してください。

## Google Play Consoleに入力するURL案

最終URLは公開後に人間が置換してください。

```text
Privacy Policy URL:
https://xxxx.github.io/gacen-memory/privacy.html

Developer contact / Support:
https://xxxx.github.io/gacen-memory/support.html

Terms:
https://xxxx.github.io/gacen-memory/terms.html
```

## Google Play Data Safety入力時に必要そうな項目

実装確認に基づく整理です。最終入力はGoogle Play Consoleの最新設問を見ながら人間が確定してください。

| 項目 | 入力方針メモ |
|---|---|
| データが収集されるか | ログイン・投稿・友達・申請・問い合わせ・通報を使う場合は、Supabaseへ送信されるデータがあります。 |
| 個人情報 | メールアドレス、表示名、ユーザーID、プロフィール、返信先メールアドレス。 |
| ユーザー生成コンテンツ | 全国公開メモ、全国公開店舗メモ、友達限定メモ、問い合わせ、通報、申請・報告内容。 |
| 位置情報 | 現在地は端末上で近くの店舗表示に利用。Supabase保存は確認なし。Data Safety上の申告方針は人間判断。 |
| 写真 | 端末内の「自分だけ」メモ用。現在は外部送信・公開なし。 |
| 使用金額・預けメダル・カウンター | 現在の画面実装では端末内の自己記録。 |
| 広告・課金・通知 | 現時点で導入確認なし。 |
| データ削除 | アプリ内からアカウント削除可能。公開寄与は匿名化して保持。 |
| 送信時の保護 | Supabaseとの通信はHTTPS。 |
| 第三者提供 | Supabaseはバックエンド処理委託先として利用。Google Playの「共有」該当性は人間確認。 |

## 公開後に確認する項目

- `privacy.html`、`terms.html`、`community-guidelines.html`、`support.html` がHTTPSで開ける。
- 各ページのナビゲーションリンクが正しく動く。
- サポートメール `gacenmemory@gmail.com` の `mailto:` リンクが正しい。
- スマートフォン幅で本文が読める。
- App Store Connect / Google Play Consoleへ入力したURLがログイン不要で開ける。
- 公開ページとアプリ内文言が矛盾していない。
- `src/constants/legal.ts` の `PRIVACY_POLICY_URL` / `TERMS_URL` は未設定のため、アプリ内からWeb最新版へ遷移させる場合は人間判断で差し替える。
- `src/constants/legal.ts` の改定日がWebページと異なるため、公開時に更新するか人間が判断する。

## 人間確認TODO

- 法務・利用規約の最終確認。
- Apple App Privacyの位置情報申告方針の確定。
- Google Play Data Safetyの最終入力。
- 公開URLの置換。
- App Store / Google Playの審査用テストアカウント準備。
- 今後、広告、課金、プッシュ通知、解析、写真公開、店舗写真投稿を追加する場合は、このサイトとストア回答を更新する。
