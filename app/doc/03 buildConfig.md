
#### buildConfig 中的配置

> 根据config 中配置进行 属性的配置

#### 方案一: 通过 gradle 进行配置
```

buildTypes {
    debug {
        buildConfigField "String", "CustomValue",'"buildType"'
        buildConfigField "boolean","LOG_DEBUG","true"
    }
    release {
        buildConfigField "String", "CustomValue",'"releaseType"'
        buildConfigField "boolean","LOG_DEBUG","false"
    }
}

通过 buildConfig 来获取参数

public final class BuildConfig {
public static final boolean DEBUG = false;
  public static final String APPLICATION_ID = "com.xxx.xxxx";
  public static final String BUILD_TYPE = "release";
  public static final String FLAVOR = "";
  public static final int VERSION_CODE = 1002;
  public static final String VERSION_NAME = "1002";
  // Fields from build type: release
  public static final String CustomValue = "releaseType";
}



```


#### 方案二 : 通过 metadata 进行配置

```

xml 中的配置

<meta-data
    android:name="Logs.enable"
    android:value="${LogEnable}"
 />

gradle 中的配置

buildTypes {
    debug {
manifestPlaceholders = [LogEnable : true]
    }
    release {
manifestPlaceholders = [LogEnable : false]
    }
}


// 在工程中 获取参数

ApplicationInfo appInfo = null;
try {
   appInfo = this.getPackageManager()
                  .getApplicationInfo(getPackageName(),
                          PackageManager.GET_META_DATA);
   boolean enable=appInfo.metaData.getBoolean("Logs.enable");
   Log.d("MyApplication","Logs.enable = "+enable);
} catch (PackageManager.NameNotFoundException e) {
   e.printStackTrace();
}


```
