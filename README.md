# ライトスタンド、倒すな！

左右をタップしてライトスタンドを支えるブラウザゲーム。`index.html` 1ファイルで動く静的サイト（ビルド不要・外部通信なし）。

## 公開方法

### A. GitHub + Vercel（推奨）

1. GitHub で新しいリポジトリを作る（例: `lightstand-game`、Public / Private どちらでも可）
2. このフォルダの中身（`index.html` と `README.md`）をリポジトリにアップロードする
   - ブラウザなら「Add file → Upload files」にドラッグ＆ドロップして Commit
   - ターミナルなら:
     ```bash
     git init
     git add .
     git commit -m "first commit"
     git branch -M main
     git remote add origin https://github.com/<ユーザー名>/lightstand-game.git
     git push -u origin main
     ```
3. https://vercel.com/new を開き、そのリポジトリを「Import」する
4. Framework Preset は「Other」のまま、Build Command・Output Directory は空のまま「Deploy」
5. `https://<プロジェクト名>.vercel.app` で公開される。以降は GitHub に push するたびに自動で再デプロイされる

### B. Cloudflare Pages（Gitなしでいちばん手軽）

1. Cloudflare ダッシュボード → Workers & Pages → Create → Pages → 「Upload assets」
2. プロジェクト名を入力し、このフォルダ（または zip）をドラッグ＆ドロップして Deploy
3. `https://<プロジェクト名>.pages.dev` で公開される。更新するときは同じ画面から新しいデプロイをアップロードする

### C. GitHub Pages

1. A の手順 1〜2 でリポジトリにアップロードする（無料プランは Public リポジトリのみ）
2. リポジトリの Settings → Pages → Source を「Deploy from a branch」、Branch を `main` / `/(root)` にして Save
3. 数分後に `https://<ユーザー名>.github.io/lightstand-game/` で公開される

## カスタマイズ

`index.html` の `<script>` 先頭にある `CONFIG` で文言を変えられる。

| キー | 内容 |
|---|---|
| `title` / `sub` | 画面上部のタイトルと説明 |
| `minuteGoal` | 1分チャレンジの目標秒数 |
| `minuteFailMessage` | 1分チャレンジで倒れたときのメッセージ |
| `minuteClearMessage` | 1分チャレンジをクリアしたときのメッセージ |
| `endlessFailMessage` | エンドレスで倒れたときのメッセージ |
| `safetyTip` | 倒れたときに小さく出す一言（空なら非表示） |

難易度は `DIFFUSERS` の `k`（倒れやすさ）・`noise`（揺れ）・`growth`（時間で揺れが増える割合）・`push`（タップの強さ）・`maxDeg`（倒れる角度）・`gust`（突風の効きやすさ）で調整できる。
