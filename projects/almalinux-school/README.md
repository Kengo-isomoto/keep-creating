# 🏫 AlmaLinux｜学校実習

職業訓練校のAlmaLinux環境で、Linux / Serverの管理操作を実践しています。

## 📚 学校実習で扱った内容

### システム・サービス管理
- `systemctl` を使用したサービス状態確認・再起動
- `firewalld` の稼働状態確認と再起動
- systemd / Unit / service / target、Linuxの起動の流れを学習

### ストレージ・ファイルシステム
- MBR / GPT、パーティション、XFS、マウントの仕組みを学習
- `lsblk`、`df -h` でストレージ・空き容量を確認
- LVMの `PV → VG → LV` 構成を理解
- `pvdisplay` / `vgdisplay` / `lvdisplay` で実際のLVM構成を確認

### ログ・ファイル調査
- rsyslog、ログローテーション、`/dev/null` の仕組みを学習
- `grep` を使用して `/var/log/messages` から必要なログを抽出
- `find` で名前・種類・サイズなどを条件にファイルを検索
- `-exec` を使い、検索結果へ `ls -l` を実行

### シェルスクリプト・自動化
- `vi` でシェルスクリプトを作成し、bashで実行
- 変数・四則演算・終了コードを実操作
- `date` / `vmstat` / `df -h` をまとめたリソース確認スクリプトを実行
- `if` / `for` による条件分岐・繰り返しの基本を学習
- cron / crontabでシェルスクリプトの時刻指定実行を設定し、出力結果まで確認

### ネットワーク・時刻管理
- `ip addr` でIPアドレス・インターフェースを確認
- `ip route` でルーティングテーブルを表示
- `ping` で外部への疎通を確認
- `chronyc` でNTP時刻ソースの状態・同期先を確認

## 🔧 サービスの状態確認・操作

SSH接続を受け付ける `sshd` サービスについて、状態確認・停止・起動を行いました。

使用したコマンド：

`systemctl status sshd`  
`systemctl stop sshd`  
`systemctl start sshd`

停止後に `inactive (dead)`、起動後に `active (running)` と表示されることを確認しました。

## 🔧 サービスの自動起動設定

`sshd` の自動起動を無効化・有効化し、設定状態の変化を確認しました。

使用したコマンド：

`sudo systemctl disable sshd`  
`sudo systemctl enable sshd`  
`systemctl status sshd`

`disable` 後に `disabled`、`enable` 後に `enabled` となることを確認しました。

また、自動起動設定に使用されるシンボリックリンクについて、

`/etc/systemd/system/multi-user.target.wants/sshd.service`

から

`/usr/lib/systemd/system/sshd.service`

へのリンクが、`disable` で削除され、`enable` で再作成されることを確認しました。

## 🔍 inode・ファイル情報の確認

ファイルを作成し、inodeやアクセス権限などの情報を確認しました。

使用したコマンド：

`echo "sample" >> sample.txt`  
`stat sample.txt`  
`ls -i sample.txt`

`stat` と `ls -i` で同じinode番号が表示されることを確認しました。

また、`stat` の出力から `0644 / -rw-r--r--` などのアクセス権限、所有者、グループ、更新日時などを確認しました。

[KEEP CREATING トップへ](../../README.md)
