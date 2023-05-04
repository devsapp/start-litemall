
> 注：当前项目为 Serverless Devs 应用，由于应用中会存在需要初始化才可运行的变量（例如应用部署地区、服务名、函数名等等），所以**不推荐**直接 Clone 本仓库到本地进行部署或直接复制 s.yaml 使用，**强烈推荐**通过 `s init ` 的方法或应用中心进行初始化，详情可参考[部署 & 体验](#部署--体验) 。

# start-litemall 帮助文档
<p align="center" class="flex justify-center">
    <a href="https://www.serverless-devs.com" class="ml-1">
    <img src="http://editor.devsapp.cn/icon?package=start-litemall&type=packageType">
  </a>
  <a href="http://www.devsapp.cn/details.html?name=start-litemall" class="ml-1">
    <img src="http://editor.devsapp.cn/icon?package=start-litemall&type=packageVersion">
  </a>
  <a href="http://www.devsapp.cn/details.html?name=start-litemall" class="ml-1">
    <img src="http://editor.devsapp.cn/icon?package=start-litemall&type=packageDownload">
  </a>
</p>

<description>

快速部署一个litemall电商应用系统到阿里云函数计算

</description>

<codeUrl>

- [:smiley_cat: 代码](https://github.com/devsapp/start-litemall/tree/main/src)

</codeUrl>
<preview>



</preview>


## 前期准备

使用该项目，您需要有开通以下服务：

<service>



| 服务 |  备注  |
| --- |  --- |
| 函数计算 FC |  电商系统web部署到函数计算平台 |

</service>

推荐您拥有以下的产品权限 / 策略：
<auth>



| 服务/业务 |  权限 |  备注  |
| --- |  --- |   --- |
| 函数计算 | AliyunFCFullAccess |  电商系统web部署到函数计算平台 |

</auth>

<remark>

您还需要注意：   
1. 项目Yaml中，使用了一个 init 空项目得到工具生成的自定义域名， 然后在真正部署函数之前，声明了`actions`，利用得到的自定义域名参与前端项目的 build, 最后得到预期的目标产物。

2. 本示例给函数配置的环境变量 `SPRING_DATASOURCE_DRUID_URL` 使用的是公网地址， 如果您想改成使用 vpc 地址， 请参考 s.yaml 中有关 vpcConfig 的注释

3. 本示例提供了测试的数据库以及账号和密码， 如果是您自己的数据库， 您需要对执行如下命令， 完成数据库的初始化。
> 注意 host，user, pwd 都需要改成您自己的
  
```bash
$ mysql -h 127.0.0.1 -uroot -p123456 < litemall-db/sql/litemall_schema.sql
$ mysql -h 127.0.0.1 -uroot -p123456 litemall < litemall-db/sql/litemall_table.sql
$ mysql -h 127.0.0.1 -uroot -p123456 litemall < litemall-db/sql/litemall_data.sql
```

</remark>

<disclaimers>

免责声明：   
本示例提供了测试的数据库以及账号和密码，只用于个人快速体验， 不能用于生产。 如若使用在生产，产生了恶意攻击或者资损概不负责。

</disclaimers>

## 部署 & 体验

<appcenter>
   
- :fire: 通过 [Serverless 应用中心](https://fcnext.console.aliyun.com/applications/create?template=start-litemall) ，
  [![Deploy with Severless Devs](https://img.alicdn.com/imgextra/i1/O1CN01w5RFbX1v45s8TIXPz_!!6000000006118-55-tps-95-28.svg)](https://fcnext.console.aliyun.com/applications/create?template=start-litemall) 该应用。
   
</appcenter>
<deploy>
    
- 通过 [Serverless Devs Cli](https://www.serverless-devs.com/serverless-devs/install) 进行部署：
  - [安装 Serverless Devs Cli 开发者工具](https://www.serverless-devs.com/serverless-devs/install) ，并进行[授权信息配置](https://docs.serverless-devs.com/fc/config) ；
  - 初始化项目：`s init start-litemall -d start-litemall `
  - 进入项目，并进行项目部署：`cd start-litemall && s deploy - y`
   
</deploy>

## 应用详情

<appdetail id="flushContent">

浏览器打开域名, 按照提示登录，就可以进入后台管理系统页面； 在当前域名加上 /vue/index.html, 就可以访问前台页面。

**后台管理页面**
![](https://img.alicdn.com/imgextra/i1/O1CN0189KTwa1CjAggEK97M_!!6000000000116-2-tps-1738-1004.png)

**前台页面**
![](https://img.alicdn.com/imgextra/i3/O1CN01z5juwO1JdrP9paB2m_!!6000000001052-2-tps-1749-1010.png)

> 在本地使用该项目时，不仅可以部署，还可以进行更多的操作，例如查看日志，查看指标，进行多种模式的调试等，这些操作详情可以参考[函数计算组件命令文档](https://github.com/devsapp/fc#%E6%96%87%E6%A1%A3%E7%9B%B8%E5%85%B3) ;








</appdetail>

## 使用文档

<usedetail id="flushContent">

本项目是将流行的电商商城[litemall]([https://github.com/linlinjava/litemall])项目部署到阿里云 Serverless 平台（函数计算 FC）。

项目包括4个系统和9个模块。

- 基础系统子系统：由数据库、litemall-core模块、litemall-db模块和litemall-all模块组成。
- 小商场子系统：由litemall-wx-api模块、litemall-wx模块和renard-wx模块组成。
- 轻商城子系统：由litemall-wx-api模块和litemall-vue模块组成。
- 管理后台子系统：由litemall-admin-api模块和litemall-admin模块组成。

![](https://img.alicdn.com/imgextra/i3/O1CN01Ru8eSQ1Xq8dtUv0w2_!!6000000002974-2-tps-1849-842.png)

更多详情请参考 [litemall](https://github.com/linlinjava/litemall)

</usedetail>


<devgroup>


## 开发者社区

您如果有关于错误的反馈或者未来的期待，您可以在 [Serverless Devs repo Issues](https://github.com/serverless-devs/serverless-devs/issues) 中进行反馈和交流。如果您想要加入我们的讨论组或者了解 FC 组件的最新动态，您可以通过以下渠道进行：

<p align="center">  

| <img src="https://serverless-article-picture.oss-cn-hangzhou.aliyuncs.com/1635407298906_20211028074819117230.png" width="130px" > | <img src="https://serverless-article-picture.oss-cn-hangzhou.aliyuncs.com/1635407044136_20211028074404326599.png" width="130px" > | <img src="https://serverless-article-picture.oss-cn-hangzhou.aliyuncs.com/1635407252200_20211028074732517533.png" width="130px" > |
| --------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| <center>微信公众号：`serverless`</center>                                                                                         | <center>微信小助手：`xiaojiangwh`</center>                                                                                        | <center>钉钉交流群：`33947367`</center>                                                                                           |
</p>
</devgroup>
