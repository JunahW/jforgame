﻿  ## 中文 | [English](README_EN.md)  

  ## 项目介绍　　
  jforgame，是一个用java编写的轻量级高性能手游服务端框架。项目提供各种支持快速二次开发的组件，以及对生产环境的服务进行管理的工具。同时，为了使用户能够快速上手，项目提供了若干常用业务功能作为演示。

  ## 项目特点  
  * 搭配框架博客栏目教程，快速理解项目模块原理  
  * 支持socket/webSocket接入，兼容手游/页游服务端架构  
  * 通信协议支持protobuf或普通javabean，为客户端提供多种选择  
  * 强大的客户端异步/同步api，轻松实现跨进程通信
  * 使用自定义的轻量级orm工具库，支持多数据源，自动建表增加字段，支持表字段全量/增量更新
  * 框架提供多种组件，可以直接二次开发业务逻辑  
  * 提供热更机制以及jmx接口，方便对生产项目进行监控与维护
  * 有独立http管理后台网站，为游戏运维/运营提供支持  --> [后台管理系统](https://github.com/kingston-csj/gamekeeper)  


  ## 模块组织结构  
  ``` 
  jforgame
  ├── jforgame-commons --基础公共服务  
  ├── jforgame-runtime --应用运行时监控数据，包括内存，线程，类等等
  ├── jforgame-socket-parent     --Tcp socket通信，包括io网关模块，消息路由，会话管理，包含netty和mina版本      
      ├── jforgame-socket-api    --服务端/客户端基础API接口
      ├── jforgame-socket-netty  --netty版实现，包含简易WebSocket
      ├── jforgame-socket-mina   --mina版实现
  ├── jforgame-orm     --使用自定义精心定制的orm库，用于数据库表记录与程序pojo对象的相互转换        
  ├── jforgame-spring-boot-starter-data    --以springboot的starter模式封装对配置数据的读取，支持csv，excel等文件格式。支持配置数据热更新        
  ├── jforgame-hotswap  --支持游戏业务热更新
  ├── jforgame-codec-parent         --用于socket通信的数据编解码  
      ├── jforgame-codec-api        --消息编解码API接口
      ├── jforgame-codec-protobuf   --protobuf实现
      ├── jforgame-socket-mina      --普通javabean，反射实现  
  ├── jforgame-demo  --游戏基础组件以及业务逻辑模块  
  |    ├──  cache包，使用guava cache库，用于支持系统的缓存框架    
  |    ├──  db包，使用独立线程，异步处理玩家及公共数据的持久化  
  |    ├──  monitor包，系统监控模块，包括使用jmx对程序进行监控  
  |    ├──  listener包，事件驱动模型  
  |    ├──  doctor包，采用Groovy执行任意动态代码，或JDK的instrument机制修改类方法体 
  |    ├──  cross包，跨服赛事的通信基础 
  |    ├──  game/gm包，游戏内部金手指命令
  |    ├──  game/admin包，游戏运营/运维后台命令  
  |    ├──  redis包，跨服通信（比如跨服排行榜）  
  |    ├──  tools包，简化项目开发的辅助小工具  
  |    └──  utils包，各种工具类    
  ```


  ## 第三方技术栈 
  名称 | 用途             | 官网  
  ----|----------------|----     
  Mina | nio socket 框架  | [http://mina.apache.org/](http://mina.apache.org/)  
  Netty | nio socket 框架  | [http://netty.io/](http://netty.io/)   
  jprotobuf | protobuff协议层注解 | [https://github.com/jhunters/jprotobuf](https://github.com/jhunters/jprotobuf)  
  Guava | 玩家数据缓存系统       | [https://github.com/google/guava](https://github.com/google/guava)  
  Jedis | 数据缓存,全服排行榜     | [https://redis.io](https://redis.io/)  
  quartz | job调度任务        | [http://www.quartz-scheduler.org/](http://www.quartz-scheduler.org/) 
  groovy | 热更新维护相关        | [http://www.groovy-lang.org/](http://www.groovy-lang.org/)　　  
  slf4j+log4j | 日志系统           | [https://www.slf4j.org/](https://www.slf4j.org/)  
  maven | 依赖管理及项目构建      | [http://maven.apache.org/](http://maven.apache.org/)  


  ## 快速开始  
  1. 使用git下载代码 git clone https://github.com/kingston-csj/jforgame;  
  2. 将代码导入带有maven插件的IDE(选择根目录下的pom.xml文件);  
  3. 新建数据库game_data_001和game_user_001，并分别导入test/resources下的同名sql文件;  
  4. 启动服务端，入口为ServerStartup类;    
  （如果导入项目所有模块，还需要设置好工作区间。例如idea设置：run->EditConfirations->Workingdirectory,设置为，**\jforgame\jforgame-demo。）;  
  5. 启动客户端，入口为ClientStartup类;  
  （如果导入项目所有模块，还需要设置好工作区间。例如idea设置：run->EditConfirations->Workingdirectory,设置为，**\jforgame\jforgame-demo。)  

  各模块demo教程 --> [wiki](https://github.com/kingston-csj/jforgame/wiki/Examples)  

  本栏目详细教程 -->  
  [从零开始搭建游戏服务器框架](https://blog.csdn.net/littleschemer/category_9269220.html)  
  [漫谈游戏服务器](https://blog.csdn.net/littleschemer/category_12576391.html)


  欢迎star/fork，欢迎学习/使用，期待一起贡献代码！！
  
  ## 请作者喝杯咖啡
  如果您觉得有所收获，可以请作者喝杯咖啡。大家的支持，促使我不断改进优化，谢谢！  
   ![](/screenshots/wx.jpg "微信收款码")
   ![](/screenshots/zfb.jpg "支付宝收款码")  

  ## 一起交流
  如果您发现bug，或者有任何疑问，请提交issue !!  
  mysql合服工程，基于jforgame的分布式五子棋源代码，私聊获取。  
  合作/咨询：+Q 641711541  
  我刚开通了知识星球，来向我提问吧~~
  ![](/screenshots/zsxq.jpg "知识星球")

   ## 免责申明
   本项目只用于学习研究，禁止用于非法获利和商业活动。如产生法律纠纷与作者无关！！
