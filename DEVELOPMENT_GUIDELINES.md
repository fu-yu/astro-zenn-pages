# 開発ガイドライン

## テストファースト開発方針

このプロジェクトは**テストファースト開発**を採用しています。

### 基本原則

1. **変更前に必ずローカルテストを実行**
   - `npm run dev` でローカルサーバーを起動
   - ブラウザで動作確認
   - 構造化データのテスト（Google Rich Results Test等）

2. **pushする前の必須チェックリスト**
   - [ ] ローカルでの動作確認完了
   - [ ] 構造化データがHTMLに正しく出力されているか確認
   - [ ] コンソールエラーなし
   - [ ] リンクの動作確認完了
   - [ ] デプロイ後にGitHub Actionsで自動テスト実行

3. **開発フロー**
   ```bash
   # 1. ローカルテスト
   npm run dev
   
   # 2. ブラウザで確認
   # http://localhost:4321/astro-zenn-pages/
   
   # 3. HTMLソースで構造化データ確認（JSON-LD形式）
   
   # 4. 問題なければcommit & push
   git add .
   git commit -m "description"
   git push
   
   # 5. GitHub Actionsで自動実行される項目:
   #    - デプロイ (Deploy to GitHub Pages)
   #    - リッチリザルトテスト (Rich Results Test)
   #    - テスト結果はActionsページのサマリーで確認
   ```

## 構造化データ検証

### ローカルでのチェックポイント
- JSON-LD形式で正しく出力されているか（HTMLソースで確認）
- 必要なプロパティが全て含まれているか
- 画像URLが正しく設定されているか
- リンクが正しく動作するか

### デプロイ後の自動テスト
- GitHub Actionsで自動実行される「Rich Results Test」ワークフロー
- 構造化データの存在確認と必須フィールドの検証
- テスト結果はGitHub ActionsのSummaryで確認可能

### 手動での最終確認
- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org Validator](https://validator.schema.org/)

**GitHub Actionsでの自動テストにより、デプロイ後すぐに構造化データの基本的な検証が行われます。**

## 環境変数管理

### ローカル開発
- `.env`ファイルに`MICROCMS_API_KEY`を設定

### 本番環境（GitHub Actions）
- GitHub SecretsにAPI_KEYを設定
- 環境変数名は統一（`MICROCMS_API_KEY`）

## 注意事項

⚠️ **pushする前に必ずローカルテストを実行してください**
⚠️ **構造化データの検証を忘れずに行ってください**
⚠️ **APIキーの管理に注意してください**
