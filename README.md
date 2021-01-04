# MobPush-for-Android
# 快速集成MobPush Android

[MobPush for iOS快速集成文档点击此处查看](https://www.mob.com/wiki/detailed/?wiki=iOSfastjoijoij2222&id=136)

# 准备你的appkey

1、访问：[MobTech开发者后台](https://new.dashboard.mob.com/#/)

1.1、按照登录或完成注册

1.2、按照提示完成实名认证

2、基于你的实际情况，基于**已有应用**增加MobPush或**创建应用**

创建应用：点击“创建应用”按钮，并根据提示上传应用ICON，填写应用名称（**应用名称会作为厂商推送的默认名称，请认真填写**），并点击“确认”完成应用创建

在应用中增加MobPush：点击需要增加MobPush的应用底部的“+”按钮，并在界面中选择“MobPush”并点击“完成”
![开发者后台配置-MobPush](http://download.sdk.mob.com/2020/09/26/12/1601096284400204.40.jpg)

3、完成创建后，再次点击对应的应用，进入“**应用管理界面**”

4、在“**应用管理界面**”顶部，可以找到你的**appkey**和**appsecret**

![appkey-Push](http://download.sdk.mob.com/2020/09/26/12/160109631826913.49.png)

**请注意**：appkey和appsecret是你的应用使用MobTech开发者服务的唯一识别条件，请不要将appkey和appsecret提供给任何与你的应用开发无关的人员，以免出现非法调用事故


# 集成MobPush

1、打开你的应用开发项目根目录的build.gradle，在buildscrip–>dependencies 模块下面添加如下代码:

```java
buildscript {
    repositories {
		...
    }
    dependencies {
        ...
        // 集成MobPush
        classpath "com.mob.sdk:MobSDK:+"
    }
}
```

实际效果如下：
![share1](https://download.sdk.mob.com/2019/12/30/10/1577671445555/906_363_45.66.png)

2、在使用到MobPush的 module 下的 build.gradle 文件里面添加如下引用，并输入与你的应用对应的appkey和appsecret：

```java
// 调用MobTech SDK
apply plugin: 'com.mob.sdk'
MobSDK {
    appKey "你的appkey"
    appSecret "你的AppSecret"
    
    // 调用MobPush
	MobPush {}
}
```

实际效果如下：
![share2](https://download.sdk.mob.com/2019/12/30/10/1577671483785/935_537_60.95.png)

**如上已完成集成配置，可以进行后续的接口调用测试了，但如果需要终端用户接受隐私条款后才能发起网络访问，则需增加如下配置：**

```g
MobSDK {
    fp true //严格模式
}
```

如上，配置完之后，在终端用户接受隐私条款之前，MobSDK不会进行任何操作。请务必按照[Mob隐私协议接入指导](https://www.mob.com/wiki/detailed?wiki=MobYXXYMobpushAndroid&id=136)，回传终端用户隐私条款授权结果，以免影响后续服务。

# 后台包名修改

1.点击新增包名，填写你项目的包名，点击确定即可
![back1](http://download.sdk.mob.com/2020/11/17/11/160558461353124.06.png)
2.(非必须)设置默认包，默认包是在后台创建推送时多包名选择的默认选项，可设置其他包名或者多包名推送。
![back2](http://download.sdk.mob.com/2020/11/17/12/160558624529211.88.png)

# 发送推送

1、启动你刚才编译完成的应用，确保应用处于**前置状态**

2、进入[开发者后台](https://new.dashboard.mob.com/#/)，点击对应的应用，并进入MobPush-创建推送页
[![Bfnf0I.png](https://s1.ax1x.com/2020/11/06/Bfnf0I.png)](https://imgchr.com/i/Bfnf0I)

3、选择“Android”，并输入你要推送的内容（你可以在屏幕右侧看到实时预览）
[![BfnXBn.png](https://s1.ax1x.com/2020/11/06/BfnXBn.png)](https://imgchr.com/i/BfnXBn)

4、点击页面底部的“**立即发送**”，现在你应该可以在手机上收到一条推送消息了！

# 进阶开发传送门

## 隐私协议接入

> 根据工信部于2019年11月28日印发的《App违法违规收集使用个人信息行为认定方法》，使用MobTechSDK需要调用隐私条款，[相关内容请点击这里](http://www.mob.com/wiki/detailed?wiki=MobYXXYMobpushAndroid&id=136)

## 其他传送门

### 问题排查

> 没收到消息？[点击这里](http://mob.com)尝试排除问题

### 厂商渠道配置

> 需要配置厂商推送渠道？请参考[厂商集成](http://www.mob.com/wiki/detailed?wiki=other11&id=136)

### 回调配置

> 需要配置回调？请参考[回调配置](http://www.mob.com/wiki/detailed?wiki=Mobpushandroidnakdfaslapi111&id=136)


[1]: http://static.zybuluo.com/sd788034/7wpnc9bvj2cd43ik0x1q9z6v/%E5%BC%80%E5%8F%91%E8%80%85%E5%90%8E%E5%8F%B0%E9%85%8D%E7%BD%AE-MobPush.jpg
[2]: http://static.zybuluo.com/sd788034/gt3tewra56qetlww1bb7lovp/appkey-Push.png
[3]: http://static.zybuluo.com/sd788034/2p45zilqsm8gev9hdari22pe/MobPush-%E5%88%9B%E5%BB%BA%E6%8E%A8%E9%80%81.png
[4]: http://static.zybuluo.com/sd788034/3sip2jn5seba73ms083pcs6x/MobPush-%E5%88%9B%E5%BB%BA%E6%8E%A8%E9%80%81-%E8%BE%93%E5%85%A5%E6%96%87%E6%9C%AC.png

推送sdk