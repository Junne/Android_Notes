#### Android中的数据转换

----



###### 接口一般返回数据为Json数据，需进行一定的转换为model或者其他数据类型供客户端使用.



###### Android Studio中的插件[RoboPOJOGenerator](https://plugins.jetbrains.com/plugin/8634-robopojogenerator):

* 可以根据返回的json数据自动生成相关的Bean,非常方便。
* 一般可在网络请求时返回的数据直接解析成相关可用的Bean供App使用。



###### 使用Gson解析:

* 一般情况下直接在接口里就已转成Bean,有些接口需要单独再转，可用Gson转换

```kotlin
var data = Gson().fromJson(it, IdentifyCheckBean::class.javaObjectType) // Kotlin
```

```java
User user = new Gson().fromJson(userString, User.class); // Java
```





##### 参考:

* [Android项目之JSON解析](https://blog.csdn.net/qq_29269233/article/details/53352668) 



