---
title: Python dotenv
date: 2021-09-30T21:17:56+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[dotenv](https://github.com/theskumar/python-dotenv)

dotenv 會讀取 `.env` 這個檔案裡面的 `key-value`

並設定成環境變數

`.env`

```env
# Development settings
DOMAIN=example.org
ADMIN_EMAIL=admin@${DOMAIN}
ROOT_URL=${DOMAIN}/app
```

使用方法

```python
from dotenv import load_dotenv

load_dotenv()  # take environment variables from .env.

# Code of your application, which uses environment variables (e.g. from `os.environ` or
# `os.getenv`) as if they came from the actual environment.
```
