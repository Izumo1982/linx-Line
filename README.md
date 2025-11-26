# linx-Line

1️⃣ QEMU / KVM のインストール（Ubuntu 24）
sudo apt update
sudo apt install -y qemu qemu-kvm libvirt-daemon-system libvirt-clients bridge-utils virt-manager ovmf

virt-manager: GUI で仮想マシン作成可能

OVMF: UEFI 起動用

libvirt: QEMU/KVM 管理用デーモン

確認：

sudo systemctl enable --now libvirtd
virsh list --all

2️⃣ ユーザーを KVM グループに追加
sudo usermod -aG kvm $USER
sudo usermod -aG libvirt $USER

一度ログアウト/再ログイン必須

3️⃣ Genymotion Desktop のインストール（QEMU モード）

Genymotion Desktop の Linux .bin をダウンロード
https://www.genymotion.com/download/desktop/

（Linux x64 版）

chmod +x genymotion-_-linux_x64.bin
./genymotion-_-linux_x64.bin

インストール先は ~/genymotion など自由

Genymotion を起動

~/genymotion/genymotion

初回セットアップ時に QEMU モードを選択

「Use VirtualBox?」ではなく、「Use QEMU/KVM」を選ぶ

VirtualBox Extension Pack を必要としないので商用利用でも問題なし

4️⃣ Android 仮想デバイス作成

Genymotion の「Add」ボタンで Android 10 / 11 イメージを選択

推奨設定：

CPU: 2 cores

RAM: 2048〜4096 MB

Storage: 8〜16 GB

GPU: Hardware/OpenGL acceleration 有効

5️⃣ カメラのパススルー設定（QR 読み取り用）

QEMU モードでは Webcam を v4l2-passthrough で Android に渡す

設定例（QEMU コマンドの場合）：

-device usb-ehci,id=usb \
-device usb-host,hostbus=1,hostaddr=2 # /dev/video0 をパススルー

virt-manager の GUI でも「Add Hardware → USB Device → host webcam」を選択可能

Android 側で Open Camera 等でカメラ確認

6️⃣ Google Play ストア / LINE インストール

Genymotion の「Open GApps」ボタンで Play ストア導入

Play ストアから LINE をインストール

7️⃣ LINE QR ログインテスト

PC 版 LINE を開き QR ログイン画面を表示

仮想 Android 内 LINE を起動 → 「QR コード読み取り」

カメラ経由で読み取り成功 → PC 版 LINE がログイン

8️⃣ メリット

VirtualBox Extension Pack 不要 → 商用ライセンス問題なし

QEMU/KVM + Genymotion で LINE QR 読み取りが安定

Linux 24 で完全に完結

⚠️ 注意点

QEMU の場合、USB カメラが複数台あると lsusb で正しい bus/addr を確認して割り当てる必要あり

OpenGL ハードウェアアクセラレーションが有効でないと LINE がクラッシュすることあり

仮想デバイスは最低でも 2GB RAM + 2 CPU 推奨

💡 ここまで準備できれば、LINE の QR 読み取り専用 Linux 端末が完成します。
