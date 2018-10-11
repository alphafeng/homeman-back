## homeman-back

homeman后台程序，主要功能：
- account 账户管理
- schedule 日程管理
- financial 财务管理

### account 账户管理

**account/wxlogin：微信登录**

| name      | type | Des  |
| --------- | ---- | ---- |
| openid    |      |      |
| avatarurl |      |      |
| nickname  |      |      |

### schedule 日程管理

**schedule数据结构**

| Name     | Type        | Des                                                          |
| -------- | ----------- | ------------------------------------------------------------ |
| type     | string(8)   | TODO-代办事项<br />DAY-每天重复<br />MON-每周一重复<br />TUES-每周二重复<br />WED-每周三重复<br />THUR-每周四重复<br />FRI-每周五重复<br />SAT-每周六重复<br />SUN-每周日重复 |
| memo     | string(512) | 任务描述                                                     |
| executor | string(32)  | 执行者                                                       |
| expdate  | string(8)   | 截止日期                                                     |
| istop    | string(1)   | 是否置顶（Y/N）                                              |

**schedule/public/all：获取所有公共日程**

**schedule/public/create：创建公共日程**

**schedule/me/all：获取我的所有日程**

**schedule/me/create：创建我的日程**