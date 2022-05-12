### Kotlin基础

---





###### Kotlin基础

**变量**

* 定义只读局部变量使用关键字 `val` 定义。只能为其赋值一次。 
* 可重新赋值的变量使用 `var` 关键字。



**类与实例**

* 类之间继承由冒号（`:`）声明。默认情况下类都是 final 的；如需让一个类可继承， 请将其标记为 `open`。



**for循环**

```kotlin
#Sample 1:
    val items = listOf("apple", "banana", "kiwifruit")
    for (item in items) {
        println(item)
    }

#Sample 2:
    val items = listOf("apple", "banana", "kiwifruit")
    for (index in items.indices) {
        println("item at $index is ${items[index]}")
    }
```

**while循环**

```kotlin
    val items = listOf("apple", "banana", "kiwifruit")
    var index = 0
    while (index < items.size) {
        println("item at $index is ${items[index]}")
        index++
    }
```

**when表达式**

```kotlin
fun describe(obj: Any): String =
    when (obj) {
        1          -> "One"
        "Hello"    -> "Greeting"
        is Long    -> "Long"
        !is String -> "Not a string"
        else       -> "Unknown"
    }
```

**过滤与映射**

```kotlin
    val fruits = listOf("banana", "avocado", "apple", "kiwifruit")
    fruits
      .filter { it.startsWith("a") }
      .sortedBy { it }
      .map { it.uppercase() }
      .forEach { println(it) }
```











##### 参考:

* [Kotlin官方文档中文版](https://book.kotlincn.net) 
