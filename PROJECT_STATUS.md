# PROJECT_STATUS.md — Edge Current LP

このファイルは作業のたびに更新する。確認できない事実は推測で埋めず、「要確認」または空欄とする。

## 正式バージョン

origin/main の最新Push済みCommitが正式版。それより新しいローカルの内容（未Commit・未Push分）は、Push・マージされるまで正式版ではない。

## ブランチ

main

## 最新の正式Commit／Push

- Commit: `156b375`（"Create CNAME"）
- Push日時: 要確認（リポジトリのローカル情報からは確認不可）

## 完了済み

- 要確認（origin/main への Push済み範囲について、タスク単位の完了記録なし。git log 上の直近Push済みCommitは `156b375` "Create CNAME" ほか）

## 作業中

- ローカルの `main` ブランチが origin/main より **3コミット先行**（未Push）
- `index.html` に **未Commitの変更**あり（Hero右カラムのレイアウト調整など、直近の編集セッションによるもの）

## 次の承認済み作業

- 要確認（人からの承認済み指示なし）

## 人による確認待ち

- ローカルの未Push commit（3件）を origin/main へ Push するかどうかの判断
- `index.html` の未Commit変更を採用するかどうかの確認
- GitHub Pages の公開設定・DNS反映状況（リポジトリ内のファイルからは確認不可、要確認）

## 既知の注意点

- `CNAME` ファイルに `edgecurrent.net` が設定されているが、GitHub Pages側の公開設定・DNS反映状況は要確認。
- `index.html` は単一ファイルで、CSS（`<style>`）・JavaScript（`<script>`）がすべてインライン記述されている。別途のCSS/JS/assetsファイルは存在しない。
- GoogleフォームリンクはJS内の `GOOGLE_FORM_URL` 定数で一括設定され、`.js-google-form-link` クラスの要素に反映される。

## 仕様なしで変更してはいけない項目

- 現在の公開導線
- CTA（文言・配置）
- GoogleフォームURL
- 新規タブ遷移（`target="_blank"`）の挙動
- 既存のブランド文言
- 画像・アセット・外部URL・フォーム設定の削除・置換・公開
- Commit・Push・GitHub Pages設定・フォーム設定などの外部操作
