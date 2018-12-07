代码中需要用的高德SDK需要自行下载

### 介绍

组件化的前提是要有基础组件、功能组件、业务组件这三大块。其中基础组件和功能组件都可以做成SDK，可以供其他APP选择性的调用。

![](https://upload-images.jianshu.io/upload_images/301129-e03e5679ab6446ce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

比如把地图组件单独封装成一个SDK，需要使用地图就加载这个SDK，不需要使用的就不加载。对于全部封装成一个公共库的做法，这样既能实现解耦，又可以减少包的大小。

### 地图模块集成Framework

业务上较多APP使用了高德地图SDK，此模块属于功能组件，下面把高德地图全部封装到一个SDK里面供给其他APP使用

新建Framework

![](https://upload-images.jianshu.io/upload_images/301129-c65dfbc4771203bd.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

命名Framework

![](https://upload-images.jianshu.io/upload_images/301129-dcf33640e74d8e7f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

修改最低支持的版本

![](https://upload-images.jianshu.io/upload_images/301129-dfebc804de3d4b7f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

导入高德地图SDK

![](https://upload-images.jianshu.io/upload_images/301129-6d0c17b4222adcaa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

添加依赖库(高德地图需要的依赖库）

![](https://upload-images.jianshu.io/upload_images/301129-6f3cb58cb72a04f2.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

统一导入到`GDSDK.h`中

![](https://upload-images.jianshu.io/upload_images/301129-d63e64bfa0a55512.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

新建TViewController.swift，适配Swift项目导入（如果没有Swift文件存在，SDK是不能被Swift项目导入的）

![](https://upload-images.jianshu.io/upload_images/301129-2c0822b7aaf3e4fe.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在TViewController中声明MAMapView变量，解决Could not find auto-linked framework问题

![](https://upload-images.jianshu.io/upload_images/301129-ed42437e9513b517.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

编译通过，地图模块SDK集成完毕，下面介绍在项目中使用`GDSDK`。

### SDK集成

新建项目DituDemo

![](https://upload-images.jianshu.io/upload_images/301129-15e82266f1ee8906.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

![](https://upload-images.jianshu.io/upload_images/301129-e54d0287d4854a32.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

拖入我们封装的GDSDK

![](https://upload-images.jianshu.io/upload_images/301129-31de51b7b11be371.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

导入二进制GDSDK

![](https://upload-images.jianshu.io/upload_images/301129-8d8595ea79cfd83b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

在ViewController中导入GDSDK，并声明遍历mapView，编译通过。至此，地图组件制作完成，其他项目可以导入此SDK开发地图业务方面的功能。

### 注意

* GDSDK制作完成一定记得添加TViewController文件，并且声明MAMapView的变量。这样SDK才会auto link framework

* 记得添加高德SDK需要的依赖库，如果高德SDK需要更新，记得及时更新需要的依赖库

* 代码参考[GDSDK](https://github.com/jackyshan/GDSDKTest)

