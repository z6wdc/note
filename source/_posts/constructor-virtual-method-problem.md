---
title: constructor virtual method problem
date: 2025-05-17 06:03:46
tags: ["Java"]
---
在 Java 中，如果你在建構子內呼叫了一個「可以被子類覆寫」的方法（也就是虛擬方法 / 非 `final` / 非 `private` 的方法）

而該方法實際上在子類中有實作，這會導致父類建構子呼叫時，**執行的是子類的版本**

但此時子類的欄位還沒初始化完成，可能發生以下問題：

- `NullPointerException`
- 初始化邏輯錯誤
- 難以除錯的 bug


## 範例：錯誤使用

```java
class Parent {
    public Parent() {
        System.out.println("Parent constructor start");
        init(); // 呼叫虛擬方法
        System.out.println("Parent constructor end");
    }

    protected void init() {
        System.out.println("Parent init");
    }
}

class Child extends Parent {
    private String message = "Hello";

    public Child() {
        System.out.println("Child constructor");
    }

    @Override
    protected void init() {
        System.out.println("Child init: " + message.length()); // NPE 發生
    }
}
```

```java
Child c = new Child();
```

### 輸出結果

```
Parent constructor start
Exception in thread "main" java.lang.NullPointerException
```

## 原因

Java 的物件建構流程是：先執行父類別建構子 → 再執行子類別建構子

但 init() 是 `virtual method`，因此在 Parent() 裡呼叫會走向 Child.init()

而此時 Child 的建構子還沒開始跑 → 欄位尚未初始化


## 實務範例：Service 初始化失敗

```java
abstract class BaseService {
    public BaseService() {
        init(); // 呼叫虛擬方法
    }

    protected abstract void init();
}

class UserService extends BaseService {
    private UserRepository userRepository;

    public UserService() {
        this.userRepository = new UserRepository(); // 尚未初始化
    }

    @Override
    protected void init() {
        userRepository.connect(); // 這裡會 NPE
    }
}
```

## 正確寫法

### 1. 在子類 constructor 中主動呼叫

```java
class UserService extends BaseService {
    private UserRepository userRepository;

    public UserService() {
        this.userRepository = new UserRepository();
        init(); // 子類自行控制時機
    }

    @Override
    protected void init() {
        userRepository.connect();
    }
}
```

### 2. 使用工廠模式或建構器（Builder）

```java
class UserService extends BaseService {
    private final UserRepository userRepository;

    public UserService(UserRepository userRepository) {
        this.userRepository = userRepository;
    }

    @Override
    protected void init() {
        userRepository.connect();
    }
}
```

## 避免錯誤的原則

| 原則 | 說明 |
|------|------|
| ❌ 建構子內呼叫虛擬方法 | 子類尚未初始化，可能導致 NPE |
| ✅ 在子類中手動呼叫 | 子類控制初始化時機 |
| ✅ 使用組合代替繼承 | 避免虛擬呼叫的風險 |
| ✅ 使用 `final` 或 `private` 方法 | 保證建構期內方法不會被覆寫 |


## 總結

在 constructor 中呼叫會被覆寫的方法是 Java 中著名的設計陷阱。實務上應：

- 儘量避免繼承中帶有邏輯的 constructor
- 初始化責任應交給子類
- 改用組合與明確初始化階段（例如 `init()`、`setup()` 方法）

這樣可以讓程式碼更穩定、可預測、也更容易維護。
