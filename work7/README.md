# Frontends 第七轮考核
## 目的

- 熟悉nodejs的使用
- 掌握对数据库的增删改查操作
- 了解websocket协议
- 掌握socket.io的使用

## 背景

众所周知，FanOne是个家喻户晓的**Aquaman**，她经常在社交软件上找小哥哥们聊天，以至于被多个平台封杀，请你写一个IM即时通信系统，让FanOne能聊天自由吧！

## 任务

> 编写一个 IM 即时通信系统 支持单聊，并且支持查找一定时间内的聊天记录，并编写前端页面

1. 对于聊天内容，请将其保存在数据库中
2. 聊天使用socket.io进行通信
3. 前端请使用TypeScript+Vue3
4. 后端在nodejs方面可以随意选择，这里给出推荐的几种选择，是否使用TypeScript自行决定
- 后端框架
  - express(通用且比较简单)
  - koa(比exprees还要简洁)
  - nest.js(起步ts，入门困难，架构体系完善，企业级框架)
  - egg.js(js企业级框架，配套完善)
- 数据库
  - mysql(关系型数据库，推荐使用orm进行操作) 
  - mongodb(非关系型数据库，可以不需要orm进行操作)
- ORM
  - prisma(最强nodejs的ORM，拥有强大的功能)
  - typeorm(起步ts，面向对象语法的ORM，比较繁琐) 
  - sequelize(比较稳定)

### Bonus

1. 支持图片功能，(可以在node后端使用fs模块将图片保存到本地)
2. 支持群聊功能
3. 连接Redis，将聊天记录保存在redis中，可以设置过期时间

## 参考

1. socket.io官方文档 https://socket.io/zh-CN/
2. socket.io官方示例(Part I II III IV) https://socket.io/zh-CN/get-started/
3. socket.io官方示例(前端架构) https://socket.io/zh-CN/how-to/use-with-vue
4. prisma 最强nodejs的ORM，拥有强大的功能 https://prisma.yoga/
5. typeorm 面向对象语法的ORM，比较繁琐 https://typeorm.io/