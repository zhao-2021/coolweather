# coolweather

app:build.gradle
```
testImplementation 'junit:junit:4.13.2'
implementation 'com.android.support:appcompat-v7:26.+'
implementation 'org.litepal.android:core:3.0.0'
implementation 'com.squareup.okhttp3:okhttp:3.10.0'
implementation 'com.google.code.gson:gson:2.8.6'
implementation 'com.github.bumptech.glide:glide:3.7.0'
```

gradle-wrapper.properties
``` 
distributionUrl=https\://services.gradle.org/distributions/gradle-3.3-bin.zip
```

报错：
A failure occurred while executing com.android.build.gradle.internal.tasks.CheckAarMetadataWorkAction
解决方法：
gradle.properties文件中添加
android.enableJetifier=true

报错：
style attribute 'android:attr/dialogCornerRadius' not found.
解决方法：
File --> Project Structure --> Modules --> Properties --> Compile Sdk version
或者修改 app --> build.gradle
compileSdk 29
buildToolsVersion '28.0.3'
CSDN解决方法
https://blog.csdn.net/weixin_43465451/article/details/83185112

报错：
Attempt to invoke interface method 'java.util.Iterator java.util.List.iterator()' on a null object reference
原因是遍历的是空