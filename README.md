# CoreLibs

这是一个MVP-Based, 集成了很多常用库, 工具以及控件的库集合, 旨在提高开发效率并保证一定的代码质量.

## 引入方法

* 下载CoreLibs
* 新建一个Android工程
* 将CoreLibs作为一个Module导入该项目
* 主模块添加CoreLibs的依赖
* 在最外层的build.gradle文件中添加maven库:

````
....
allprojects {
    repositories {
        jcenter()
        maven { url "https://jitpack.io" }
    }
}

````

* 新建一个Application类并在onCreate中加入如下代码:

````
GlobalExceptionHandler.getInstance().init(this, getResources().getString(R.string.app_name)); //初始化全局异常捕获
ToastMgr.init(getApplicationContext()); //初始化Toast管理器
RetrofitFactory.init(Urls.ROOT_API); //初始化Retrofit接口工厂
PreferencesHelper.init(getApplicationContext()); //初始化SharedPreferences工具类
Configuration.enableLoggingNetworkParams(); //打开网络请求Log打印
FileDownloader.init(getApplicationContext()); //初始化下载工具
GalleryFinalConfigurator.config(getApplicationContext()); //初始化GalleryFinal
````
* 根据服务器接口返回JSON的结构, 新建一个实体类, 并集成IBaseData.
* 根据需要项目的主题可以使用CoreLibs中的AppBaseCompactTheme.

## 使用方法

请参考 https://www.gitbook.com/book/theseyears/android-architecture-journey

## Change Log

* 2016-02 完善雏形
* 2016-04 完善 [文档](https://www.gitbook.com/book/theseyears/android-architecture-journey)
* 2016-09-07 添加Studio插件 [MvpClassesGenerator](https://github.com/TheseYears/MvpClassesGenerator)
* 2016-09-22 
    1. 扩展Adapter相关工具类 <BR/>
        * 添加多布局支持
        * 添加RecyclerView支持
        * 添加RecyclerView的多布局支持
    2. 添加RecyclerView的Header, Footer支持
    3. 扩展PTR组件 <BR/>
        * 添加对RecyclerView的支持