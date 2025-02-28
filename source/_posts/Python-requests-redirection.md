---
title: Python requests redirection
date: 2021-09-30T21:23:52+09:00
tags: ["Python"]
---
[Redirection and History](https://docs.python-requests.org/en/latest/user/quickstart/#redirection-and-history)

requests 預設會自動 redirect

```python
import requests

r = requests.get('http://github.com/')
r.status_code
# 200

r.history
# [<Response [301]>]
```

但可以用 `allow_redirects` 關掉

```python
import requests

r = requests.get('http://github.com/', allow_redirects=False)

r.status_code
#301

r.history
#[]
```
