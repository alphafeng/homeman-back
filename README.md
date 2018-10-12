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

| Name         | Type        | Des                                                          |
| ------------ | ----------- | ------------------------------------------------------------ |
| type         | string(8)   | TODO-代办事项<br />DATE-某一天的工作，用于覆盖周期性任务<br />DAY-每天重复<br />MON-每周一重复<br />TUES-每周二重复<br />WED-每周三重复<br />THUR-每周四重复<br />FRI-每周五重复<br />SAT-每周六重复<br />SUN-每周日重复 |
| startDate    | string(8)   | 开始日期，仅在type为DATE时生效                               |
| expDate      | string(8)   | 截止日期                                                     |
| beginTime    | string(8)   | 24小时，eg: 9:00                                             |
| endTime      | string(8)   | 24小时，eg: 13:00                                            |
| memo         | string(512) | 任务描述                                                     |
| executor     | string(32)  | 执行者                                                       |
| isTop        | string(1)   | 是否置顶（Y/N），仅当type为TODO时生效                        |
| isActive     | string(1)   | 是否生效（Y/N），对于TODO任务，一旦完成，即改为失效状态      |
| *creator*    | string(32)  | 创建者                                                       |
| *createTime* | timestamp   | 数据库自动生成                                               |



**处理逻辑：**

1. 获取本周日期，现实本周的timetable
2. 查询***本周范围内***每一天`type`为`DATE`的任务；如果当天没有`type`为`DATE`的任务，则查询每周重复任务记录；如果都没有，则显示空任务
3. 查询所有未完成的`TODO`任务



**主要接口：**

- schedule/public/all：获取所有公共日程

- schedule/public/create：创建公共日程

- schedule/me/all：获取我的所有日程

- schedule/me/create：创建我的日程