# MONSTER DATABASE — PWA公開パッケージ

## フォルダ内容
- `index.html` : 図鑑本体
- `manifest.json` : ホーム画面追加時のアプリ名・表示設定
- `sw.js` : キャッシュとオフライン表示
- `icons/` : アプリアイコン

## 1. GitHub Pagesで公開する方法
1. GitHubにログインして、新しいリポジトリを作成する（例: `monster-database`）。
2. このZIPを解凍する。
3. `index.html`、`manifest.json`、`sw.js`、`icons`フォルダを、リポジトリの一番上にアップロードする。
4. リポジトリの Settings → Pages を開く。
5. Build and deployment の Source を `Deploy from a branch` にする。
6. Branch を `main`、フォルダを `/(root)` にして Save。
7. 数分待つと `https://あなたのGitHubユーザー名.github.io/monster-database/` の形式で公開される。

※公開URLはGitHubのPages画面に表示されるURLを使う。リポジトリ名を変えた場合はURLも変わる。
※GitHub PagesはHTTPSで配信されるので、PWAのService Workerを利用できる。

## 2. iPhoneでホーム画面に追加
1. 公開URLをChromeで開く。
2. Chromeの共有メニューから「ホーム画面に追加」を選ぶ（表示が異なる場合はSafariでも同じURLを開き、共有 → ホーム画面に追加）。
3. 名前を確認して「追加」。
4. ホーム画面のアイコンから起動する。

## 3. モンスターを追加・編集する
1. `index.html` を開く。
2. `const monsters = [` の中にあるデータを編集する。
3. 例:
   `{id:130,name:"新モンスター",image:"monster07.png",type:"新しい科",description:"説明文"}`
4. 画像を使う場合は画像ファイルもリポジトリの一番上にアップロードする。画像名はデータの `image` と完全一致させる。
5. 変更した `index.html` と追加画像をGitHubにアップロードして、既存ファイルを置き換える。
6. 数分後にサイトが更新される。ホーム画面アプリで古い表示が残る場合は、アプリを完全に閉じて再起動する。反映が遅い場合は少し待って再度開く。

## 4. オフラインについて
一度オンラインでサイトを開くと、図鑑本体・アイコン等がキャッシュされ、通信がないときも基本画面を開ける。
画像はオンラインで読み込んだものから順にキャッシュされる。新しい画像は一度オンラインで開いて読み込ませる。
更新後、古い内容が残る場合があるので、最新版が必要なときは一度ネット接続して開く。

## 5. 重要
- `index.html` と `manifest.json` と `sw.js` のファイル名は変えない。
- `icons` フォルダ名も変えない。
- `monster01.png` などの画像は、HTMLと同じ階層に置く（このサンプルでは画像ファイル自体は含めていない）。
- このパッケージは公開用の土台。GitHubへのログイン・アップロード・公開操作は本人が行う必要がある。
