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
   - [ ] 構造化データの検証完了
   - [ ] コンソールエラーなし
   - [ ] リンクの動作確認完了

3. **開発フロー**
   ```bash
   # 1. ローカルテスト
   npm run dev
   
   # 2. ブラウザで確認
   # http://localhost:4321/astro-zenn-pages/
   
   # 3. 構造化データテスト
   # https://search.google.com/test/rich-results
   
   # 4. 問題なければcommit & push
   git add .
   git commit -m "description"
   git push
   ```

## 構造化データ検証

### チェックポイント
- JSON-LD形式で正しく出力されているか
- 必要なプロパティが全て含まれているか
- 画像URLが正しく設定されているか
- リンクが正しく動作するか

### テストツール
- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [Schema.org Validator](https://validator.schema.org/)

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
