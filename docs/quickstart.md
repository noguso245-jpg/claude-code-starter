# 30分セットアップガイド
## Claude Code Starter Kit

---

## 前提条件

- [ ] Claude Codeがインストール済み（`claude --version` で確認）
- [ ] プロジェクトディレクトリが存在する

Claude Codeが未インストールの場合：
```bash
npm install -g @anthropic-ai/claude-code
```

---

## Step 1：テンプレートをコピー（5分）

```bash
# プロジェクトのルートディレクトリで実行
mkdir -p .claude

# このリポジトリのテンプレートをコピー
cp /path/to/claude-code-starter/templates/CLAUDE.md .claude/CLAUDE.md
```

---

## Step 2：プロジェクト情報を記入（10分）

`.claude/CLAUDE.md` を開いて、以下を埋めてください：

```markdown
## Project Overview

- **Type**: Web Application
- **Stack**: Next.js + Node.js + PostgreSQL  ← あなたのスタックに変更
- **Stage**: MVP
- **Team Size**: Solo
```

**ポイント：**
- スタックを正確に書くと、Claude Codeが正しいコードを生成する
- 「やってはいけないこと」セクションは特に重要。カスタマイズ推奨

---

## Step 3：動作確認（5分）

```bash
# Claude Codeを起動
claude

# 最初のコマンドで確認
> /overview
```

CLAUDE.mdの内容がClaudeに読み込まれていることを確認してください。

---

## Step 4：最初のタスクを試す（10分）

```
> このプロジェクトの構造を理解して、最初に何をすべきか教えて
```

設定前と比較して、回答の精度が上がっているはずです。

---

## よくある質問

**Q: CLAUDE.mdはどこに置くべきか？**  
A: プロジェクトルートの `.claude/` フォルダ内。またはプロジェクトルート直下。

**Q: 内容はどれくらい書くべきか？**  
A: 50〜150行が最適。200行を超えると効果が落ちる。

**Q: チームで使う場合は？**  
A: `.claude/CLAUDE.md` をGitにコミットしてチームで共有。個人設定は `.claude/CLAUDE.local.md` に分離。

**Q: モデルが変わったら更新が必要？**  
A: ワークフローの型は変わらない。モデル名などの設定値だけ更新が必要。

---

## 次のステップ

このテンプレートで効果を感じたら、**完全版**を試してください。

完全版の追加内容：
- CLAUDE.md テンプレート（残り6種）：API開発用、マイグレーション用、OSS用、チーム用、セキュリティ監査用、スタートアップ用
- Hooks設定完全セット（エラー検知・自動コミット・品質チェック）
- MCP設定済みスタック3種（GitHub・Notion・Slack）
- 53の実行可能スキル
- カスタムコマンド10個（`/plan`, `/review`, `/debug`, etc.）

**[完全版を入手する → ¥9,800](https://gumroad.com/[username])**

---

問題があれば Issues でお気軽に。
