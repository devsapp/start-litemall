# Serverless Litemall 电商商城案例

> 快速部署和体验Serverless架构下的Litemall电商商城项目

- [Serverless Litemall 电商商城案例](#serverless-litemall-电商商城案例)
  - [体验前准备](#体验前准备)
  - [代码与预览](#代码与预览)
  - [快速部署和体验](#快速部署和体验)
    - [在线快速体验](#在线快速体验)
    - [在本地部署体验](#在本地部署体验)
  - [项目使用注意事项](#项目使用注意事项)
  - [应用详情](#应用详情)
  - [参考](#参考)

## 体验前准备

该应用案例需要您开通[阿里云函数计算](https://fcnext.console.aliyun.com/) 产品；并建议您当前的账号有一下权限存在`FCDefaultRole`。

## 代码与预览

- [:octocat: 源代码](https://github.com/devsapp/start-litemall/tree/main/src)
- [:earth_africa: 后台管理效果预览](https://img.alicdn.com/imgextra/i1/O1CN0189KTwa1CjAggEK97M_!!6000000000116-2-tps-1738-1004.png)
- [:earth_africa: 用户前端效果预览](https://img.alicdn.com/imgextra/i3/O1CN01z5juwO1JdrP9paB2m_!!6000000001052-2-tps-1749-1010.png)

## 快速部署和体验
### 在线快速体验

- 通过阿里云 **Serverless 应用中心**： 可以点击 [【🚀 部署】](https://fcnext.console.aliyun.com/applications/create?template=start-litemall) ，按照引导填入参数，快速进行部署和体验。
  
### 在本地部署体验

1. 下载安装 Serverless Devs：`npm install @serverless-devs/s` 
    > 详细文档可以参考 [Serverless Devs 安装文档](https://github.com/Serverless-Devs/Serverless-Devs/blob/master/docs/zh/install.md)
2. 配置密钥信息：`s config add`
    > 详细文档可以参考 [阿里云密钥配置文档](https://github.com/devsapp/fc/blob/main/docs/zh/config.md)
3. 初始化项目：`s init start-litemall -d start-litemall`
4. 进入项目后部署：`s deploy`
5. 部署过程中可能需要阿里云密钥的支持，部署完成之后会获得到临时域名可供测试

> 浏览器打开域名, 按照提示登录，就可以进入后台管理系统页面； 在当前域名加上 /vue/index.html, 就可以访问前台页面。

**后台管理页面**
![](https://img.alicdn.com/imgextra/i1/O1CN0189KTwa1CjAggEK97M_!!6000000000116-2-tps-1738-1004.png)

**前台页面**
![](https://img.alicdn.com/imgextra/i3/O1CN01z5juwO1JdrP9paB2m_!!6000000001052-2-tps-1749-1010.png)

> 在本地使用该项目时，不仅可以部署，还可以进行更多的操作，例如查看日志，查看指标，进行多种模式的调试等，这些操作详情可以参考[函数计算组件命令文档](https://github.com/devsapp/fc#%E6%96%87%E6%A1%A3%E7%9B%B8%E5%85%B3) ;

## 项目使用注意事项

1. 项目Yaml中，使用了一个 init 空项目得到工具生成的自定义域名， 然后在真正部署函数之前，声明了`actions`，利用得到的自定义域名参与前端项目的 build, 最后得到预期的目标产物。

2. 本示例给函数配置的环境变量 `SPRING_DATASOURCE_DRUID_URL` 使用的是公网地址， 如果您想改成使用 vpc 地址， 请参考 s.yaml 中有关 vpcConfig 的注释

3. 本示例提供了测试的数据库以及账号和密码， 如果是您自己的数据库， 您需要对执行如下命令， 完成数据库的初始化。
> 注意 host，user, pwd 都需要改成您自己的
  
```bash
$ mysql -h 127.0.0.1 -uroot -p123456 < litemall-db/sql/litemall_schema.sql
$ mysql -h 127.0.0.1 -uroot -p123456 litemall < litemall-db/sql/litemall_table.sql
$ mysql -h 127.0.0.1 -uroot -p123456 litemall < litemall-db/sql/litemall_data.sql
```

## 应用详情

本项目是将流行的电商商城[litemall]([https://github.com/linlinjava/litemall])项目部署到阿里云 Serverless 平台（函数计算 FC）。

项目包括4个系统和9个模块。

- 基础系统子系统：由数据库、litemall-core模块、litemall-db模块和litemall-all模块组成。
- 小商场子系统：由litemall-wx-api模块、litemall-wx模块和renard-wx模块组成。
- 轻商城子系统：由litemall-wx-api模块和litemall-vue模块组成。
- 管理后台子系统：由litemall-admin-api模块和litemall-admin模块组成。

![](https://img.alicdn.com/imgextra/i3/O1CN01Ru8eSQ1Xq8dtUv0w2_!!6000000002974-2-tps-1849-842.png)

更多详情请参考 [litemall](https://github.com/linlinjava/litemall)

通过 Serverless Devs 开发者工具，您只需要几步，就可以体验 Serverless 架构，带来的降本提效的技术红利。


## 参考
使用开源的Litemall电商商城系统: [litemall](https://github.com/linlinjava/litemall)

-----

> - Serverless Devs 项目：https://www.github.com/serverless-devs/serverless-devs   
> - Serverless Devs 文档：https://www.github.com/serverless-devs/docs   
> - Serverless Devs 钉钉交流群：33947367    