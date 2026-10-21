# 数字社区 App（LianXiGongNeng003）

> 个人练习 Demo —— 山西省第二十届职业院校技能大赛（中职组）移动应用与开发赛项，
> 模块B「移动应用前端开发」数字社区主题的练习项目，基于 DCloud MUI 框架。

很菜喵，慢慢来 OVO，有路过的大佬愿意指点指点就太感谢了 ^_^

---

## 📱 页面功能

| 页面 | 文件 | 标题 | 主要接口 |
|---|---|---|---|
| 登录页 | `index.html` | 数字社区 | `/api/login` |
| 主框架 | `exe/page.html` | — | 底部 5 个 Tab |
| 首页 | `exe/home.html` | 首页 | `rotation/list`、`community-activity/activity-list`、`community-activity/dynamic-list` |
| 友邻社交 | `exe/ylsj.html` | — | `friendly_neighborhood/list` |
| 友邻列表（另一版） | `exe/DOmeKong.html` | — | `friendly_neighborhood/list` |
| 帖子详情 | `exe/XiangQingHTML.html` | 详情 | `friendly_neighborhood/{id}` |
| 新增评论 | `exe/XiangZhengQinglUenHTML.html` | 新增评论 | `friendly_neighborhood/add/comment` |
| 社区公告 | `exe/li_6.html` | 社区公告 | `community_notice/list` |
| 公告详情 | `exe/QuanBuHTML.html` | 公告详情 | `community_notice/{id}` |
| **数据分析** | `exe/sjfx.html` | 数据分析 | 3 个图表接口 |
| 数据分析（空壳） | `exe/ajfx.html` | 数据分析 | — |

## 📊 数据分析三张图

| 图表 | 接口 | 官方字段 |
|---|---|---|
| 条形图（评论数·按性别） | `/api/data/comment/list_1` | `name`（月份）/ `woman` / `man` |
| 折线图（快递数量趋势） | `/api/dataAnalysis/information/list_1` | `name`（1~12月）/ `value` |
| 饼状图（前五亲子活动占比） | `/api/dataAnalysis/activity/list_1` | `name`（排名前五亲子活动）/ `count`（报名人数）/ `data`（占比）|

> 💡 饼图接口 **`name` 已经是「排名前五的亲子类型活动」**，后端已排序取前五，
> 前端只需把 `name` / `count` 组装成 `[{name, value}]`，echarts 会自动算百分比。

## 🎯 练到的知识点

| 技能 | 位置 |
|---|---|
| 登录 + token | `index.html` |
| 底部 Tab + subpages | `page.html` |
| 轮播图首尾复制循环 | `home.html` |
| 宫格入口 | `home.html` |
| 横向滚动卡片列表 | `home.html` |
| 列表渲染 | `ylsj.html` / `li_6.html` |
| 跨页传参（`extras` + `plus.storage` 兜底）| `ylsj.html` → `XiangQingHTML.html` |
| **`beforeback` + `mui.fire` 返回刷新** | `XiangZhengQinglUenHTML.html` → `XiangQingHTML.html` |
| echarts 柱/折/饼 | `sjfx.html` |
| 手动组装图表数据 | `sjfx.html` 饼图 `{name, value}` |

## 🛠 技术栈

- **HTML5 / CSS3 / JavaScript**（原生，无构建工具）
- **MUI**（DCloud 移动端 UI 框架）
- **ECharts**（`js/echarts.js`）
- **Ajax**：`mui.ajax` + `Authorization: token`
- 打包：HBuilderX

## 📂 目录结构

```
.
├── index.html            登录页（入口）
├── manifest.json         HBuilderX App 配置
├── exe/                  业务页面（11 个）
├── css/                  mui.css / mui.min.css
├── js/                   http.js（地址配置）/ mui.js / mui.min.js / echarts.js
├── IMG/                  图片素材（约 8 MB）
└── fonts/                mui.ttf
```

## 🖼 关于 `IMG/` 目录

- 部分文件**用图片 MD5 值命名**（如 `56eeee9b....jpg`），这是素材库的命名习惯。
- ⚠️ **版权说明**：图片素材**并非本人原创**，版权归原作者所有。
  本仓库仅作个人学习练习，**不做任何商业用途**；如涉及侵权请联系删除。
- 💡 其中有一个 **2 MB 的 GIF**，已在 `.gitignore` 中排除。

## 🔌 用到的接口

| 功能 | 方法 | 路径 |
|---|---|---|
| 登录 | POST | `/api/login` |
| 首页轮播 | GET | `/api/rotation/list` |
| 社区信息 | GET | `/api/community/community/{id}` |
| 社区活动列表 | GET | `/api/community/community-activity/activity-list` |
| 社区动态列表 | GET | `/api/community/community-activity/dynamic-list` |
| 友邻帖子列表 | GET | `/api/community/friendly_neighborhood/list` |
| 友邻帖子详情 | GET | `/api/community/friendly_neighborhood/{id}` |
| 发布评论 | POST | `/api/community/friendly_neighborhood/add/comment` |
| 社区公告列表 | GET | `/api/community/community_notice/list` |
| 社区公告详情 | GET | `/api/community/community_notice/{id}` |
| 图表·条形 | GET | `/api/data/comment/list_1` |
| 图表·折线 | GET | `/api/dataAnalysis/information/list_1` |
| 图表·饼图 | GET | `/api/dataAnalysis/activity/list_1` |

> ⚠️ 路径是**脱敏后的写法**（去掉了平台前缀）。考场以**现场发放的接口文档**为准，**照抄路径**。

## ⚠️ 字段名坑（**已核对官方文档**）

| 接口 | 字段 | 说明 |
|---|---|---|
| `community-activity/activity-list` | **`titile`** | 官方就是拼错的 `titile`，**不是 `title`** |
| `community-activity/dynamic-list` | **`titile`** | 同上 |
| `community-activity/dynamic-list` | **`number`** | 评论数（不是 `commentNum`）|
| `friendly_neighborhood/list` | `title` | 这个接口是正常的 `title` |
| `friendly_neighborhood/list` | **`commentNum`** | 评论数（这个接口叫 `commentNum`）|
| `community_notice/list` | `noticeStatus` | **1=已读 / 0=未读**（integer，需转中文）|
| `community_notice/{id}` | `phone` | 联系电话 |
| `community_notice/{id}` | `createTime` | 发布时间 |

## 🚀 本地运行

用 **HBuilderX** 打开本文件夹，然后「运行 → 运行到手机或模拟器」。

**配置服务器地址**（编辑 `js/http.js`）：

```javascript
var http    = 'http://YOUR_SERVER_HOST:PORT';            // 调接口
var httpimg = 'http://YOUR_SERVER_HOST:PORT/prod-api';   // 显示图片
```

> ⚠️ `http` **不带** `/prod-api`；`httpimg` **带** `/prod-api` 且**末尾不要加 `/`**。

**接口约定**：

```json
{ "code": 200, "msg": "操作成功", "rows": [ ... ], "total": 10 }
```

需要认证的接口带：`headers: { 'Authorization': localStorage.getItem('token') }`

## 📝 待补（按赛题要求）

- [ ] **首页·社区名称**：调 `/api/community/community/{id}`，显示 `data.name`
- [ ] **首页·社区通知滚动播放**
- [ ] **宫格 8 个名称**：开门 / 我的房屋 / 我的车位 / 物业缴费 / 扫码取件 / 社区公告 / 社区电话 / 投诉建议
- [ ] **活动/动态列表标题**：`title` → **`titile`**（否则空白）
- [ ] **动态列表**：加评论数 `number`；布局改为「左文字 + 右图片」
- [ ] **底部导航**：改成 4 个（去掉「+」），并做当前页高亮
- [ ] **帖子列表**：加发布人 `publishName`
- [ ] **帖子详情**：加评论总数；**底部加评论输入框 + 发布按钮**（当前是跳转新页面）
- [ ] **公告列表**：加「查看详情」按钮；`noticeStatus` 1/0 转「已读/未读」
- [ ] **公告详情**：加发布时间 `createTime`、联系电话 `phone`
- [ ] `page.html` 缺 `sqfw.html`（社区服务）、`Jia.html`（+ Tab）
- [ ] `home.html` 九宫格入口缺 `li_1~li_5`、`li_7`、`li_8` 页面
- [ ] 打包 release 版 APK

## ⚠️ 说明

- 本仓库为**个人学习练习**，非生产级代码。
- 仓库内**不含**任何赛项原始资料、接口文档或真实服务器地址。
- **图片素材版权归原作者所有**，仅作学习用途。
- MUI 版权归 [DCloud](https://www.dcloud.io/)；ECharts 版权归 Apache 基金会。

## 📄 License

代码部分：学习用途，可自由参考。
图片素材：**不适用**，版权归原作者，请勿二次分发。
