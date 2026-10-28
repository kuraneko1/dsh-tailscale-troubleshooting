# DSH Tailscale Troubleshooting

日本語 | [English](README.en.md)

DeepSeek Harness の Web 画面に Tailscale 経由でアクセスできないとき、原因の診断と、ホスト名の許可設定が原因と確認された場合の復旧を支援する Codex スキルです。

実際のサービス、プロキシ、失敗した API を確認してから修正方法を判断します。特定の環境のホスト名やアクセストークンは含まれていません。

## インストール

Codex に、このリポジトリの `skills/dsh-tailscale-troubleshooting` スキルをインストールするよう依頼してください。または、同ディレクトリを `~/.codex/skills/` にコピーし、Codex を再起動してスキルを読み直してください。

## 使い方

Codex に「DeepSeek Harness の画面が Tailscale 経由で開けないので調べて」と依頼するか、`$dsh-tailscale-troubleshooting` を明示的に指定します。
