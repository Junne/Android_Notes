### Android NetWork



##### [Retrofit](https://square.github.io/retrofit/) 的使用:

* 选择获取天气的api来测试 [最好的免费天气API接口对比评测](https://segmentfault.com/a/1190000041210520) 

* 高德地图的天气服务: 1.[高德天气查询](https://lbs.amap.com/api/webservice/guide/api/weatherinfo/) 2.[城市编码查询](https://lbs.amap.com/api/webservice/download) 

  ```
  https://restapi.amap.com/v3/weather/weatherInfo?key=4017b7f4d06c1c631d5baad7172d8468&extensions=all&city=410300
  ```

* [Android项目java与kotlin混编](https://blog.csdn.net/Cyanogen_dom/article/details/107876869) 

* [启动项目报错:java.lang.NoSuchMethodError: No static method metafactory](https://github.com/likaiyuan559/TouchEffects/issues/12) 

* Retofit要求java8+和android 21+的支持，所以需要在模块的build.gradle文件的 android{ } 配置如下:

  ```kotlin
  android{
  		...
      	compileOptions {
          sourceCompatibility JavaVersion.VERSION_1_8
          targetCompatibility JavaVersion.VERSION_1_8
      }
  
         kotlinOptions{
          jvmTarget="1.8"
      }    
  }
  ```

* 创建请求:

  * 请求头参数:

    ```kotlin
    public interface AmapWeatherService {
    
        @GET("v3/weather/weatherInfo")
        Call<AmapWeatherBean> getAmapWeather(
                @Query("key") String key,
                @Query("city") String city,
                @Query("extensions") String extensions
                );
    
    }
    ```

  * 完整的请求:

    ```kotlin
            val retrofit: Retrofit = Retrofit.Builder()
                .baseUrl("https://restapi.amap.com/")
                .addConverterFactory(GsonConverterFactory.create())
                .build()
    				// AmapWeatherBead为解析的Java Bean
            val request = retrofit.create(AmapWeatherService::class.java)
            request.getAmapWeather("4017b7f4d06c1c631d5baad7172d8468", "410300","all").
                enqueue(object :Callback<AmapWeatherBean> {
                    override fun onFailure(call: Call<AmapWeatherBean>, t: Throwable) {
    
                        Log.d("Failure=", t.toString())
                    }
    
                    override fun onResponse(
                        call: Call<AmapWeatherBean>,
                        response: Response<AmapWeatherBean>
                    ) {
                        if (response.isSuccessful) {
                            Log.d("Result=", response.toString())
                        }
                    }
                })
    ```

    

##### 创建Java对象

* 使用[RoboPOJOGenerator](https://plugins.jetbrains.com/plugin/8634-robopojogenerator) 来生成Java对象



###### 参考:

* [Retrofit2.0使用教程](https://juejin.cn/post/6844903751438827527) 
* [Retrofit使用说明书](https://juejin.cn/post/6844904190314037262) 
* [Retrofit2详解与使用](https://blog.csdn.net/m0_37796683/article/details/90702095) 
* [优雅的封装网络请求,协程+Retrofit](https://juejin.cn/post/6959115482511343647) 
* [ReJava+Retrofit完成网络请求](https://segmentfault.com/a/1190000018253015) 
* [Kotlin+Retrofit+RxKotlin+MVP](https://juejin.cn/post/6844903542151446542) 











-----



##### 参考:

* [那些年我用过的Android网络请求库](https://blog.51cto.com/u_15060510/2641038) 
