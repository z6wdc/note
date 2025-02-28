---
title: "Python Requests パラメータ allow_redirects"
date: 2022-12-11T14:59:56+09:00
tags: ["Python"]
---
## allow_redirects

`Request`は（`HEAD`以外）デフォルトリダイレクトする

`history`のプロパティでリダイレクトされたかの歴史を追跡できる

### 例

GitHub は`HTTP`を`HTTPS`にリダイレクトする

```python:default
>>> r = requests.get('http://github.com/')

>>> r.url
'https://github.com/'

>>> r.status_code
200

>>> r.history
[<Response [301]>]
```

`allow_redirects=False`を設定すると、リダイレクトをしない

```python:allow_directs=False
>>> r = requests.get('http://github.com/', allow_redirects=False)

>>> r.status_code
301

>>> r.history
[]
```

`HEAD`の場合、デフォルトはリダイレクトしない

リダイレクトをしたい場合、`allow_redirects=True`を設定すれば

```python:allow_directs=True
>>> r = requests.head('http://github.com/', allow_redirects=True)

>>> r.url
'https://github.com/'

>>> r.history
[<Response [301]>]
```

## 参考

https://docs.python-requests.org/en/latest/user/quickstart/#redirection-and-history
