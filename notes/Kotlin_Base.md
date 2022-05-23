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

**类**

```kotlin
class Person{ /**....**/ }
```

**抽象类**

* 类以及其中的某些或全部成员可以声明为 `abstract`。 抽象成员在本类中可以不用实现。 并不需要用 `open` 标注抽象类或者函数。

**接口**

```kotlin
interface MyInterface {
    fun bar()
    fun foo() {
      // 可选的方法体
    }
}

// 实现接口
class Child : MyInterface {
    override fun bar() {
        // 方法体
    }
}

interface MyInterface {
    val prop: Int // 抽象的

    val propertyWithImplementation: String
        get() = "foo"

    fun foo() {
        print(prop)
    }
}

class Child : MyInterface {
    override val prop: Int = 29
}
```

**可见性修饰符**

* 在 Kotlin 中有这四个可见性修饰符：`private`、 `protected`、 `internal` 和 `public`。 默认可见性是 `public`。
* 如果你不使用任何可见性修饰符，默认为 `public`，这意味着你的声明将随处可见。
* 如果你声明为 `private`，它只会在声明它的文件内可见。
* 如果你声明为 `internal`，它会在相同[模块](https://book.kotlincn.net/text/visibility-modifiers.html#模块)内随处可见。
* `protected` 修饰符不适用于顶层声明。







##### 参考:

* [Kotlin官方文档中文版](https://book.kotlincn.net) 
