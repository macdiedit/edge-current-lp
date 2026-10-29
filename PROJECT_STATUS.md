# PROJECT_STATUS.md — Edge Current LP

更新日: 2026-10-29（JST）

## 正式バージョン

GitHub の origin/main に Push 済みの内容だけが正式版。以下のセキュリティ修正は作業ブランチで進める公開前の変更であり、mainへの反映が終わるまでは正式版ではない。

## ブランチ

- 作業ブランチ: `codex/edgecurrent-security-2026-10-29`
- 作業場所: 元リポジトリとは別の、今回の作業用クローン
- GitHub の正式ブランチ: `main`

## 最新の正式Commit／Push

- Commit: `f6d3783dad4ec0f45372ed9a0dc0d969d1e3e25e`（`Add Brand Movie to Edge Current LP`）
- 2026-10-29 に GitHub API、元のローカルリポジトリ、作業用クローンの HEAD 一致を確認。
- Push日時: 未確認。

## 完了済み（公開前の実装・検証）

- 公開3ページ相当のHTMLに、既存のインラインCSS・JavaScriptのSHA-256を許可するmeta CSPを追加。
- 3ページに `strict-origin-when-cross-origin` のreferrer metaを追加。
- ユーザー承認に基づき、thanksページの仮IDのMetaピクセル、noscript追跡画像、計測専用クリック処理を削除。
- CSS、CTA文言、リンク先、target/rel、画像・動画の参照とデータを維持したことを差分・静的検証で確認。
- 申込みリンク2件の設定処理と、スクロール位置に応じたCTAの表示・非表示を、Node.jsによるDOMの模擬テストで確認。
- 公開中の3ページ、参照画像3点、動画、Google Forms 2件の読み取り応答を確認。修正版の公開確認ではない。
- 2026-10-29、ユーザーがChromeで修正版を確認し「3ページともOK」と回答。トップの画像・動画、チェックリストのフォーム導線、完了ページの表示について人による確認を完了。Codexによるブラウザー自動検証やGoogle Formsへのテスト送信を実施したという意味ではない。

## 作業中／人による確認待ち

- チェックリスト上部の「無料でダウンロードする」は、従来から `#form` の下部案内へ移動するリンク。Google Formsを開くのは移動先の「チェックリストを受け取る」ボタン。ユーザーの確認により、当初の不具合申告は既存の2段階導線の確認として整理した。上部CTAを直接Google Formsへ変更する修正はしていない。
- 2026-10-29、ユーザーが3HTMLと本ファイルの4ファイルだけのCommit、作業ブランチへのPush、PR作成を承認。これらを実施する段階。mainへのmerge・本番公開・GitHub設定変更は引き続き別途承認待ち。
- main保護は `protected=false`、rulesets一覧は空。PR経由の反映、force push／削除の禁止などの具体的な保護設定は、単独運用との両立と設定変更の承認を得てから行う。
- GitHub Pages管理画面で、公開ソースは `Deploy from a branch` → `main` → `/ (root)`、Enforce HTTPSは有効、カスタムドメインは `edgecurrent.net` と確認。mainへの反映は本番公開を伴う。DNSチェックは参照時に進行中と表示され、ドメイン検証完了状態は未確認。

## 保留・残存項目

- プライバシーポリシー: 窓口・保存期間の方針が未定とのユーザー回答に基づき保留。推測の文言や新しい公開導線は追加していない。
- `frame-ancestors`／X-Frame-Options、nosniff、Permissions-Policy: HTTPレスポンス側の対策が残る。meta CSPで代用した扱いにしない。配信基盤・DNS・有料サービスは変更していない。
- Google Formsの回答権限、保存先、通知、自動返信、不正送信対策、Google Drive資料の公開要件・共有権限は未確認。送信・回答一覧・非公開資料の取得はしていない。
- 自動監査・定期実行の導入は保留のまま。新しいCIやCodexの定期実行は設定していない。

## 保守上の注意

- `index.html`、`checklist/index.html`、`checklist/thanks.html` のインラインCSS／JSを編集した場合、同じファイルのmeta CSP内のSHA-256も再計算する。空白や改行の変更でもハッシュは変わる。
- Googleフォームは既存の外部リンクで開く構成。自サイト内にフォーム送信処理はない。thanksページには引き続き資料のDriveリンクがあり、回答者限定のアクセス制御を追加したわけではない。
- `AGENTS.md` にある公開導線・文言・外部設定・公開操作の承認ルールを維持する。
