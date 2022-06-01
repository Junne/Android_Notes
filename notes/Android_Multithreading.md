### Android中的多线程

---

##### 进程和线程:

”**进程是资源分配的最小单位，线程是CPU调度的最小单位“**

**进程**:进程是对运行时程序的封装，是**系统进行资源调度和分配的的基本单位，实现了操作系统的并发**

**线程**:是进程的子任务，**是CPU调度和分派的基本单位**，**用于保证程序的实时性，实现进程内部的并发；线程是操作系统可识别的最小执行和调度单位**。每个线程都独自占用一个**虚拟处理器**：独自的**寄存器组**，**指令计数器和处理器状态**。每个线程完成不同的任务，但是**共享同一地址空间**（也就是同样的**动态内存，映射文件，目标代码等等**），**打开的文件队列和其他内核资源**。

---

##### 多线程使用:

**适用范围**：善于在 Android 上利用线程可以帮助您提升应用的性能。

**主线程**:当用户启动您的应用时，Android 会创建新的 [Linux 进程](https://developer.android.com/guide/components/fundamentals)以及执行线程。主线程的设计非常简单：它的唯一工作就是从线程安全工作队列获取工作块并执行，直到应用被终止。框架会从多个位置生成部分工作块。这些位置包括与生命周期信息、用户事件（例如输入）或来自其他应用和进程的事件相关的回调。此外，应用也可以不使用框架而自行对块进行明确排队。这个**主线程**也称为界面线程，负责屏幕上发生的一切活动。 如果主线程阻塞大约 5 秒，系统会显示[“应用无响应”](https://developer.android.com/training/articles/perf-anr)(ANR) 对话框，允许用户直接关闭应用。根据设计，[Android 视图对象不是线程安全的](https://www.youtube.com/watch?v=tBHPmQQNiS8&index=3&list=PLWz5rJ2EKKc9CBxr3BVjPTPoDPLdPIFCE)。无论是创建、使用还是销毁界面对象，应用都应在主线程上完成。在任何情况下，应用都只应在主线程上更新界面对象。这意味着您应制定允许多个线程将工作传回主线程的协商政策，让最顶层的 Activity 或 Fragment 负责更新实际界面对象。

**多线程的实现**：

1. **Handler+Thread**

    ```kotlin
        Thread(Runnable {
    
            val xxInfo = XX
    
            val mainHandler = Handler(Looper.getMainLooper())
            mainHandler.post {
    
                if (xxInfo.status == Status.SUCCESS) {
    
                    // do some thing
                }
            }
        }).start()
    ```

2. **Thread**

   ```java
   class MyThread extends Thread {
          @Override
       public void run(){
       ... // 定义的线程行为
       }
   }
   MyThread myThread = new MyThread("One");
   myThread.start();
   ```

3. **AsyncTask**

   ```java
   		new AsyncTask<Void, Void, Integer>() {
   			@Override
   			protected Integer doInBackground(Void... params) {
   				int ret = mCCREngine.init(PreviewActivity.this, appkey);
   				return ret;
   			}
   
   			@Override
   			protected void onPostExecute(Integer result) {
   				if (result != 0) {
   					/**
   					 * 101 包名错误, 授权APP_KEY与绑定的APP包名不匹配；
   					 * 102 appKey错误，传递的APP_KEY填写错误；
   					 * 103 超过时间限制，授权的APP_KEY超出使用时间限制；
   					 * 104 达到设备上限，授权的APP_KEY使用设备数量达到限制；
   					 * 201 签名错误，授权的APP_KEY与绑定的APP签名不匹配；
   					 * 202 其他错误，其他未知错误，比如初始化有问题；
   					 * 203 服务器错误，第一次联网验证时，因服务器问题，没有验证通过；
   					 * 204 网络错误，第一次联网验证时，没有网络连接，导致没有验证通过；
   					 * 205 包名/签名错误，授权的APP_KEY与绑定的APP包名和签名都不匹配；
   					 */
   					new AlertDialog.Builder(PreviewActivity.this)
   							.setMessage("Error " + result)
   							.setNegativeButton(android.R.string.ok, new DialogInterface.OnClickListener() {
   								@Override
   								public void onClick(DialogInterface dialog, int which) {
   									finish();
   								}
   							}).setCancelable(false).create().show();
   				}
   			}
   		}.execute();
   ```

   





###### 参考:

* [进程和线程概览](https://developer.android.com/guide/components/processes-and-threads) 
* [进程和线程的概念、区别及进程线程间通信](https://cloud.tencent.com/developer/article/1688297) 
* [线程和进程的区别是什么](https://www.zhihu.com/question/25532384) 
* [Android多线程详解](https://juejin.cn/post/6844903856388702216) 
