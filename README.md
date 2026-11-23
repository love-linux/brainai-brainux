# BrainAI for Brainux

SHARP Brain 上の Linux（Brainux）で動く、オフラインの日本語対話 AI です。

## 機能

- **日本語の対話**: インターネットに接続せず、本体と SD カードの中だけで会話できます。
- **モデルの切り替え**: `/model` で会話用の v2 とコード用の coderv1 を切り替えられます。
- **計算**: 関数電卓の道具と、モデルに内蔵した計算ユニットで計算できます。
- **時刻**: 現在の時刻、日付、曜日を確認できます。
- **百科事典の検索**: 別インストーラーの辞書を入れると、約 139 万項目をオフラインで検索できます。
- **メモ**: 内容を本体に保存し、あとから読み出せます。
- **会話の思い出し**: 今の会話の前のほうの発言を探して答えられます。
- **日本語入力**: Anthy による漢字変換に対応しています。
- **2 つのターミナルに対応**: 起動直後の全画面コンソールでも、デスクトップの LXTerminal でも動きます。
- **CLI 画面**: ロゴ、入力枠、モデル名、返答ごとの速度を表示します。
- **コマンド**: `/help`、`/model`、`/clear`、`/exit` が使えます。

## 使い方

> QEMU 上の公式 Brainux で動作を確認しています。Brain 実機での動作は未確認です。

### ダウンロード

[Releases](https://github.com/love-linux/brainai-brainux/releases/latest) から次のファイルをダウンロードして、Brainux に移します。

- `brainai-addon-0.1.tar.gz`: アプリとモデル（必須）
- `brainai-dict-0.1.tar.gz`: 百科事典の辞書（検索を使うときだけ）

### インストール

```sh
tar xzf brainai-addon-0.1.tar.gz
cd brainai-addon-0.1
sudo sh install.sh
```

### 辞書のインストール

インストール中は約 550MB、インストール後は 412MB の空きが必要です。

```sh
tar xzf brainai-dict-0.1.tar.gz
cd brainai-dict-0.1
sudo sh install.sh
```

### 起動

起動直後の全画面コンソールでも、デスクトップの LXTerminal でも、次のコマンドで起動します。

```sh
brainai
```

### 操作

| 操作 | 動き |
|---|---|
| `Ctrl+J` | 日本語入力のオン・オフ |
| `Space` | 漢字に変換 |
| `Enter` | 変換を確定、もう一度押すと送信 |
| `Ctrl+C` | 生成を途中で止める |
| `/model` | モデルの一覧 |
| `/model coderv1` | コード用モデルに切り替え（`/model v2` で戻す） |
| `/clear` | 会話を消す |
| `/help` | 使い方を表示 |
| `/exit` | 終了 |

計算、時刻、検索、メモ、前の発言の思い出しは、普通に話しかけると使われます。メモは `~/.brx/memo.txt` に保存されます。会話は終了すると消えます。

### 削除

アプリと辞書は、それぞれのフォルダで次のコマンドを実行すると削除できます。メモは残ります。

```sh
sudo sh uninstall.sh
```

## 作者とライセンス

作者: **love-linux**
配布元: https://github.com/love-linux/brainai-brainux

再配布するときは、作者名「love-linux」とこのリポジトリのリンクを必ず明記し、`NOTICE.txt` とライセンスのファイルを一緒に配布してください。

- **アプリ本体**: [LICENSE-APP.txt](LICENSE-APP.txt)。無料で使え、改変していないものは再配布できます。改変版の配布には love-linux の許可が必要です。
- **モデル (v2、coderv1)**: [CC BY-SA 4.0](LICENSE)
- **辞書 (kb.tsv)**: [CC BY-SA 4.0](LICENSE)。[日本語版 Wikipedia](https://ja.wikipedia.org/) の見出しと本文冒頭をもとに作成しています。
