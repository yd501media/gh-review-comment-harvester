# AGENTS

## Purpose
- Give Copilot/Codex a lightweight operating manual for this repository so generated changes stay safe, scoped, and easy to review.
- Copilot/Codex が安全かつスコープ内で変更を行い、レビューしやすくするための簡潔な運用ガイドです。

## Repository Notes
- Goal: tools to harvest/analyze GitHub review comments. Prioritize clarity and traceability of any data handling.
- Stack defaults: Node.js 20, TypeScript with ESM modules, `npm` for scripts. If introducing tooling, prefer `eslint` + `prettier` + `node --test`.
- Auth: never hardcode tokens. Expect a personal access token via environment variable (e.g., `GITHUB_TOKEN`) and keep it out of git and logs.
- Data: avoid writing outside the repo. If you must cache, use a `.cache/` folder and add it to `.gitignore`.
- 目的：GitHub のレビューコメントを収集・分析するツール。データの扱いは明瞭さと追跡可能性を優先してください。
- 想定スタック：Node.js 20、TypeScript（ESM）、スクリプトは `npm`。新しいツールは `eslint` + `prettier` + `node --test` を優先。
- 認証：トークンはハードコード禁止。`GITHUB_TOKEN` など環境変数で受け取り、git やログに残さない。
- データ出力：リポジトリ外への書き出しは避ける。キャッシュが必要な場合は `.cache/` 配下を使い `.gitignore` へ追記。

## Working Style
- Confirm unknown requirements early; do not invent APIs. Describe the intended inputs/outputs before large implementations.
- Keep dependencies lean; flag any new runtime dependency with a short rationale.
- Tests/docs: add or update minimal coverage and README snippets when behavior changes or new commands are added.
- Changes should stay scoped and explained with concise summaries and sample commands.
- 不明点は早めに確認し、API を憶測で作らない。大きな実装前に入出力を言語化。
- 依存は最小限に保ち、追加が必要なら短い理由を残す。
- 挙動変更やコマンド追加時は最小限でよいのでテストや README を更新。
- 変更範囲は小さく保ち、要約と実行例で説明。

## Git & Templates
- Use feature branches and descriptive commits (avoid "WIP"). Follow the `.github` templates for PRs and issues.
- If CI/tooling is missing, propose a small starter workflow but avoid breaking changes to the default branch.
- フィーチャーブランチと具体的なコミットメッセージ（"WIP" 避ける）を使い、PR/Issue テンプレートに従う。
- CI が未整備でも壊れない最小のワークフローを提案し、デフォルトブランチを壊さない。

## Response Style for Agents
- Default to concise, actionable answers. Include what changed, how to run it, and test results.
- Surface risks or follow-ups explicitly; prefer checklists for manual steps.
- 返答は簡潔かつ実行可能に。変更内容・実行方法・テスト結果を添える。
- リスクやフォロー事項は明示し、手作業はチェックリスト形式で共有。
- 言語: 特に指定がなければ日本語で回答する。英語が必要ならリクエスト時に明記してもらう。
- 不明点が残る場合は、実装前に質問リストを提示して確認を求める。
- 認証・機密チェック: 回答前にトークン/個人情報/秘密情報が出力やログに含まれないか再確認する。

## Japanese Response Prompt
- When the requester wants answers in Japanese, start responses with: `このリポジトリでは日本語で回答してください。変更概要、実行方法、テスト結果を短く教えてください。`
- 日本語での回答が求められたら、上記のプロンプトを先頭に付けてから返信してください。
