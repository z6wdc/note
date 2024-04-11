---
title: MongoDB install
date: 2024-04-11 19:38:11
categories: ["en"]
tags: ["MongoDB"]
---
## Install MongoDB Community Edition on macOS

### Install

```
brew tap mongodb/brew
brew update
brew install mongodb-community@7.0
```

### Run

```
brew services start mongodb-community@7.0
```

### Stop

```
brew services stop mongodb-community@7.0
```

### Connect

```
mongosh
```

## Reference
https://www.mongodb.com/docs/manual/installation/
