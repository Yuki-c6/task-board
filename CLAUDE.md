# CLAUDE.md

このファイルは、Claude Code (claude.ai/code) がこのリポジトリで作業する際のガイダンスを提供します。

## プロジェクト概要

task-board プロジェクト。タスクの追加・完了切り替え・削除ができるシンプルなタスクボードアプリ。タスクは `localStorage` に保存され、ページをリロードしても消えない。

## デプロイ先

https://yuki-c6.github.io/task-board/

`main` ブランチへの push をトリガーに、GitHub Actions（[.github/workflows/deploy.yml](.github/workflows/deploy.yml)）が自動でビルド・デプロイする。

## 技術スタック

- [React](https://react.dev/) 19（関数コンポーネント + Hooks）
- [Vite](https://vite.dev/) 8（開発サーバー・ビルド）
- CSS（コンポーネントごとのプレーンな `.css` ファイル。CSS-in-JS やCSSフレームワークは未使用）
- [oxlint](https://oxc.rs/) （Lint）
- ブラウザの `localStorage` によるクライアントサイドの永続化（バックエンド・DBなし）
- GitHub Actions + GitHub Pages（デプロイ）

## コンポーネントの命名規則

- コンポーネントファイルは `PascalCase.jsx`（例: `TaskBoard.jsx`）。1ファイルにつき1コンポーネントを `function` 宣言で定義し、末尾で `export default` する。
- 対応するスタイルは同名の `PascalCase.css`（例: `TaskBoard.css`）としてコンポーネントと同じディレクトリに置き、コンポーネント側で `import './ComponentName.css'` する。
- ルート直下の `src/App.jsx` はエントリーポイント用コンポーネントとし、実際の機能は `src/` 配下の個別コンポーネント（例: `TaskBoard`）に実装する。
- CSSのクラス名はケバブケース（例: `task-form`, `delete-button`）を用いる。

## Git 運用ルール

- **コードを変更するたびに、変更内容をコミットし GitHub にプッシュすること。** 作業を溜め込まず、意味のある変更の単位ごとにコミット・プッシュを行う。
- コミットメッセージは変更内容が分かるように簡潔に記述する（「何を」よりも「なぜ」を意識する）。
- プッシュ前に `git status` / `git diff` で変更内容を確認し、意図しないファイル（secrets、.env、ビルド成果物など）が含まれていないか確認する。
- force push（`--force` / `-f`）や `git reset --hard` などの破壊的操作は、ユーザーの明示的な許可がない限り行わない。
- pre-commit フックなどが失敗した場合は `--no-verify` で回避せず、原因を修正してから再度コミットする。
- 可能な限り小さく、レビューしやすい単位でコミットする。

### 基本フロー

1. コードを変更する
2. `git status` で変更内容を確認する
3. 関連するファイルのみを `git add` する
4. 意味のある単位でコミットする（`git commit -m "..."`）
5. リモートリポジトリ（GitHub）に `git push` する

## 開発コマンド

```bash
npm run dev      # 開発サーバーを起動
npm run build    # 本番用ビルド（dist/ に出力）
npm run preview  # ビルド結果をローカルでプレビュー
npm run lint      # oxlint による Lint
```
