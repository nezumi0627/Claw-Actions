# OpenClaw GitHub Actions Test

このリポジトリは、GitHub Actions 内で **OpenClaw** と **Ollama (Local LLM)** を連携させて実行するためのテスト環境です。

## ワークフローの概要

`.github/workflows/test.yml` は以下の手順を実行します：

1.  **環境セットアップ**: Node.js 22 のインストール。
2.  **OpenClaw のインストール**: `npm install -g openclaw` を使用。
3.  **Ollama (Local LLM) のインストール**: `ollama` をインストールし、バックグラウンドで起動。
4.  **モデルの準備**: 軽量なモデル `phi3:mini` を `ollama pull` します。
5.  **OpenClaw 設定**: `~/.openclaw/clawdbot.json` を生成し、Ollama をプロバイダーとして設定。
6.  **ゲートウェイ起動**: `openclaw gateway run` を実行し、ヘルスチェック (`/health`) で動作を確認。

## テストの実行方法

1.  このリポジトリを GitHub にプッシュします。
2.  GitHub の「Actions」タブからワークフローの実行状況を確認。
3.  手動で実行する場合は `workflow_dispatch` が有効になっています。

## 注意事項

- GitHub Actions のランナー（Ubuntu）のメモリ制限は約 7GB です。
- 8B 以上の巨大な LLM モデルはメモリ不足で動作しない可能性があるため、現在は軽量な `phi3:mini` (約 2.3GB) を使用しています。
- これはテスト段階（PoC）の構成です。
