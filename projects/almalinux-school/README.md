# 🏫 AlmaLinux｜学校実習

職業訓練校のAlmaLinux環境で、Linux / Serverの管理操作を実践しています。

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
