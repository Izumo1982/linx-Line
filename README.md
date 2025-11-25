# linx-Line

ステップ 1：VirtualBox をインストール

sudo apt install virtualbox virtualbox-ext-pack

ステップ 2：Genymotion Desktop の入手

公式サイト：
https://www.genymotion.com/download/

Linux 版をダウンロード

ファイル名例：

genymotion-3.6.0-linux_x64.bin

chmod +x genymotion-\*-linux_x64.bin

./genymotion-\*-linux_x64.bin

ステップ 3：Genymotion を起動してデバイスを作成

Genymotion Desktop を起動

「Add」を押す

以下の Android イメージを選択：

🎯 推奨イメージ
⭐ Android 10.0 (API 29)

→ LINE の QR 読み取りが最も安定する

または

⭐ Android 11.0 (API 30)

→ 新しいが多少重いだけで安定

🧰 ステップ 4：設定（最重要：Camera passthrough）

作成した仮想デバイスを選択 → Settings を押す。

🔸 CPU / RAM
CPU: 2〜4 core
RAM: 2048〜4096MB

📷 最重要：Camera 設定

Genymotion の設定で：

Camera → Webcam passthrough → /dev/video0（あなたの Web カメラ）

これを必ず選択。

📌 Genymotion は VirtualBox 経由でカメラを直接 Android に渡すため、LINE の QR 画面も落ちない。

🧩 ステップ 5：Google Apps (GApps) を有効化

LINE を使うなら Play ストアが必要。

Genymotion の右上にある
Open GAPPS アイコン（ダウンロードの雲アイコン）
を押すだけで自動インストールされる。

🧱 ステップ 6：LINE をインストール

Play ストア → LINE をインストール

🎥 ステップ 7：LINE の QR 読み取りをテスト

PC 版 LINE を開いて QR ログイン画面を出す

Genymotion 内の LINE → QR ログイン

カメラが起動して PC 画面が映る

QR 解析が成功すると
　 PC 版 LINE がログインされる

Waydroid とは違い、クラッシュしません。

🔒 Step 8（重要）
PC 版 LINE にログインできたら

スマホ（Genymotion）はもう不要

再ログイン時もスマホ不要

本人確認コードも不要

QR も不要

PC 版 LINE 単体で使い続けられる。

🎉 まとめ：Genymotion の構成（最強安定版）
項目 推奨値
Genymotion Version 3.5〜3.6
Android Version 10 or 11
CPU 2〜4 core
RAM 2〜4GB
Camera mode Webcam passthrough
VirtualBox 6 or 7
GApps Open GApps ボタンで自動
