### Android中的数据存储

----

##### Android中的数据存储:

Android 使用的文件系统类似于其他平台上基于磁盘的文件系统。该系统为您提供了以下几种保存应用数据的选项：

- **应用专属存储空间**：存储仅供应用使用的文件，可以存储到内部存储卷中的专属目录或外部存储空间中的其他专属目录。使用内部存储空间中的目录保存其他应用不应访问的敏感信息。
- **共享存储**：存储您的应用打算与其他应用共享的文件，包括媒体、文档和其他文件。
- **偏好设置**：以键值对形式存储私有原始数据。
- **数据库**：使用 Room 持久性库将结构化数据存储在专用数据库中。
- **网络存储**：采用接口存储更新相关数据。



下表汇总了这些选项的特点：

|                                                              | 内容类型                                 | 访问方法                                                     | 所需权限                                                     | 其他应用是否可以访问？                         | 卸载应用时是否移除文件？ |
| :----------------------------------------------------------- | :--------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :--------------------------------------------- | ------------------------ |
| [应用专属文件](https://developer.android.com/training/data-storage/app-specific?hl=zh-cn) | 仅供您的应用使用的文件                   | 从内部存储空间访问，可以使用 `getFilesDir()` 或 `getCacheDir()` 方法  从外部存储空间访问，可以使用 `getExternalFilesDir()`或 `getExternalCacheDir()`方法 | 从内部存储空间访问不需要任何权限  如果应用在搭载 Android 4.4（API 级别 19）或更高版本的设备上运行，从外部存储空间访问不需要任何权限 | 否                                             | 是                       |
| [媒体](https://developer.android.com/training/data-storage/shared/media?hl=zh-cn) | 可共享的媒体文件（图片、音频文件、视频） | `MediaStore` API                                             | 在 Android 11（API 级别 30）或更高版本中，访问其他应用的文件需要 `READ_EXTERNAL_STORAGE`  在 Android 10（API 级别 29）中，访问其他应用的文件需要 `READ_EXTERNAL_STORAGE` 或 `WRITE_EXTERNAL_STORAGE`  在 Android 9（API 级别 28）或更低版本中，访问**所有**文件均需要相关权限 | 是，但其他应用需要 `READ_EXTERNAL_STORAGE`权限 | 否                       |
| [文档和其他文件](https://developer.android.com/training/data-storage/shared/documents-files?hl=zh-cn) | 其他类型的可共享内容，包括已下载的文件   | 存储访问框架                                                 | 无                                                           | 是，可以通过系统文件选择器访问                 | 否                       |
| [应用偏好设置](https://developer.android.com/training/data-storage/shared-preferences?hl=zh-cn) | 键值对                                   | [Jetpack Preferences](https://developer.android.com/guide/topics/ui/settings/use-saved-values?hl=zh-cn) 库 | 无                                                           | 否                                             | 是                       |
| 数据库                                                       | 结构化数据                               | [Room](https://developer.android.com/training/data-storage/room?hl=zh-cn) 持久性库 | 无                                                           | 否                                             | 是                       |



在很多情况下，您的应用会创建其他应用不需要访问或不应访问的文件。系统提供以下位置，用于存储此类应用专属文件：

- **内部存储空间目录**：这些目录既包括用于存储持久性文件的专属位置，也包括用于存储缓存数据的其他位置。系统会阻止其他应用访问这些位置，并且在 Android 10（API 级别 29）及更高版本中，系统会对这些位置进行加密。这些特征使得这些位置非常适合存储只有应用本身才能访问的敏感数据。
- **外部存储空间目录**：这些目录既包括用于存储持久性文件的专属位置，也包括用于存储缓存数据的其他位置。虽然其他应用可以在具有适当权限的情况下访问这些目录，但存储在这些目录中的文件仅供您的应用使用。如果您明确打算创建其他应用能够访问的文件，您的应用应改为将这些文件存储在外部存储空间的[共享存储空间](https://developer.android.com/training/data-storage/shared?hl=zh-cn)部分。

###### 从内部存储空间访问:

###### 从外部存储空间访问: 



##### 使用Room将数据保存到本地数据库

Room 持久性库在 SQLite 上提供了一个抽象层，以便在充分利用 SQLite 的强大功能的同时，能够流畅地访问数据库。具体来说，Room 具有以下优势：

- 针对 SQL 查询的编译时验证。
- 可最大限度减少重复和容易出错的样板代码的方便注解。
- 简化了数据库迁移路径。





#### 参考:

* [Android四种数据存储的应用方式](https://cloud.tencent.com/developer/article/1726116) 

* [数据和文件存储概览](https://developer.android.com/training/data-storage?hl=zh-cn) 

* [访问应用专属文件](https://developer.android.com/training/data-storage/app-specific?hl=zh-cn) 

* [一文搞懂Android内部存储和外部存储](https://www.jianshu.com/p/a39bc4b3a1a6) 

* [Android数据存储五种方式使用与总结](https://github.com/Mr-YangCheng/ForAndroidInterview/blob/master/android/Android%20数据存储五种方式使用与总结.md) 

* [使用Room将数据保存在本地数据库](https://developer.android.google.cn/training/data-storage/room?hl=zh-cn#kts) 

* [A gardening app illustrating Android development best practices with Android Jetpack.](https://github.com/android/sunflower)

* [将Room的使用方式塞到脑子里记下来](https://juejin.cn/post/6992875656707211271) 

* [Kotlin中的单例](https://juejin.cn/post/6844903590545326088) 

  
