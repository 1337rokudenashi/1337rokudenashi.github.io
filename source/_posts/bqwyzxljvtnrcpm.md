---
title: NotifyとDiscordでセキュリティ通知を連携させる方法
excerpt: セキュリティスキャンの結果を、Discordですぐに確認したいですか？
date: 2025-05-01 01:37:00
tags: [1337rokudenashi]
categories:
  - [1337rokudenashi]
index_img: https://raw.githubusercontent.com/1337rokudenashi/1337rokudenashi.github.io/main/yublueflower.jpg
banner_img: https://raw.githubusercontent.com/1337rokudenashi/1337rokudenashi.github.io/main/1337yublueflower.jpg
---

### NotifyとDiscordでセキュリティ通知を連携させる方法

セキュリティスキャンの結果を、Discordですぐに確認したいですか？

#### 1\. Discordでウェブフックを準備しましょう

Discordのサーバーで、「**チャンネル設定**」を開き、「**連携サービス**」へ進みます。「**ウェブフックを作成**」をクリックして、名前をつけます（例：「セキュリティアラート」）。すると、「**ウェブフックURLをコピー**」というボタンが表示されるので、それを押してくださいね。これが今回の連携に欠かせない、大切な鍵となります。

---

#### 2\. ProjectDiscovery Notifyをインストールしましょう

まずは、Goというプログラミング言語がインストールされているか確認してください（バージョン1.16以上が必要です）。ターミナルを開いて、以下のコマンドを実行します。

```bash
go install -v github.com/projectdiscovery/notify/cmd/notify@latest
```

正しくインストールできたか、`notify -h`と入力して確認してみましょう。

---

#### 3\. Notifyの設定ファイルを準備しましょう

`~/.config/notify/provider-config.yaml`という設定ファイルを作成するか、すでにある場合はそれを開いてください。以下の内容をファイルに書き込んで、先ほどコピーした**DiscordのウェブフックURL**を貼り付けます。

```yaml
discord:
  - discord_webhook_url: "ここにDiscordのウェブフックURLを貼り付けてください"
```

入力が終わったら、ファイルを保存してくださいね。

---

#### 4\. 最初の通知を送ってみましょう！

ターミナルから、テストメッセージを送信してみましょう。

```bash
echo "こんにちは、1337rokudenashiさん！" | notify -provider discord
```

**大切なこと**：Notifyにメッセージの送り先を教えるために、必ず最後に`-provider discord`とつけてくださいね。あとは、Discordを開いて確認してみましょう。無事にメッセージが届いているはずです。
