# Hooks設定ガイド（サンプル）
## コミット前に自動でコード品質をチェックする

---

## Hooksとは

Claude Codeの Hooks は、特定のイベントが発生したときに  
自動でコマンドを実行する仕組みです。

```
コミット実行
    ↓
Hookが発動
    ↓
自動チェック（lint / test / セキュリティスキャン）
    ↓
問題なし → コミット完了
問題あり → コミット中断 + 警告
```

---

## 設定場所

`.claude/settings.json` に追記します：

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "echo '[Hook] ファイル変更を検知しました'"
          }
        ]
      }
    ]
  }
}
```

---

## サンプル：コミット前のlintチェック

```json
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "if git diff --staged --name-only | grep -q '\\.ts$\\|\\.tsx$'; then npm run lint --quiet; fi"
          }
        ]
      }
    ]
  }
}
```

---

## サンプル：.envファイルの誤コミット防止

```json
{
  "hooks": {
    "PreToolUse": [
      {
        "matcher": "Write|Edit",
        "hooks": [
          {
            "type": "command",
            "command": "python3 -c \"\nimport sys, json\ndata = json.load(sys.stdin)\npath = data.get('file_path', '')\nif '.env' in path and not path.endswith('.example'):\n    print('ERROR: .envファイルへの書き込みを検知しました', file=sys.stderr)\n    sys.exit(1)\n\""
          }
        ]
      }
    ]
  }
}
```

---

## 注意事項

- Hooks は `.claude/settings.json` （チーム共通）に設定
- 個人だけに適用したい場合は `.claude/settings.local.json` に設定
- `settings.local.json` は `.gitignore` に追加する

---

## 完全版のHooksセット

このサンプルは Hooks の概念を示すものです。

完全版には：
- セキュリティ違反の自動検知フック
- 認証情報のハードコード検出フック
- コスト超過アラートフック
- 自動コミットメッセージ生成フック
- テスト失敗時の自動ロールバックフック
- チーム通知フック（Slack連携）

**[完全版を入手する → ¥9,800](https://gumroad.com/[username])**
