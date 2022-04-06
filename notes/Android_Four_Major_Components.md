

###  Android四大组件

---

##### 四大组件:1.Activity 2.Service 3.Broadcast Receive 4.Content Provider

Android 开发的四大组件分别是：活动（activity），用于表现功能；服务（service），后台运行服务，不提供界面呈现；广播接受者（Broadcast Receive），勇于接收广播；内容提供者（Content Provider），支持多个应用中存储和读取数据，相当于数据库。

##### 1.[Activity](https://developer.android.com/guide/components/activities/intro-activities?hl=zh-cn) 

* Activity 提供窗口供应用在其中绘制界面。此窗口通常会填满屏幕，但也可能比屏幕小，并浮动在其他窗口上面。通常，一个 Activity 实现应用中的一个屏幕。例如，应用中的一个 Activity 实现“偏好设置”屏幕，而另一个 Activity 实现“选择照片”屏幕。

* 要使应用能够使用 Activity，您必须在清单中声明 Activity 及其特定属性。此元素唯一的必要属性是 [android:name](https://developer.android.com/guide/topics/manifest/activity-element?hl=zh-cn#nm)，该属性用于指定 Activity 的类名称。

  ```
      <manifest ... >
        <application ... >
            <activity android:name=".ExampleActivity" />
            ...
        </application ... >
        ...
      </manifest >
  ```

* 通过Intent显式或者隐式启动Activity.

* [Activty的生命周期](https://developer.android.com/guide/components/activities/activity-lifecycle?hl=zh-cn) :

  ![Activity生命周期简化图示](https://developer.android.com/guide/components/images/activity_lifecycle.png?hl=zh-cn)

* Fragment

   

  

  

  













#### 参考:

* [Android四大组件](https://blog.csdn.net/xchaha/article/details/80398620) 
* [Android Fragment使用解析](https://juejin.cn/post/6844903816240857095) 
* [Android必知必会的四大组件-Service](https://juejin.cn/post/6844904071749435406) 
