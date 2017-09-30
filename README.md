[TOC]

# 我的分享

# 我的关注

## Android6.0 动态权限

### [Gota](https://github.com/alhazmy13/Gota)

#### 安装

Maven

```xml
<dependency>
<groupId>net.alhazmy13.Gota</groupId>
<artifactId>libary</artifactId>
<version>1.4.1</version>
</dependency>
```

gradle

```
dependencies {
	compile 'net.alhazmy13.Gota:libary:1.4.1'
}
```

#### 使用

添加好库之后，创建一个对象，传入权限数组，注册回调函数。

```java
new Gota.Builder(this)
                .withPermissions(Manifest.permission.CAMERA,Manifest.permission.ACCESS_FINE_LOCATION,Manifest.permission.CALL_PHONE)
                .requestId(1)
                .setListener(this)
                .check();
```

OnRequestPermissionsBack

```java
@Override
public void onRequestBack(int requestId, @NonNull GotaResponse gotaResponse) {
	if(gotaResponse.isGranted(Manifest.permission.CAMERA)) {
		 // Your Code
	}
}
```


