# Task Board

React + Vite で作成したシンプルなタスクボードアプリです。

## 機能

- テキスト入力でタスクを追加
- チェックボックスで完了・未完了を切り替え
- タスクの削除
- 完了済みタスクはグレー表示

## 開発

```bash
npm install
npm run dev
```

## 公開（GitHub Pages）

`main` ブランチに push すると GitHub Actions（[.github/workflows/deploy.yml](.github/workflows/deploy.yml)）が自動でビルドし、GitHub Pages に公開します。

公開URL: https://Yuki-c6.github.io/task-board/

初回のみ、リポジトリの Settings > Pages で Source を「GitHub Actions」に設定してください。
