---
title: Java virtual method
date: 2025-05-17 05:51:56
tags: ["Java"]
---
在 Java 中，虛擬方法（Virtual Method）是指在執行階段會根據「實際物件的類型」來動態決定要執行哪個方法實作的機制。

這是物件導向程式設計中實現多型（polymorphism）的核心功能之一。

## Java 的虛擬方法定義

在 Java 中，**除了 `static`、`private` 和 `final` 方法之外，所有的方法預設都是虛擬方法**。也就是說，大多數的實例方法都會在執行時被動態繫結（dynamic dispatch）。

## 特性

- 使用父類別參考指向子類別物件時，呼叫的方法會依照「實際物件的類型」決定。
- 呼叫的決策發生在執行階段，而不是編譯階段。
- 支援 override：子類別可以覆寫父類別的方法實作。

## 範例程式碼

```java
class Animal {
    void speak() {
        System.out.println("Animal speaks");
    }
}

class Dog extends Animal {
    @Override
    void speak() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();  // 父類別參考指向 Dog 實體
        a.speak();             // 輸出：Dog barks
    }
}
```

雖然變數 a 是 Animal 型別，但實際物件是 Dog，因此呼叫的是 Dog 類別中的 speak 方法。這就是虛擬方法的行為。

## 非虛擬方法（Non-Virtual Method）

以下幾種方法不是虛擬方法，因為它們不支援 override 或不會被動態繫結：

- static 方法：屬於類別本身
- private 方法：僅能在定義該方法的類別中使用
- final 方法：不允許被子類別覆寫

```java
class Animal {
    static void staticMethod() {
        System.out.println("Animal static");
    }

    private void privateMethod() {
        System.out.println("Animal private");
    }

    final void finalMethod() {
        System.out.println("Animal final");
    }
}
```

## 結論

Java 中的虛擬方法機制是實現多型的關鍵。除非方法被聲明為 `static`、`final` 或 `private`，否則它預設就是虛擬的，會依照執行時的實際物件決定呼叫的版本。
