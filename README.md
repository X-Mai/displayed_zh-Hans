# displayed_zh-Hans
### ios系统弹框文字指定中文显示

----

### 需求简介：
- 产品要求H5中js打开相册、相机、选择文件时候系统弹出框中显示内容为中文

- 在线客服测试地址：https://qiyukf.com/client?k=1fa1db97aec638fdc98a275e7798ed84&wp=1

- ios_多椒Demo中，使用自己公司研发的多椒SDK集成使用；其中多椒SDK中有一个"在线客服(H5方式接入网易七鱼的客服)"功能，进入在线客服页面后，点击其中的拍照、视频、文件(网易客服那边JS方式打开相机、相册、文件)时候，弹出的系统弹框显示为英文。（前提：当前手机语言设置的是简体中文）

- 直接使用在线客服地址在safari浏览器上打开，根据上面的操作，弹出的系统弹框显示为中文（前提：当前手机语言设置的是简体中文）

<img width="1104" alt="3" src="https://user-images.githubusercontent.com/19405301/163746924-c0be5bb1-6a06-4f77-9810-251a72eee085.png">

### 解决办法：
- 分析：Js中有根据APP中对应的语言国际化进行判断展示是否为中文、英文。在解决问题的时候，检查ios_多椒Demo项目中没有配置简体中文(xocde设置中没有简体中文、打包后的ipa解压后里面也没有zh-Hans.lproj),虽然当前手机系统设置为中文，但是app中没有设置对应中文，在H5加载在线客服时候识别到默认英文才，结果导致系统弹框显示为英文
-  解决办法一：ios_多椒Demo中配置添加简体中文
<img width="950" alt="4" src="https://user-images.githubusercontent.com/19405301/163747567-9f04048d-0b55-419d-ab0c-4555b7bb0a28.png">
-  解决办法二：将zh-Hans.lproj文件当做对接sdk中一元，直接给接入的工程使用，添加进去会自动添加设置简体中文(我们功能在SDK，采用这个办法；需要注意：zh-Hans.lproj和bundle资源文件同一级别，不能放bundle资源里)
<img width="979" alt="5" src="https://user-images.githubusercontent.com/19405301/163747863-7dbbb766-7c0b-4f04-a792-8fea407a9ffc.png">


### 总结：
出包的ipa中添加简体中文即可解决问题
