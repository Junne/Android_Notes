## Android中的加密算法
----



##### 1.Base64

* 维基百科中的释义:**Base64**（基底64）是一种基于64个可打印字符来表示[二进制数据](https://zh.wikipedia.org/wiki/二进制)的表示方法。由于log2⁡64=6![{\displaystyle \log _{2}64=6}](https://wikimedia.org/api/rest_v1/media/math/render/svg/9c986fbdc6c036a937e0647d7a6ec5ad745bccab)，所以每6个[位元](https://zh.wikipedia.org/wiki/位元)为一个单元，对应某个可打印字符。3个[字节](https://zh.wikipedia.org/wiki/字节)相當於24个位元，对应于4个Base64单元，即3个字节可由4个可打印字符来表示。在Base64中的可打印字符包括[字母](https://zh.wikipedia.org/wiki/拉丁字母)`A-Z`、`a-z`、[数字](https://zh.wikipedia.org/wiki/数字)`0-9`，这样共有62个字符，此外两个可打印符号在不同的系统中而不同。一些如[uuencode](https://zh.wikipedia.org/wiki/Uuencode)的其他编码方法，和之后[BinHex](https://zh.wikipedia.org/w/index.php?title=BinHex&action=edit&redlink=1)的版本使用不同的64字符集来代表6个二进制数字，但是不被称为Base64。Base64常用于在通常处理文本[数据](https://zh.wikipedia.org/wiki/数据)的场合，表示、传输、存储一些二进制数据，包括[MIME](https://zh.wikipedia.org/wiki/MIME)的[电子邮件](https://zh.wikipedia.org/wiki/电子邮件)及[XML](https://zh.wikipedia.org/wiki/XML)的一些复杂数据。

* Kotlin中实现Base64的加解密:

  ```kotlin
      private fun testBase64() {
          val text = "Hello World!"
          val byteArray = text.toByteArray(Charsets.UTF_8)
          val encode = Base64.encodeToString(byteArray, Base64.DEFAULT)
          Log.d("testBase64==", encode)
  
          val decode: String? = String(Base64.decode(encode, Base64.DEFAULT),Charsets.UTF_8)
          Log.d("testBase64=", decode.toString())
      }
  ```

* 用途  主要用于精简数据的传输、简单的加解密（不安全）图片数据的传输

##### 2.对称加密  加解密秘钥相同，加密速度快，适合经常发送数据的场合。缺点为秘钥传输比较麻烦。











##### 参考:

* [Andorid中的加密算法总结](https://www.jianshu.com/p/9c5db51d3efc) 
* [什么是Base64算法？](https://blog.csdn.net/qq_19782019/article/details/88117150) 
* [加密算法测试工具](https://tool.chinaz.com/Tools/Base64.aspx) 
