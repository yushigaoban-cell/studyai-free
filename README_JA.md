# STUDY//AI FREE — PROデザイン版

iPad / Androidのブラウザで利用するレスポンシブ学習Webアプリです。

## 機能
- ダークネイビー×ブルーのモバイル対応UI
- 問題の手動登録、AI生成JSONの一括取り込み
- 選択問題・短答問題の演習と自動採点
- 間違えた問題の復習リスト
- 教科別正答率、学習履歴、7日間の回答グラフ
- JSONバックアップ・復元
- PWA用manifestとService Worker

## 制限とデータ
- AI問題作成は、プロンプトをChatGPTなどに貼り付け、生成されたJSONを取り込む方式です。AIのAPI料金はかかりませんが、AIサービスの無料利用制限は適用されます。
- 採点は文字列一致方式です。記述の意味を理解するAI採点ではありません。
- データはブラウザ内に保存され、自動で端末間同期しません。別端末では設定からバックアップを書き出し、読み込んでください。
- PWAのホーム画面追加とオフラインキャッシュにはHTTPS公開が必要です。

## iPad / Androidだけで公開する概要
1. ブラウザでGitHubにログインし、新しいリポジトリを作成。
2. ZIPを展開して `index.html`、`manifest.json`、`sw.js` をリポジトリのルートにアップロード。
3. Settings → Pages で公開元ブランチとルートを指定。
4. 公開されたHTTPS URLをiPad Safari / Android Chromeで開く。
5. iPadは共有メニュー、AndroidはChromeメニューから「ホーム画面に追加」。

## AI生成JSONの例
{
  "questions": [
    {
      "subject": "数学",
      "type": "choice",
      "question": "x² = 9 のとき、xの値は？",
      "choices": ["3のみ", "-3のみ", "±3", "9"],
      "answer": "3",
      "explanation": "x²=9よりx=±3です。"
    },
    {
      "subject": "英語",
      "type": "short",
      "question": "「私は毎日勉強します」を英語にしなさい。",
      "answer": "I study every day",
      "explanation": "習慣を表すので現在形を使います。"
    }
  ]
}

選択問題の answer は正解選択肢の番号（1から始まる文字列）です。
