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

## [butterknife](https://github.com/JakeWharton/butterknife)

使用

```java
class ExampleActivity extends Activity {
  @BindView(R.id.user) EditText username;
  @BindView(R.id.pass) EditText password;

  @BindString(R.string.login_error) String loginErrorMessage;

  @OnClick(R.id.submit) void submit() {
    // TODO call server...
  }

  @Override public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.simple_activity);
    ButterKnife.bind(this);
    // TODO Use fields...
  }
}
```

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

## Demo类
 
### [Minimal-Todo](https://github.com/avjinder/Minimal-Todo)

迷你代办事项app。

- 截图

<p><a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/main_empty_light.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/main_empty_light.png" height="400px" style="max-width:100%;"></a> <a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/main_empty_dark.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/main_empty_dark.png" height="400px" style="max-width:100%;"></a>
<a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/main_full_light.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/main_full_light.png" height="400px" style="max-width:100%;"></a><a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/main_full_dark.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/main_full_dark.png" height="400px" style="max-width:100%;"></a>
<a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/add_todo_light.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/add_todo_light.png" height="400px" style="max-width:100%;"></a>
<a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/add_todo_dark.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/add_todo_dark.png" height="400px" style="max-width:100%;"></a>
<a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/screenshot_reminder_date.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/screenshot_reminder_date.png" height="400px" style="max-width:100%;"></a>
<a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/screenshot_reminder_time.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/screenshot_reminder_time.png" height="400px" style="max-width:100%;"></a>
<a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/todo_date_dark.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/todo_date_dark.png" height="400px" style="max-width:100%;"></a>
<a href="https://github.com/avjinder/Minimal-Todo/blob/master/screenshots/todo_time_dark.png" target="_blank"><img src="https://github.com/avjinder/Minimal-Todo/raw/master/screenshots/todo_time_dark.png" height="400px" style="max-width:100%;"></a>
<a href="https://github.com/avjinder/Toodle/blob/master/screenshots/screenshot_notification.png" target="_blank"><img src="https://github.com/avjinder/Toodle/raw/master/screenshots/screenshot_notification.png" height="400px" style="max-width:100%;"></a>
<a href="https://github.com/avjinder/Toodle/blob/master/screenshots/screenshot_todo_snooze.png" target="_blank"><img src="https://github.com/avjinder/Toodle/raw/master/screenshots/screenshot_todo_snooze.png" height="400px" style="max-width:100%;"></a></p>

### [MovieGuide](https://github.com/esoxjem/MovieGuide)

电影向导

- 截图

<p><a href="https://camo.githubusercontent.com/d43f985014a6ef8e7a8054cde976fce0977fbcac/687474703a2f2f692e696d6775722e636f6d2f373250797058436d2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/d43f985014a6ef8e7a8054cde976fce0977fbcac/687474703a2f2f692e696d6775722e636f6d2f373250797058436d2e706e67" alt="Screenshot" data-canonical-src="http://i.imgur.com/72PypXCm.png" style="max-width:100%;"></a>
<a href="https://camo.githubusercontent.com/ad120628f367abe35dabce72336120dc773b62b0/687474703a2f2f696d6775722e636f6d2f493936456b61366d2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/ad120628f367abe35dabce72336120dc773b62b0/687474703a2f2f696d6775722e636f6d2f493936456b61366d2e706e67" alt="screenshot2" data-canonical-src="http://imgur.com/I96Eka6m.png" style="max-width:100%;"></a>
<a href="https://camo.githubusercontent.com/bf81b95d4407b83bdf581b180e1b8ae298d0a1ce/687474703a2f2f696d6775722e636f6d2f3471485a63656a6d2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/bf81b95d4407b83bdf581b180e1b8ae298d0a1ce/687474703a2f2f696d6775722e636f6d2f3471485a63656a6d2e706e67" alt="screenshot3" data-canonical-src="http://imgur.com/4qHZcejm.png" style="max-width:100%;"></a>
<a href="https://camo.githubusercontent.com/8d532a414447cb9dee0769fccc48efaf3eda99ac/687474703a2f2f696d6775722e636f6d2f6d374a38487a556d2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/8d532a414447cb9dee0769fccc48efaf3eda99ac/687474703a2f2f696d6775722e636f6d2f6d374a38487a556d2e706e67" alt="screenshot4" data-canonical-src="http://imgur.com/m7J8HzUm.png" style="max-width:100%;"></a>
<a href="https://camo.githubusercontent.com/04d8e35076dbe346bc91296775a380e0b5bb743d/687474703a2f2f696d6775722e636f6d2f5077746a5a484b6d2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/04d8e35076dbe346bc91296775a380e0b5bb743d/687474703a2f2f696d6775722e636f6d2f5077746a5a484b6d2e706e67" alt="screenshot5" data-canonical-src="http://imgur.com/PwtjZHKm.png" style="max-width:100%;"></a>
<a href="https://camo.githubusercontent.com/b5317c9487bd3baac104c1ede870948e28fcf2e3/687474703a2f2f696d6775722e636f6d2f6b4e486a4358536d2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/b5317c9487bd3baac104c1ede870948e28fcf2e3/687474703a2f2f696d6775722e636f6d2f6b4e486a4358536d2e706e67" alt="screenshot6" data-canonical-src="http://imgur.com/kNHjCXSm.png" style="max-width:100%;"></a></p>

[Kotlin版本传送门](https://github.com/esoxjem/MovieGuide-Kotlin)

### [superCleanMaster](https://github.com/joyoyao/superCleanMaster)

超级清理大师

- 基本功能

    - 内存加速
    - 缓存清理
    - 自启管理
    - 软件管理
    - 设备信息

- 截图

<p><a href="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/home.jpg" target="_blank">
    <img src="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/home.jpg" height="400px" style="max-width:100%;">
</a>

<a href="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/1.jpg" target="_blank"><img src="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/1.jpg" height="400px" style="max-width:100%;"></a>

<a href="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/2.jpg" target="_blank"><img src="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/2.jpg" height="400px" style="max-width:100%;"></a>

<a href="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/3.jpg" target="_blank"><img src="https://github.com/joyoyao/superCleanMaster/blob/master/screenshot/3.jpg" height="400px" style="max-width:100%;"></a></p>


### [photo-affix](https://github.com/afollestad/photo-affix)

- 截图

<p><a href="https://raw.githubusercontent.com/afollestad/photo-affix/master/art/pashowcase1.png" target="_blank"><img src="https://raw.githubusercontent.com/afollestad/photo-affix/master/art/pashowcase1.png" alt="Showcase" style="max-width:100%;"></a></p>

### [Travel-Mate](https://github.com/Swati4star/Travel-Mate)

旅游助手

- 截图

<p><a href="https://github.com/Swati4star/Travel-Mate/blob/master/screenshots/all_cities.png" target="_blank"><img src="https://github.com/Swati4star/Travel-Mate/raw/master/screenshots/all_cities.png" width="200px" style="max-width:100%;"></a> <a href="https://github.com/Swati4star/Travel-Mate/blob/master/screenshots/one_city.png" target="_blank"><img src="https://github.com/Swati4star/Travel-Mate/raw/master/screenshots/one_city.png" width="200px" style="max-width:100%;"></a> <a href="https://github.com/Swati4star/Travel-Mate/blob/master/screenshots/fact.png" target="_blank"><img src="https://github.com/Swati4star/Travel-Mate/raw/master/screenshots/fact.png" width="200px" style="max-width:100%;"></a></p>
<p><a href="https://github.com/Swati4star/Travel-Mate/blob/master/screenshots/city_here.png" target="_blank"><img src="https://github.com/Swati4star/Travel-Mate/raw/master/screenshots/city_here.png" width="200px" style="max-width:100%;"></a> <a href="https://github.com/Swati4star/Travel-Mate/blob/master/screenshots/trend.png" target="_blank"><img src="https://github.com/Swati4star/Travel-Mate/raw/master/screenshots/trend.png" width="200px" style="max-width:100%;"></a></p>


### [Turbo Editor](https://github.com/vmihalachi/turbo-editor)

简单、强大、开源的文本编辑器。

### [KISS](https://github.com/Neamar/KISS)

快速搜索联系人、应用的程序。

- 截图

<table>
<thead>
<tr>
<th align="center"><a href="https://camo.githubusercontent.com/be01974f69d6b2b13a65f7e07d46270b3a3e0067/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f31422d566339547168366266474356794b586b59535a79637759395a3467364e785833554c414b644350676939706d47486f7949656c43346e735662514b3864356c3069" target="_blank"><img src="https://camo.githubusercontent.com/be01974f69d6b2b13a65f7e07d46270b3a3e0067/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f31422d566339547168366266474356794b586b59535a79637759395a3467364e785833554c414b644350676939706d47486f7949656c43346e735662514b3864356c3069" alt="Preview" data-canonical-src="https://lh3.googleusercontent.com/1B-Vc9Tqh6bfGCVyKXkYSZycwY9Z4g6NxX3ULAKdCPgi9pmGHoyIelC4nsVbQK8d5l0i" style="max-width:100%;"></a></th>
<th align="center"><a href="https://camo.githubusercontent.com/e351a79862b46b4a0dc204c374c1a11ae18cabb1/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f41446c686775364a42564f4a526e5f58532d4262466277364874476f7056414270425364424d66414e5870477069634659336a78564c637542686e4a39516b5373685470" target="_blank"><img src="https://camo.githubusercontent.com/e351a79862b46b4a0dc204c374c1a11ae18cabb1/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f41446c686775364a42564f4a526e5f58532d4262466277364874476f7056414270425364424d66414e5870477069634659336a78564c637542686e4a39516b5373685470" alt="Preview" data-canonical-src="https://lh3.googleusercontent.com/ADlhgu6JBVOJRn_XS-BbFbw6HtGopVABpBSdBMfANXpGpicFY3jxVLcuBhnJ9QkSshTp" style="max-width:100%;"></a></th>
<th align="center"><a href="https://camo.githubusercontent.com/5bc5b8ba7005da0852eecb332174fd73b4fcc3ac/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f31374a545a4b693077683852654e544d6d68457a6f523149755f6d69724b3836375f483247624d7744684666385177707168787a636370424c41466f354462466467" target="_blank"><img src="https://camo.githubusercontent.com/5bc5b8ba7005da0852eecb332174fd73b4fcc3ac/68747470733a2f2f6c68332e676f6f676c6575736572636f6e74656e742e636f6d2f31374a545a4b693077683852654e544d6d68457a6f523149755f6d69724b3836375f483247624d7744684666385177707168787a636370424c41466f354462466467" alt="Preview" data-canonical-src="https://lh3.googleusercontent.com/17JTZKi0wh8ReNTMmhEzoR1Iu_mirK867_H2GbMwDhFf8QwpqhxzccpBLAFo5DbFdg" style="max-width:100%;"></a></th>
</tr>
</thead>
<tbody>
<tr>
<td align="center">Recently used first</td>
<td align="center">Search apps, contacts...</td>
<td align="center">Even in settings!</td>
</tr></tbody></table>

### [InstaMaterial](https://github.com/frogermcs/InstaMaterial)

### [LeafPic](https://github.com/HoraApps/LeafPic)

- 截图

<div>
<a href="https://github.com/HoraApps/LeafPic/blob/dev/screenshots/1.png" target="_blank"><img src="https://github.com/HoraApps/LeafPic/raw/dev/screenshots/1.png" width="19%" style="max-width:100%;"></a>
<a href="https://github.com/HoraApps/LeafPic/blob/dev/screenshots/2.png" target="_blank"><img src="https://github.com/HoraApps/LeafPic/raw/dev/screenshots/2.png" width="19%" style="max-width:100%;"></a>
<a href="https://github.com/HoraApps/LeafPic/blob/dev/screenshots/3.png" target="_blank"><img src="https://github.com/HoraApps/LeafPic/raw/dev/screenshots/3.png" width="19%" style="max-width:100%;"></a>
<a href="https://github.com/HoraApps/LeafPic/blob/dev/screenshots/4.png" target="_blank"><img src="https://github.com/HoraApps/LeafPic/raw/dev/screenshots/4.png" width="19%" style="max-width:100%;"></a>
<a href="https://github.com/HoraApps/LeafPic/blob/dev/screenshots/5.png" target="_blank"><img src="https://github.com/HoraApps/LeafPic/raw/dev/screenshots/5.png" width="19%" style="max-width:100%;"></a>
</div>

### [Omni-Notes](https://github.com/federicoiosue/Omni-Notes)

- 截图

<p><a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/02.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/02.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/03.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/03.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/04.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/04.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/05.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/05.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/06.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/06.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/07.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/07.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/08.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/08.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/09.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/09.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/10.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/10.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/11.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/11.png" alt="" style="max-width:100%;"></a>
<a href="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/12.png" target="_blank"><img src="https://raw.githubusercontent.com/federicoiosue/Omni-Notes/develop/etc/play_store_pics/12.png" alt="" style="max-width:100%;"></a></p>


### [MLManager](https://github.com/javiersantos/MLManager)

### [Simple-Calendar](https://github.com/SimpleMobileTools/Simple-Calendar)

简单日历应用

- 截图

<p><a href="https://github.com/SimpleMobileTools/Simple-Calendar/blob/master/screenshots/app_2.png" target="_blank"><img alt="App image" src="https://github.com/SimpleMobileTools/Simple-Calendar/raw/master/screenshots/app_2.png" width="250" style="max-width:100%;"></a></p>
<p><a href="https://github.com/SimpleMobileTools/Simple-Calendar/blob/master/screenshots/app_4.png" target="_blank"><img alt="App image" src="https://github.com/SimpleMobileTools/Simple-Calendar/raw/master/screenshots/app_4.png" width="250" style="max-width:100%;"></a></p>
<p><a href="https://github.com/SimpleMobileTools/Simple-Calendar/blob/master/screenshots/app.png" target="_blank"><img alt="App image" src="https://github.com/SimpleMobileTools/Simple-Calendar/raw/master/screenshots/app.png" width="250" style="max-width:100%;"></a></p>

### [SoundRecorder](https://github.com/dkim0419/SoundRecorder)

录音应用

- 截图

<p><a href="https://camo.githubusercontent.com/0ac8e9f2ca2ce2ee4d3b151d74f9167820529505/687474703a2f2f692e696d6775722e636f6d2f345735666a30496c2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/0ac8e9f2ca2ce2ee4d3b151d74f9167820529505/687474703a2f2f692e696d6775722e636f6d2f345735666a30496c2e706e67" alt="alt tag" data-canonical-src="http://i.imgur.com/4W5fj0Il.png" style="max-width:100%;"></a> <a href="https://camo.githubusercontent.com/4016cf2d75e835d50621bb15ce6c9d06e653fc5b/687474703a2f2f692e696d6775722e636f6d2f3767676346517a6c2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/4016cf2d75e835d50621bb15ce6c9d06e653fc5b/687474703a2f2f692e696d6775722e636f6d2f3767676346517a6c2e706e67" alt="alt tag" data-canonical-src="http://i.imgur.com/7ggcFQzl.png" style="max-width:100%;"></a> <a href="https://camo.githubusercontent.com/a8cc19c9ce5681d43ca62881d39a61a5111ec633/687474703a2f2f692e696d6775722e636f6d2f527144385333496c2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/a8cc19c9ce5681d43ca62881d39a61a5111ec633/687474703a2f2f692e696d6775722e636f6d2f527144385333496c2e706e67" alt="alt tag" data-canonical-src="http://i.imgur.com/RqD8S3Il.png" style="max-width:100%;"></a> <a href="https://camo.githubusercontent.com/f80c6c88e16a1f42494b04a6c610a4d3b1122041/687474703a2f2f692e696d6775722e636f6d2f483653634f32316c2e706e67" target="_blank"><img src="https://camo.githubusercontent.com/f80c6c88e16a1f42494b04a6c610a4d3b1122041/687474703a2f2f692e696d6775722e636f6d2f483653634f32316c2e706e67" alt="alt tag" data-canonical-src="http://i.imgur.com/H6ScO21l.png" style="max-width:100%;"></a></p>

### [Timber](https://github.com/naman14/Timber)

音乐播放器

- 截图

<p><a href="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen2.png" target="_blank"><img src="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen2.png" width="360" height="640" style="max-width:100%;"></a></p>
<p><a href="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen3.png" target="_blank"><img src="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen3.png" width="360" height="640" style="max-width:100%;"></a></p>
<p><a href="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen7.png" target="_blank"><img src="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen7.png" width="360" height="640" style="max-width:100%;"></a></p>
<p><a href="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen1.png" target="_blank"><img src="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen1.png" width="360" height="640" style="max-width:100%;"></a></p>
<p><a href="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen5.png" target="_blank"><img src="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen5.png" width="360" height="640" style="max-width:100%;"></a></p>
<p><a href="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen4.png" target="_blank"><img src="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen4.png" width="360" height="640" style="max-width:100%;"></a></p>
<p><a href="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen6.png" target="_blank"><img src="https://raw.githubusercontent.com/naman14/Timber/master/graphics/screen6.png" width="360" height="640" style="max-width:100%;"></a></p>

### [CoCoin](https://github.com/Nightonke/CoCoin)

多视图记账APP

### [Clip-Stack](https://github.com/heruoxin/Clip-Stack)

剪纸堆

一个超轻量级剪贴板历史记录管理软件。

- 无限保存剪贴板历史

>剪纸堆会自动保留您复制过的每一段文字。就算重启后也会自动恢复。

- 易于管理

>无论添加、搜索、编辑还是全部清空，都非常容易。而轻轻滑动即可逐条删除。

- 有用的扩展通知

>当你可能要输入文字的时候，你最近的6条剪贴板记录会悄悄出现在通知栏上。你能在其中自由切换和粘贴。当不需要时，轻滑即可消去。

- 自由分享

>每一条剪贴板记录都能分享给其他的程序，诸如 Twitter、Gmail、 Evernote、微信、QQ……

- Material Design

>不仅图标和颜色，剪纸堆的每一个细节都遵循 Material design 设计标准。尽我可能的利用了 Android 🍭Lollipop 的新特性。

- 自动清理

>当手机持续出于充电状态几分钟后，剪纸堆会悄悄自动清理自己的缓存数据，和内存占用，——这全归功于 Android 🍭Lollipop 的全新定时任务 API

### [AnotherMonitor](https://github.com/AntonioRedondo/AnotherMonitor)

安卓程序监听器

- 截图

<p>
<a href="https://camo.githubusercontent.com/e8a643e7373bfa716cc54ac949a12c6c760639c9/68747470733a2f2f6c68342e67677068742e636f6d2f6766774d683449683056443041617849385f656831316d364352755f7a5357362d5536463235416a43646c556a436b6c69574842674a4d684462336550646c5f454d6f54" target="_blank"><img src="https://camo.githubusercontent.com/e8a643e7373bfa716cc54ac949a12c6c760639c9/68747470733a2f2f6c68342e67677068742e636f6d2f6766774d683449683056443041617849385f656831316d364352755f7a5357362d5536463235416a43646c556a436b6c69574842674a4d684462336550646c5f454d6f54" width="180px" data-canonical-src="https://lh4.ggpht.com/gfwMh4Ih0VD0AaxI8_eh11m6CRu_zSW6-U6F25AjCdlUjCkliWHBgJMhDb3ePdl_EMoT" style="max-width:100%;"></a>
<a href="https://camo.githubusercontent.com/76347b5b00f31b60245a2af6dc5df31df683faa9/68747470733a2f2f6c68342e67677068742e636f6d2f667567545446396937366e73666e705766763334786531587a3575346444574f716254596b426150727a7564347a507559495a7451516845794837705839504f6a5955" target="_blank"><img src="https://camo.githubusercontent.com/76347b5b00f31b60245a2af6dc5df31df683faa9/68747470733a2f2f6c68342e67677068742e636f6d2f667567545446396937366e73666e705766763334786531587a3575346444574f716254596b426150727a7564347a507559495a7451516845794837705839504f6a5955" width="180px" data-canonical-src="https://lh4.ggpht.com/fugTTF9i76nsfnpWfv34xe1Xz5u4dDWOqbTYkBaPrzud4zPuYIZtQQhEyH7pX9POjYU" style="max-width:100%;"></a>
<a href="https://camo.githubusercontent.com/8f434cd361424c0a77b73f23dadcb56b70ade8af/68747470733a2f2f6c68352e67677068742e636f6d2f3936426d6b6c62424f454f674c356d6d585a516b6f667773774c47457a59345a66364569727446326e4f4267665f63546f38365278757a43496e7637657449664e67544f" target="_blank"><img src="https://camo.githubusercontent.com/8f434cd361424c0a77b73f23dadcb56b70ade8af/68747470733a2f2f6c68352e67677068742e636f6d2f3936426d6b6c62424f454f674c356d6d585a516b6f667773774c47457a59345a66364569727446326e4f4267665f63546f38365278757a43496e7637657449664e67544f" width="180px" data-canonical-src="https://lh5.ggpht.com/96BmklbBOEOgL5mmXZQkofwswLGEzY4Zf6EirtF2nOBgf_cTo86RxuzCInv7etIfNgTO" style="max-width:100%;"></a></p>

### [AnExplorer](https://github.com/1hakr/AnExplorer)

文件浏览器

### [Android-PickerView](https://github.com/Bigkoo/Android-PickerView)

安卓选择器

这是一款仿iOS的PickerView控件，有时间选择和选项选择，并支持一二三级联动，支持自定义样式，3.x新版本的详细特性如下：

- 有时间和选项这两种选择器
- 选项选择器支持三级联动
- 时间选择器支持起始和终止日期设定
- 支持“年，月，日，时，分，秒”，“省，市，区”等选项的单位（label）显示、隐藏和自定义。
- 支持自定义文字、颜色、文字大小等属性
- 支持背景颜色更换，有夜间模式需求的问题可以解决了
- Item的文字长度过长时，文字会自适应缩放到Item的长度，避免显示不完全的问题
- TimePickerView 时间选择器，支持年月日时分，年月日，年月，时分等格式
- OptionsPickerView 选项选择器，支持一，二，三级选项选择，并且可以设置是否联动

### [lottie-android](https://github.com/airbnb/lottie-android)

- 截图

<p><a href="https://github.com/airbnb/lottie-android/blob/master/gifs/Example1.gif" target="_blank"><img src="https://github.com/airbnb/lottie-android/raw/master/gifs/Example1.gif" alt="Example1" style="max-width:100%;"></a></p>
<p><a href="https://github.com/airbnb/lottie-android/blob/master/gifs/Example2.gif" target="_blank"><img src="https://github.com/airbnb/lottie-android/raw/master/gifs/Example2.gif" alt="Example2" style="max-width:100%;"></a></p>
<p><a href="https://github.com/airbnb/lottie-android/blob/master/gifs/Example3.gif" target="_blank"><img src="https://github.com/airbnb/lottie-android/raw/master/gifs/Example3.gif" alt="Example3" style="max-width:100%;"></a></p>
<p><a href="https://github.com/airbnb/lottie-android/blob/master/gifs/Community%202_3.gif" target="_blank"><img src="https://github.com/airbnb/lottie-android/raw/master/gifs/Community%202_3.gif" alt="Community" style="max-width:100%;"></a></p>
<p><a href="https://github.com/airbnb/lottie-android/blob/master/gifs/Example4.gif" target="_blank"><img src="https://github.com/airbnb/lottie-android/raw/master/gifs/Example4.gif" alt="Example4" style="max-width:100%;"></a></p>

### [AmazeFileManager](https://github.com/TeamAmaze/AmazeFileManager)

文件管理器

## 图表库

- [XCL-Charts](https://github.com/xcltapestry/XCL-Charts)
- [MPAndroidChart](https://github.com/PhilJay/MPAndroidChart)



## [HorizontalPageGridView](https://github.com/ledlau/HorizontalPageGridView)

水平GridView组件


## [ZBar](https://github.com/ZBar/ZBar)

ZBar 二维码

## 图片加载

- [Android-Universal-Image-Loade](https://github.com/nostra13/Android-Universal-Image-Loader)
- [picasso](https://github.com/square/picasso)
- [glide](https://github.com/bumptech/glide)

## [EventBus](https://github.com/greenrobot/EventBus)




