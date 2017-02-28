# 把自己写的library开源库提交到JitPack供他人使用

- 首先打开AndroidStudio —— New Project —— 一直next

此时项目中只有一个Module也就是app，而我们新建的library为另一个Module

- 新建Module —— Android library —— next —— 命名为library

![](http://i1.piimg.com/567571/93aa380fe1a6b972.png)

![](http://p1.bqimg.com/567571/6b9aea06f916cbbc.png)

--------

怎么知道Module是application还是普通的library呢？

我们只需要打开相应的build.gradle文件即可清楚区分出来

![](http://p1.bqimg.com/567571/ae6b66310db7878e.png)

到这里我们的library已经创建好了，然后我们在项目中关联上library，只需要我们在app build.gradle中的dependencies添加compile project(':library') [此处名称由自己的library决定]

![](http://p1.bpimg.com/567571/12588134ca7def1f.png)

到这里我们app已经在本地关联好了library库了，那么我们如何把自己的library库提交到jitpack供其他人使用呢

[1] [jitpack文档](https://jitpack.io/docs/ANDROID/)
里边有说明
1) In your root build.gradle://在项目的根build.gradle里边加上这句话

```java
buildscript {
  dependencies {
    classpath 'com.github.dcendents:android-maven-gradle-plugin:1.5' // Add this line
}
```
![](http://p1.bqimg.com/567571/6159546440d922a0.png)

2) In your library/build.gradle add:
```java
 apply plugin: 'com.github.dcendents.android-maven'  

 group='com.github.YourUsername'
 ```

 ![](http://p1.bqimg.com/567571/b05571d6fad370e8.png)


3) Create a GitHub release or add a git tag.


[2] 我们要先把整个工程上传到自己的github，此时项目是没有release版本的，我们要自己先new 一个release版本，里边命名都是v1.0，这样子好区分版本号，最后把项目的地址复制出来，只截取到项目名称即可，复制到https://jitpack.io/，出现get it的时候点击一下，这样子我们就已经成功的把自己github开源库托管到了jitpack上

![](http://p1.bpimg.com/567571/175ad0d0a2032c40.png)

![](http://i1.piimg.com/567571/c110a59fff443524.png)

![](http://i1.piimg.com/567571/d6efbc37a7787eb4.png)

![](http://p1.bqimg.com/567571/17519ec07802329b.png)

![](http://i1.piimg.com/567571/114a51b4c4135eea.png)

最后完成之后会在jitpack生成这样子的文件
![](http://i1.piimg.com/567571/919cba636fca3de7.png)

如果想使用该开源框架按要求向自己项目引入该代码即可
