# 数字社区 App · DigitalLife

> 山西省第二十届职业院校技能大赛（中职组）移动应用与开发赛项
> 模块B「移动应用前端开发」数字社区主题练习项目，基于 DCloud MUI 框架。

很菜喵，慢慢来 OVO，有路过的大佬愿意指点指点就太感谢了 ^_^

---

## 📱 页面功能

| 页面 | 文件 | 说明 |
|---|---|---|
| 登录页 | `index.html` | 账号密码登录、JSON 提交、存 token、跳主框架 |
| 主框架 | `exe/page.html` | 底部 4 个 Tab + subpages，**切换有当前页高亮** |
| 首页 | `exe/home.html` | 社区名称 + 轮播图 + 通知滚动 + 宫格 + 活动列表 + 动态列表 |
| 友邻社交 | `exe/ylsj.html` | 帖子列表（图片 / 标题 / 发布人 / 点赞数）|
| 帖子详情 | `exe/SeiJiaoXinagQing.html` | 帖子详情 + 评论列表 + 发表评论 |
| 社区公告 | `exe/li_6.html` | 全部 / 未读 / 已读 三个页签 + 通知列表 + 查看详情 |
| 公告详情 | `exe/QuanBuHTML.html` | 标题 / 时间 / 内容 / 发布单位 / 联系电话 |
| **数据分析** | `exe/sjfx.html` | echarts 条形图 + 折线图 + 饼图 |

## ✅ 四个任务完成情况

### 任务1 社区首页

| 要求 | 实现 |
|---|---|
| 顶部**所在社区名称** | ✅ `community/community/1` → `data.name` |
| 轮播图 | ✅ `rotation/list`，首尾复制节点实现无限循环 + 圆点指示器 |
| **社区通知滚动播放** | ✅ `<marquee scrollamount="4">` |
| 宫格 8 个快捷功能 | ✅ 开门 / 我的房屋 / 我的车位 / 物业缴费 / 扫码取件 / 社区公告 / 社区电话 / 投诉建议 |
| 社区活动横向列表 | ✅ `flex` + `overflow-x:auto`，图片 + `titile` + `comDistance` |
| 社区动态列表 | ✅ **图片在右**（`mui-pull-right`）+ `titile` + `number`（评论数）+ `createTime` |
| 底部导航 4 个 + **颜色标记当前页** | ✅ 首页 / 友邻社交 / 社区服务 / 数据分析，切换时切 `mui-active` |

### 任务2 友邻社交

| 要求 | 实现 |
|---|---|
| 标题栏 + 帖子列表 | ✅ |
| 列表项：图片 / 发布人 / 点赞数 | ✅ `imgUrl` / `publishName` / `likeNum` |
| 点击进详情 | ✅ `extras` + `plus.storage` 双保险 |
| 详情：发布人 / 发布时间 / 发布内容 | ✅ `publishName` / `publishTime` / `publishContent` |
| 评论总数 | ✅ |
| 评论：头像 / 昵称 / 日期 / 点赞数 / 内容 | ✅ `avater` / `userName` / `pulishTime` / `likeNum` / `content` |
| 底部发表评论 | ✅ 按钮 + 输入 + POST `add/comment`，成功后重新加载评论 |

### 任务3 社区公告

| 要求 | 实现 |
|---|---|
| 状态菜单栏 | ✅ 全部 / 未读 / 已读 |
| **点击状态显示对应列表** | ✅ `loadNotice({noticeStatus: 0/1}, 容器)` |
| 列表项：标题 / 状态 / 内容 / 时间 / **查看详情按钮** | ✅ 全部有；`noticeStatus` 1/0 已转「已读/未读」 |
| 点击进详情 | ✅ |
| 详情：标题栏 / 标题 / **发布时间** / 内容 / **发布单位** / **联系电话** | ✅ 6 项齐全（`createTime` / `releaseUnit` / `phone`）|

### 任务4 数据分析

| 图表 | 接口 | 字段 |
|---|---|---|
| 条形图（评论数·按性别）| `/api/data/comment/list_1` | `name`（月份）/ `woman` / `man` |
| 折线图（快递数量趋势）| `/api/dataAnalysis/information/list_1` | `name`（1~12月）/ `value` |
| 饼状图（前五亲子活动占比）| `/api/dataAnalysis/activity/list_1` | `name`（排名前五）/ `count`（报名人数）/ `data`（占比）|

> 💡 饼图接口的 `name` 后端**已经是「排名前五的亲子类型活动」**，前端只需组装 `[{name, value}]`，
> echarts 自动算百分比，`formatter: '{b}: {d}%'` 显示「名称: 比例」。

## 🎯 练到的知识点

| 技能 | 位置 |
|---|---|
| 登录 + token + JSON 提交 | `index.html` |
| 底部 Tab + subpages + **高亮切换** | `page.html` |
| 轮播图首尾复制循环 | `home.html` |
| 横向滚动卡片列表 | `home.html` |
| 动态列表「左字右图」 | `home.html` |
| 通知滚动 marquee | `home.html` |
| 列表渲染 + 事件委托 | `ylsj.html` / `li_6.html` |
| 跨页传参（`extras` + `plus.storage` 兜底）| `ylsj.html` → `SeiJiaoXinagQing.html` |
| 发表评论 + 成功后重载 | `SeiJiaoXinagQing.html` |
| **分段控件页签 + 接口条件筛选** | `li_6.html` |
| echarts 柱 / 折 / 饼 | `sjfx.html` |
| 手动组装图表数据 + 类型容错 | `sjfx.html` 饼图 |

## 🛠 技术栈

- **HTML5 / CSS3 / JavaScript**（原生，无构建工具）
- **MUI**（DCloud 移动端 UI 框架）
- **ECharts**（`js/echarts.js`）
- **Ajax**：`mui.ajax` + `Authorization: token`
- **HTML5+**：`plus.webview` / `plus.storage` / `plus.nativeUI`
- 打包：HBuilderX

## 📂 目录结构

```
.
├── index.html                    登录页（入口）
├── manifest.json                 HBuilderX App 配置
├── exe/
│   ├── page.html                 主框架（底部 4 Tab + subpages）
│   ├── home.html                 首页
│   ├── ylsj.html                 友邻社交列表
│   ├── SeiJiaoXinagQing.html     帖子详情 + 发表评论
│   ├── li_6.html                 社区公告列表
│   ├── QuanBuHTML.html           公告详情
│   └── sjfx.html                 数据分析（三图）
├── css/
│   ├── mui.css
│   └── mui.min.css
├── js/
│   ├── http.js                   服务器地址配置（需自己填，见下）
│   ├── mui.js / mui.min.js       MUI 框架
│   └── echarts.js                图表库
├── IMG/                          图片素材（约 8 MB）
└── fonts/
    └── mui.ttf                   MUI 图标字体
```

## 🖼 关于 `IMG/` 目录

- 部分文件**用图片 MD5 值命名**（如 `56eeee9b....jpg`），这是素材库的命名习惯。
- ⚠️ **版权说明**：图片素材**并非本人原创**，版权归原作者所有。
  本仓库仅作个人学习练习，**不做任何商业用途**；如涉及侵权请联系删除。
- 💡 其中有一个 **2 MB 的 GIF**，已在 `.gitignore` 中排除。

## 🔌 接口清单

| 功能 | 方法 | 路径 |
|---|---|---|
| 登录 | POST | `/api/login` |
| 社区信息（社区名称）| GET | `/api/community/community/{id}` |
| 首页轮播 | GET | `/api/rotation/list` |
| 社区通知列表 | GET | `/api/community/community_notice/list` |
| 社区活动列表 | GET | `/api/community/community-activity/activity-list` |
| 社区动态列表 | GET | `/api/community/community-activity/dynamic-list` |
| 友邻帖子列表 | GET | `/api/community/friendly_neighborhood/list` |
| 友邻帖子详情（含评论）| GET | `/api/community/friendly_neighborhood/{id}` |
| **发布评论** | POST | `/api/community/friendly_neighborhood/add/comment` |
| 公告列表 | GET | `/api/community/community_notice/list` |
| 公告详情 | GET | `/api/community/community_notice/{id}` |
| 图表·条形 | GET | `/api/data/comment/list_1` |
| 图表·折线 | GET | `/api/dataAnalysis/information/list_1` |
| 图表·饼图 | GET | `/api/dataAnalysis/activity/list_1` |

> ⚠️ 路径是**脱敏后的写法**（去掉了平台前缀）。考场以**现场发放的接口文档**为准，**照抄路径**。

**发布评论 Body**：`content`（string，必须）、`neighborhoodId`（integer，必须）
> ⚠️ `Content-Type: application/json` 时，`data` 必须用 `JSON.stringify()`，否则后端报 500。

## ⚠️ 字段名坑（已核对官方文档）

| 接口 | 字段 | 说明 |
|---|---|---|
| `community-activity/activity-list` | **`titile`** | 官方就是拼错的 `titile`，**不是 `title`** |
| `community-activity/dynamic-list` | **`titile`** | 同上 |
| `community-activity/dynamic-list` | **`number`** | 评论数（不是 `commentNum`）|
| `friendly_neighborhood/list` | `title` | ← 这个接口才是正常 `title` |
| `friendly_neighborhood/list` | `commentNum` | 评论数 ← 这个接口叫 `commentNum` |
| `community_notice/list` | `noticeStatus` | **1=已读 / 0=未读**（Query 参数也能用它筛选）|
| `community_notice/{id}` | `phone` / `createTime` | 联系电话 / 发布时间 |
| `community/community/{id}` | `name` | 社区名称 |

## 🚀 本地运行

用 **HBuilderX** 打开本文件夹，然后「运行 → 运行到手机或模拟器」。

**配置服务器地址**（编辑 `js/http.js`）：

```javascript
var http    = 'http://YOUR_SERVER_HOST:PORT';            // 调接口
var httpimg = 'http://YOUR_SERVER_HOST:PORT/prod-api';   // 显示图片
```

> ⚠️ `http` **不带** `/prod-api`；`httpimg` **带** `/prod-api` 且**末尾不要加 `/`**。
> 因为接口返回的图片字段（如 `/profile/p1.jpg`）本身以 `/` 开头，两边都带会拼成 `//`。

**接口约定**：

```json
{ "code": 200, "msg": "操作成功", "rows": [ ... ], "total": 10 }
```

需要认证的接口带：`headers: { 'Authorization': localStorage.getItem('token') }`

## 📝 待补

- [ ] `page.html` 里 `sqfw.html`（社区服务）页面还没建，点该 Tab 会报错
- [ ] `home.html` 宫格 8 个入口对应的 `li_1~li_8.html`（除 `li_6`）还没建
- [ ] 底部评论可考虑做成页面内联输入框（当前是按钮 + 原生输入弹窗）
- [ ] 打包 **release 版 APK**（赛项要求提交 `DigitalLife.apk`）

## ⚠️ 说明

- 本仓库为**个人学习练习**，非生产级代码。
- 仓库内**不含**任何赛项原始资料、接口文档或真实服务器地址。
- **图片素材版权归原作者所有**，仅作学习用途。
- MUI 版权归 [DCloud](https://www.dcloud.io/)；ECharts 版权归 Apache 基金会。

## 📄 License

代码部分：学习用途，可自由参考。
图片素材：**不适用**，版权归原作者，请勿二次分发。
