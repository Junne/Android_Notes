### Android UI

---



##### **基础**

**ID**：任何 View 对象均可拥有与之关联的整型 ID，用于在结构树中对 View 对象进行唯一标识。

```
android:id="@+id/my_button"
```

**布局参数**：

![定义布局参数](https://developer.android.com/images/layoutparams.png?hl=zh-cn) 

所有视图组均包含宽度和高度（`layout_width` 和 `layout_height`），并且每个视图都必须定义它们。

- wrap_content 指示您的视图将其大小调整为内容所需的尺寸。
- match_parent 指示您的视图尽可能采用其父视图组所允许的最大尺寸。





**线性布局LinearLayout**

**相对布局RelativeLayout**

**RecyclerView**









##### 参考:

* [Android Developer 布局教程](https://developer.android.com/guide/topics/ui/declaring-layout?hl=zh-cn) 
* [Android UI布局](http://gitbook.net/android/android_user_interface_layouts.html) 
* [Android常用布局及属性](https://cloud.tencent.com/developer/article/1394185) 
* [ConstraintLayout完全解读](https://blog.csdn.net/guolin_blog/article/details/53122387) 
