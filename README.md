[TOC]

# 我的分享

# 我的关注

## [Gota](https://github.com/alhazmy13/Gota)

Android 6.0 动态权限适配。

### 安装

>Maven

```xml
<dependency>
<groupId>net.alhazmy13.Gota</groupId>
<artifactId>libary</artifactId>
<version>1.4.1</version>
</dependency>
```

>gradle

```
dependencies {
	compile 'net.alhazmy13.Gota:libary:1.4.1'
}
```

### 使用

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

## [OpenSSl](https://github.com/openssl/openssl)

是一个安全套接字层密码库，囊括主要的密码算法、常用的密钥和证书封装管理功能及SSL协议，并提供丰富的应用程序供测试或其它目的使用。

## [zxing](https://github.com/zxing/zxing)

条形码、二维码识别库

## [KotterKnife](https://github.com/JakeWharton/kotterknife)

ButterKnife 的kotlin版本。

## [ImmersionBar](https://github.com/gyf-dev/ImmersionBar)

安卓沉浸式任务栏的封装。

### 安装

>AndroidStudio

```
compile 'com.gyf.barlibrary:barlibrary:2.3.0'
```

>eclipse

[barlibrary-2.3.0.jar](https://github.com/gyf-dev/ImmersionBar/blob/master/jar/barlibrary-2.3.0.jar)

### 使用

基本用法

```java
ImmersionBar.with(this).init();
```

高级用法

```java
ImmersionBar.with(this)
             .transparentStatusBar()  //透明状态栏，不写默认透明色
             .transparentNavigationBar()  //透明导航栏，不写默认黑色(设置此方法，fullScreen()方法自动为true)
             .transparentBar()             //透明状态栏和导航栏，不写默认状态栏为透明色，导航栏为黑色（设置此方法，fullScreen()方法自动为true）
             .statusBarColor(R.color.colorPrimary)     //状态栏颜色，不写默认透明色
             .navigationBarColor(R.color.colorPrimary) //导航栏颜色，不写默认黑色
             .barColor(R.color.colorPrimary)  //同时自定义状态栏和导航栏颜色，不写默认状态栏为透明色，导航栏为黑色
             .statusBarAlpha(0.3f)  //状态栏透明度，不写默认0.0f
             .navigationBarAlpha(0.4f)  //导航栏透明度，不写默认0.0F
             .barAlpha(0.3f)  //状态栏和导航栏透明度，不写默认0.0f
             .statusBarDarkFont(true)   //状态栏字体是深色，不写默认为亮色
             .flymeOSStatusBarFontColor(R.color.btn3)  //修改flyme OS状态栏字体颜色
             .fullScreen(true)      //有导航栏的情况下，activity全屏显示，也就是activity最下面被导航栏覆盖，不写默认非全屏
             .hideBar(BarHide.FLAG_HIDE_BAR)  //隐藏状态栏或导航栏或两者，不写默认不隐藏
             .addViewSupportTransformColor(toolbar)  //设置支持view变色，可以添加多个view，不指定颜色，默认和状态栏同色，还有两个重载方法
             .titleBar(view)    //解决状态栏和布局重叠问题，任选其一
             .titleBarMarginTop(view)     //解决状态栏和布局重叠问题，任选其一
             .statusBarView(view)  //解决状态栏和布局重叠问题，任选其一
             .fitsSystemWindows(true)    //解决状态栏和布局重叠问题，任选其一，默认为false，当为true时一定要指定statusBarColor()，不然状态栏为透明色，还有一些重载方法
             .supportActionBar(true) //支持ActionBar使用
             .statusBarColorTransform(R.color.orange)  //状态栏变色后的颜色
             .navigationBarColorTransform(R.color.orange) //导航栏变色后的颜色
             .barColorTransform(R.color.orange)  //状态栏和导航栏变色后的颜色
             .removeSupportView(toolbar)  //移除指定view支持
             .removeSupportAllView() //移除全部view支持
             .navigationBarEnable(true)   //是否可以修改导航栏颜色，默认为true
             .navigationBarWithKitkatEnable(true)  //是否可以修改安卓4.4和emui3.1手机导航栏颜色，默认为true
             .fixMarginAtBottom(true)   //已过时，当xml里使用android:fitsSystemWindows="true"属性时,解决4.4和emui3.1手机底部有时会出现多余空白的问题，默认为false，非必须
             .addTag("tag")  //给以上设置的参数打标记
             .getTag("tag")  //根据tag获得沉浸式参数
             .reset()  //重置所以沉浸式参数
             .keyboardEnable(true)  //解决软键盘与底部输入框冲突问题，默认为false，还有一个重载方法，可以指定软键盘mode
             .keyboardMode(WindowManager.LayoutParams.SOFT_INPUT_ADJUST_RESIZE)  //单独指定软键盘模式
             .setOnKeyboardListener(new OnKeyboardListener() {    //软键盘监听回调
                   @Override
                   public void onKeyboardChange(boolean isPopup, int keyboardHeight) {
                       LogUtils.e(isPopup);  //isPopup为true，软键盘弹出，为false，软键盘关闭
                   }
              })
             .init();  //必须调用方可沉浸式
```

关闭销毁

- 在activity的onDestroy方法中执行

```java
ImmersionBar.with(this).destroy(); //必须调用该方法，防止内存泄漏
```

## [NFCCard](https://github.com/sinpolib/nfcard)

NFC读取卡片demo

## 安卓日志工具类

- [XLog](https://github.com/elvishew/xLog)

- [logger](https://github.com/orhanobut/logger)

-  [Klog](https://github.com/ZhaoKaiQiang/KLog)

## [GreenDAO](https://github.com/greenrobot/greenDAO)

GreenDAO 是轻量且快速的将对象关联到到SQLite数据库的Android平台的对象关系映射。

## [Realm-java](https://github.com/realm/realm-java)

Realm 是可以直接运行在手机、平板、穿戴设备上的手机数据库。

## APPDemo 类
 
### [Minimal-Todo](https://github.com/avjinder/Minimal-Todo)

迷你代办事项app。

### [MovieGuide](https://github.com/esoxjem/MovieGuide)

电影向导

### [superCleanMaster](https://github.com/joyoyao/superCleanMaster)

超级清理大师

- 基本功能

    - 内存加速
    - 缓存清理
    - 自启管理
    - 软件管理
    - 设备信息

- 截图

<img src="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/home.jpg" height="400px"/>

<img src="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/1.jpg" height="400px"/>










