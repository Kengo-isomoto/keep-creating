# 🖥️ Ubuntu Server「零号機」

Mac上のUTMに構築した、Linux / Server学習用のUbuntu Server環境です。

## 🔧 実践内容

- Ubuntu Serverの構築
- ISOファイルのSHA-256確認
- IPアドレスの確認
- MacからSSH接続
- ファイル・ディレクトリ操作
- 所有者・グループ・権限の確認と変更
- プロセスの確認と終了
- サービスの状態確認・操作
- ログの確認
- APTによる更新・パッケージ管理

## 🔍 トラブルシューティング例

MacからSSH接続できなかった際、SSHサービスの状態を確認しました。

`inactive (dead)` だったためサービスを起動し、`active (running)` になったことを確認。

その後、Macから再度SSH接続を行い、接続できることを確認しました。

この実践では、

**状態確認 → 原因候補の確認 → 対応 → 再確認**

という流れを経験しました。

[KEEP CREATING トップへ](../../README.md)
