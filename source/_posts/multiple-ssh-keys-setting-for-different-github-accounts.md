---
title: 為不同的 GitHub 帳號設定多把 SSH key
date: 2024-10-23 11:44:18
tags: [GitHub]
---
如果有多個 github 帳號（例如個人用，工作用）

如何在同一台電腦上各自設定 SSH key

## step 1 產生 SSH key

```bash
ssh-keygen -t ed25519 -C "your_email@personal.com" -f ~/.ssh/github-personal
```

```bash
ssh-keygen -t ed25519 -C "your_email@company.com" -f ~/.ssh/github-work
```

這指令會生成新的 SSH 私鑰並將其存儲在 ~/.ssh/github-work 中，公鑰也會存儲在同樣路徑下，檔案名稱為 github-work.pub

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

personal 的公鑰（`~/.ssh/github-personal.pub`）也用同樣的方式，加到另一個 GitHub 帳號

## step 3 編輯 ~/.ssh/config 檔案

```text
Host github-work
    HostName github.com
    User git
    IdentityFile ~/.ssh/github-work
    IdentitiesOnly yes

Host github-personal
    HostName github.com
    User git
    IdentityFile ~/.ssh/github-personal
    IdentitiesOnly yes
```

如果希望沒有修改 Host 的網址（`git@github.com:...`）也能使用某個預設帳號，可以再加上 `github.com` 的設定

```text
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/id_rsa
    IdentitiesOnly yes
```

`IdentityFile` 可以換成想當作預設帳號的私鑰，例如 `~/.ssh/github-personal`

也可以追加下列設定

```text
Host *
    AddKeysToAgent yes
    UseKeychain yes
```

SSH 對同一個選項會採用第一個符合的值，所以 `Host *` 這類通用設定建議放在檔案最後面，避免蓋掉前面個別 Host 的設定

### 設定說明

- Host: 本地的 SSH 別名，可以是任何你想要的名稱
- HostName: 用來指定實際的伺服器主機名或 IP 地址
- User: 登入用戶名，GitHub上必須設為 git
- IdentityFile: 指定用戶連接到主機時所使用的私鑰檔案
- IdentitiesOnly: 設為 yes 時，只使用 IdentityFile 指定的私鑰，不會去嘗試 SSH agent 裡的其他金鑰。多帳號時一定要加，否則 SSH 可能先用到另一個帳號的金鑰並認證成功，導致以錯誤的帳號身分操作
- AddKeysToAgent: 用來自動將 SSH 私鑰添加到 SSH agent 中
- UseKeychain: 在 macOS 上，這選項讓 SSH agent 將私鑰存儲在 macOS 的 Keychain 中，進一步減少輸入密碼的頻率

## step 4 測試連接

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

成功的話會看到類似下面的訊息，可以從 username 確認連到的是哪個帳號

```text
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

### （選用）查看 SSH agent 中的金鑰

因為 config 中已經用 `IdentityFile` 指定私鑰，SSH 會直接讀取該檔案，不需要手動加進 SSH agent

如果想確認 agent 中目前有哪些金鑰，可以使用下列命令

```bash
ssh-add -l
```

需要手動加入時，可以使用下列命令

```bash
ssh-add ~/.ssh/github-work
```

## step 5 使用 SSH 進行 Clone

在 GitHub 上找到你想要 clone 的 SSH URL

通常是這樣

```text
git@github.com:username/repository.git
```

如果修改成自行設定的 `Host`

```bash
git clone git@github-work:username/repository.git
```

`git clone` 命令會使用 SSH 配置中的 `Host github-work`，並按照該配置文件中的設定，使用正確的私鑰（如 ~/.ssh/github-work）連接到 GitHub

## PS1 修改遠端 URL 的方法

使用以下命令檢查當前的遠端 URL

```bash
git remote -v
```

修改 origin 的 URL 並使用自定義的 Host（例如 github-work）

```bash
git remote set-url origin git@github-work:username/repository.git
```

## PS2 git config

設定 Git 的 commit 使用的名稱（name）和電子郵件（email）

```bash
git config user.email "your_email@company.com"
git config user.name "work"
```

## References

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
