# coolweather

app:build.gradle
```
//noinspection GradleCompatible
implementation 'com.android.support:appcompat-v7:26.1.0.'
implementation 'com.android.support.constraint:constraint-layout:1.0.2'
implementation 'com.squareup.okhttp3:okhttp:3.4.1'
implementation 'com.google.code.gson:gson:2.7'
implementation 'com.github.bumptech.glide:glide:3.7.0'
```
***
gradle-wrapper.properties
``` 
distributionUrl=https\://services.gradle.org/distributions/gradle-7.3.3-all.zip
```
***
必应每日一图

http://api.muvip.cn/api/bing

http://guolin.tech/api/bing_pic

https://blog.csdn.net/chenxihanhui/article/details/113115019
***
# ERROR
报错：
A failure occurred while executing com.android.build.gradle.internal.tasks.CheckAarMetadataWorkAction

解决方法：

gradle.properties文件中添加
```
android.enableJetifier=true
```
***
报错：
style attribute 'android:attr/dialogCornerRadius' not found.

解决方法：
File --> Project Structure --> Modules --> Properties --> Compile Sdk version

或者修改 app --> build.gradle
```
compileSdk 29
buildToolsVersion '28.0.3'
```

CSDN解决方法:
https://blog.csdn.net/weixin_43465451/article/details/83185112
***
报错：
Attempt to invoke interface method 'java.util.Iterator java.util.List.iterator()' on a null object reference

原因：遍历的是空
***
报错：
GoldfishAddressSpaceHostMemoryAllocator: ioctl_ping failed for device_type=5, ret=-1

原因：传入的图片有问题
```
Glide.with(WeatherActivity.this).load(bingPic).into(bingPicImg);
Glide.with(上下文).load(api地址).into(需要传入的View);
```
***
报错：
android.support.v4.widget.SwipeRefreshLayout

https://blog.csdn.net/weixin_43873198/article/details/108895904
***

```xml
<fragment android:id="@+id/choose_area_fragment"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:name="com.example.coolweather.ChooseAreaFragment"
    android:layout_gravity="end" />
```
右边：
android:layout_gravity="end"
左边：
android:layout_gravity="start"

android:gravity：是对view控件本身来说的，是用来设置view本身的内容应该显示在view的什么位置，默认值是左侧。也可以用来设置布局中的控件位置

android:layout_gravity：是相对于包含改元素的父元素来说的，设置该元素在父元素的什么位置；


读取数据
```
SharedPreferences prefs = PreferenceManager.getDefaultSharedPreferences(this);
String weatherString = prefs.getString("weather", null);
```
https://blog.csdn.net/ZHXLXH/article/details/87940293

# PROBLEM
问题1：Glide加载相同URL时由于缓存无法更新图片

解决方法：
``` 
Glide.with(WeatherActivity.this)
    .load("http://api.muvip.cn/api/bing")
    .skipMemoryCache(true)//不使用内存缓存
    .diskCacheStrategy(DiskCacheStrategy.NONE) // 不使用磁盘缓存
    .into(bingPicImg);
```
https://blog.csdn.net/zhifanxu/article/details/78981459


# 笔记
``` 
response = [{"id":1,"name":"北京"},{"id":2,"name":"上海"}]
```
[]表示数组，使用JSONArray解析

JSONArray allCounties = new JSONArray(response);

{}表示元素，使用JSONObject解析

JSONObject countyObject = allCounties.getJSONObject(i);

getJSONObject(i)表示第i个元素，遍历获取所有省份

获取键值对：
provinceObject.getString("name")
provinceObject.getInt("id")

***

复习6.3SharedPreferences储存


https://blog.csdn.net/weixin_42292229/article/details/90737346

