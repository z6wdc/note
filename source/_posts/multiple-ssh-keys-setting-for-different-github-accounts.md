---
title: 為不同的 GitHub 帳號設定多把 SSH key
date: 2024-10-23 11:44:18
tags: [GitHub]
---
如果有多個 github 帳號（例如個人用，工作用）

如何在同一台電腦上各自設定 SSH key

## step1 產生 SSH key

```bash
ssh-keygen -t ed25519 -C "your_email@personal.com" -f "github-personal"
```

```bash
ssh-keygen -t ed25519 -C "your_email@company.com" -f "github-work"
```

這指令會生成新的 SSH 私鑰並將其存儲在 github-work 中，公鑰也會存儲在同樣路徑下，檔案名稱為 github-work.pub

### option 說明

- -t: 用來指定 key 的類型
- -C: 用來更改 key 的註解
- -f: 用來指定生成或操作 key 時的檔案名稱或路徑

## step 2 複製 SSH 公鑰到 GitHub

```bash
pbcopy < ~/.ssh/github-work.pub
```

如果是 mac 的話可以用上述指令複製 ssh 公鑰

接著到 GitHub 頁面，進入 Settings → SSH and GPG keys → New SSH key，將複製的公鑰貼上

## step 3 編輯 ~/.ssh/config 檔案

```bash
Host github-work
    HostName github.com
    User git
    IdentityFile ~/.ssh/github-work

Host github-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/github-personal
```

也可以追加下列設定

```bash
Host *
    AddKeysToAgent yes
    UseKeychain yes
```

### 設定說明

- Host: 本地的 SSH 別名，可以是任何你想要的名稱
- HostName: 用來指定實際的伺服器主機名或 IP 地址
- User: 登入用戶名，GitHub上必須設為 git
- IdentityFile: 指定用戶連接到主機時所使用的私鑰檔案
- AddKeysToAgent: 用來自動將 SSH 私鑰添加到 SSH agent 中
- UseKeychain: 在 macOS 上，這選項讓 SSH agent 將私鑰存儲在 macOS 的 Keychain 中，進一步減少輸入密碼的頻率

### step4 測試連接

```bash
ssh -T github-work
```

```bash
ssh -T github-personal
```

或

```bash
ssh -T git@github-work
```

```bash
ssh -T git@github-personal
```

也可以使用下列命令查看當前正在使用的金鑰

```bash
ssh-add -l
```

如果 `work` 的金鑰沒有在列表中，可以使用下列命令將它添加進來

```
ssh-add ~/.ssh/github-work
```

### step5 使用 SSH 進行 Clone

在 GitHub 上找到你想要 clone 的  SSH URL

通常是這樣

```
git@github.com:username/repository.git
```

如果修改成自行設定的 `Host`

```
git clone git@github-work:username/repository.git
```

`git clone` 命令會使用 SSH 配置中的 `Host github-work`，並按照該配置文件中的設定，使用正確的私鑰（如 ~/.ssh/github-work）連接到 GitHub

### PS1 修改遠端 URL 的方法

使用以下命令檢查當前的遠端 URL

```bash
git remote -v
```

修改 origin 的 URL 並使用自定義的 Host（例如 github-work）

```bash
git remote set-url origin git@github-work:username/repository.git
```

### PS2 git config

設定 Git 的 commit 使用的名稱（name）和電子郵件（email）

```bash
git config user.email "your_email@company.com"
git config user.name "work"
```

### References

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent