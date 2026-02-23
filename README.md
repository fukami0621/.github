# Git基本操作(変更の保存)

---

```
git add .　　                  追加（確定前の準備）
git commit -m "メッセージ"      確定（履歴に保存）
git push                       送信（GitHubへ反映）
```

# Git操作集（新規プロジェクト立ち上げ手順）

---

# ✅ 1) GitHubでリポジトリ（箱）を作る

GitHubの画面で：

① 左上 or 中央の「New」（緑ボタン）を押す  
② Repository name：例 kyushu-boat-elim（好きでOK）  
③ Public / Private：好きでOK（迷ったら Private）

⚠️ ここ重要：
- READMEは作らない（チェック入れない）
- Add .gitignore → None のまま
- License → None のまま

④ 「Create repository」を押す

作成後、リポジトリ画面に移動する。

そこに HTTPSのURL がある：
例）https://github.com/xxxxx/xxxx.git

👉 このURLをあとで使う

---

# ✅ 2) ローカル（Git）で「初回コミット」を作る

ターミナルで：

```bash
cd プロジェクトフォルダ
git init
```

.gitignore を作成（Next.js例）

```gitignore
node_modules
.next
out
.env
.env.local
.DS_Store
```

初回コミット：

```bash
git add .
git commit -m "Initial commit"
```

---

# ✅ 3) ローカルとGitHubを接続（remote追加）

GitHubで確認した HTTPSのURL を使う：

```bash
git branch -M main
git remote add origin https://github.com/xxxxx/xxxx.git
git remote -v
```

確認できたら初回push：

```bash
git push -u origin main
```

これで接続完了。

---

# ✅ 以降の基本運用

```bash
git status
git add .
git commit -m "message"
git push
```

---

# ⚠️ よくあるミス

■ GitHubでREADMEや.gitignoreを作ってしまう  
→ ローカルと衝突する可能性あり

■ remote追加前にpushしようとする  
→ エラーになる

■ mainとmasterの違いで混乱  
→ `git branch -M main` で統一

---

# 🧠 自分ルール（事故防止）

・初回コミットは動作確認後にやる  
・.envは絶対にpushしない  
・毎回 git status を見るクセをつける
