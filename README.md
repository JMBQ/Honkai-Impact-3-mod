# Honkai Impact 3 mod

针对 崩坏3rd 的悬浮菜单mod
<br>![image](https://github.com/JMBQ/image/blob/main/Honkai-Impact-3-mod/06.jpg)</br>
   
## 特点
1. 只适用于国外区服（sea, global, JP, KR, TW）, 国服玩家直接看最后
2. 动态抓取offset，故适用于当前及以后的任意游戏版本
3. 适配arm64-v8a、armeabi-v7a
4. 适用于安卓手机(推荐)、安卓模拟器
5. 没有广告
  
## 模拟器
* 在某些模拟器上会出现闪退，指向libhoudini.so，无法彻底修复
  * 夜神模拟器(nox7)，推荐度100%，完美运行
  * 雷电模拟器9，推荐度50%，概率抽风闪退
  * mumu，推荐度0%
  * 其它未测试
  
## 食用方法
  
* 看不懂的话，直接看video，内有PC+安卓视频教程

* 反编译游戏apk，生成对应文件夹
* 添加悬浮窗权限
```
<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW"/>
```
<br>![image](https://github.com/JMBQ/image/blob/main/Honkai-Impact-3-mod/01.png)</br>
* 添加悬浮窗服务	
```
<service android:name="com.android.support.Launcher" android:enabled="true" android:exported="false" android:stopWithTask="true"/>
```
<br>![image](https://github.com/JMBQ/image/blob/main/Honkai-Impact-3-mod/02.png)</br>
* 将com\android\support里的所有smali文件放入游戏文件夹中的android\support
<br>![image](https://github.com/JMBQ/image/blob/main/Honkai-Impact-3-mod/03.png)</br>
* 打开com\miHoYo\overridenativeactivity\OverrideNativeActivity.smali，找到onCreate方法，在方法开头插入
```
invoke-static {p0}, Lcom/android/support/Main;->Start(Landroid/content/Context;)V
```
<br>![image](https://github.com/JMBQ/image/blob/main/Honkai-Impact-3-mod/04.png)</br>
* 将libSaber、libArcher这2个文件放入游戏目录assets文件夹内
<br>![image](https://github.com/JMBQ/image/blob/main/Honkai-Impact-3-mod/05.png)</br>
* 编译游戏文件夹，生成直装包


## 注意事项
* 首次运行游戏，在正常情况下会跳至悬浮权限界面
* 刚打开游戏就闪退
  * 偶尔出现刚打开就闪退 属于正常现象
  * 连续多次出现刚打开就闪退 属于不正常现象，检查是否存在错误操作
* 游戏中途正常情况下不会闪退、卡住
* 如果出现游戏卡住，但悬浮菜单可以正常移动及操作，这种情况是触发了mod自身运行环境检测，mod主动击溃游戏进程

## 国服玩家注意
* 该mod不适合国服(有签名校验)
* 如果你手机已解锁，可以使用 [U.R.C](https://github.com/JMBQ/URC)，通杀所有服务器
* 提供官服6.4版本直装包，我先建个文件夹，出新版来拿。中路对决，把我的防守技术都塞进去，来人挑战下二改apk？
