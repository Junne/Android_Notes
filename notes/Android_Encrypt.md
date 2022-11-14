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

* [什么是DES加密?](https://www.zhihu.com/question/36767829) 

* DES加密算法原理(图片来自GeneralAndroid ):

  ![DES原理图](https://pica.zhimg.com/80/v2-5c8662f473220a8cd18f5622f4e412e8_1440w.jpg?source=1940ef5c)

  

  * 3DES 3DES（或称为Triple DES）是三重[数据加密算法](https://links.jianshu.com/go?to=https%3A%2F%2Fbaike.baidu.com%2Fitem%2F%E6%95%B0%E6%8D%AE%E5%8A%A0%E5%AF%86%E7%AE%97%E6%B3%95%2F3030864)（TDEA，Triple Data Encryption Algorithm）块密码的通称。是DES向AES过渡的加密算法，它使用3条56位的密钥对数据进行三次加密。是DES的一个更安全的变形。它以DES为基本模块，通过组合分组方法设计出分组加密算法。比起最初的DES，3DES更为安全。

  * AES AES全称Advanced Encryption Standard，即高级加密标准，当今最流行的对称加密算法之一，是DES的替代者。支持三种长度的密钥：128位，192位，256位。

    AES算法是把明文拆分成一个个独立的明文块，每一个明文块长128bit。这些明文块经过AES加密器的复杂处理，生成一个个独立的密文块，这些密文块拼接在一起，就是最终的AES加密结果。

    一般是通过RSA加密AES的密钥，传输到接收方，接收方解密得到AES密钥，然后发送方和接收方用AES密钥来通信。

  

  

  ##### 3.非对称加密

  * SHA  [SHA256算法原理详解](https://blog.csdn.net/u011583927/article/details/80905740)   安全散列算法（英语：Secure Hash Algorithm，缩写为SHA）是一个密码散列函数家族，是FIPS所认证的安全散列算法。能计算出一个数字消息所对应到的，长度固定的字符串（又称消息摘要）的算法，且若输入的消息不同，它们对应到不同字符串的机率很高。
    SHA分为SHA-1、SHA-224、SHA-256、SHA-384，和SHA-512五种算法，后四者有时并称为SHA-2。SHA-1在许多安全协定中广为使用，包括TLS和SSL、PGP、SSH、S/MIME和IPsec，曾被视为是MD5（更早之前被广为使用的杂凑函数）的后继者。但SHA-1的安全性如今被密码学家严重质疑；虽然至今尚未出现对SHA-2有效的攻击，它的算法跟SHA-1基本上仍然相似；因此有些人开始发展其他替代的杂凑算法。

    优点:破解难度高，不可逆。 缺点:可以通过穷举法破解。

  * RSA RSA算法1978年出现，是第一个既能用于数据加密也能用于数字签名的算法，易于理解和操作。
    RSA基于一个数论事实：将两个大素数相乘十分容易，但想要对其乘积进行因式分解却极其困难，因此可以将乘积公开作为加密密钥，即公钥，而两个大素数组合成私钥。公钥是可提供给任何人使用，私钥则为自己所有，供解密之用。[RSA算法原理](https://www.ruanyifeng.com/blog/2013/06/rsa_algorithm_part_one.html) 

    - 优点：不可逆，既能用于数据加密，也可以应用于数字签名。
    - 缺点：RSA非对称加密内容长度有限制，1024位key的最多只能加密127位数据。

  * MD5 **MD5信息摘要算法**（英语：MD5 Message-Digest Algorithm），[MD5算法详解](https://blog.csdn.net/goodnameused/article/details/81068697) 一种被广泛使用的密码散列函数，可以产生出一个128位（16字节）的散列值，用于确保信息传输完整一致。具有如下优点：
    - 压缩性：任意长度的数据，算出的MD5值长度都是固定的。
    - 容易计算：从原数据计算出MD5值很容易。
    - 抗修改性：对原数据进行任何改动，所得到的MD5值都有很大区别。
    - 强抗碰撞：已知原数据和其MD5值，想找到一个相同MD5值得数据是非常困难的。

  * XOR XOR：异或加密，既将某个字符或者数值 x 与一个数值 m 进行异或运算得到 y ，则再用 y 与 m 进行异或运算就可还原为 x。
    使用场景：
    （1）两个变量的互换（不借助第三个变量）；
    （2）数据的简单加密解密。



##### 国密算法

* 国产密码算法（国密算法）是指国家密码局认定的国产商用密码算法，在金融领域目前主要使用公开的SM2、SM3、SM4三类算法，分别是非对称算法、哈希算法和对称算法。

* SM2算法：非对称算法。SM2椭圆曲线公钥密码算法是我国自主设计的公钥密码算法，包括SM2-1椭圆曲线数字签名算法，SM2-2椭圆曲线密钥交换协议，SM2-3椭圆曲线公钥加密算法，分别用于实现数字签名密钥协商和数据加密等功能。SM2算法与RSA算法不同的是，SM2算法是基于椭圆曲线上点群离散对数难题，相对于RSA算法，256位的SM2密码强度已经比2048位的RSA密码强度要高。

* SM3算法：SM3杂凑算法是我国自主设计的密码杂凑算法，适用于商用密码应用中的数字签名和验证消息认证码的生成与验证以及随机数的生成，可满足多种密码应用的安全需求。为了保证杂凑算法的安全性，其产生的杂凑值的长度不应太短，例如MD5输出128比特杂凑值，输出长度太短，影响其安全性SHA-1算法的输出长度为160比特，SM3算法的输出长度为256比特，因此SM3算法的安全性要高于MD5算法和SHA-1算法。

*  SM4算法：SM4分组密码算法是我国自主设计的分组对称密码算法，用于实现数据的加密/解密运算，以保证数据和信息的机密性。要保证一个对称密码算法的安全性的基本条件是其具备足够的密钥长度，SM4算法与AES算法具有相同的密钥长度分组长度128比特，因此在安全性上高于3DES算法。





##### 参考:

* [Andorid中的加密算法总结](https://www.jianshu.com/p/9c5db51d3efc) 
* [什么是Base64算法？](https://blog.csdn.net/qq_19782019/article/details/88117150) 
* [加密算法测试工具](https://tool.chinaz.com/Tools/Base64.aspx) 
* [AES加密算法的详细介绍与实现](https://blog.csdn.net/qq_28205153/article/details/55798628) 
* [国产算法概述](https://www.cnblogs.com/peterYong/p/15043372.html) 



