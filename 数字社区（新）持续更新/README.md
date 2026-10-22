# 数字社区 App · dLianXi003（重写版）

> 个人练习 Demo —— 山西省第二十届职业院校技能大赛（中职组）移动应用与开发赛项，
> 模块B「移动应用前端开发」数字社区主题的练习项目，基于 DCloud MUI 框架。

很菜喵，慢慢来 OVO，有路过的大佬愿意指点指点就太感谢了 ^_^

---

## 📱 页面功能

| 页面 | 文件 | 标题 | 主要接口 |
|---|---|---|---|
| 登录页 | `index.html` | 登录 | `/api/login` |
| 主框架 | `exe/page.html` | — | 底部 4 个 Tab |
| 首页 | `exe/home.html` | 社区名称（动态） | `community/community/1`、`rotation/list`、`community_notice/list`、`community-activity/activity-list`、`community-activity/dynamic-list` |
| 友邻社交 | `exe/ylsj.html` | 友邻社交 | `friendly_neighborhood/list` |
| 帖子详情 | `exe/SeiJiaoXinagQing.html` | 帖子详情 | `friendly_neighborhood/{id}`、`friendly_neighborhood/add/comment` |

## 🎯 已实现的功能点

### 任务1 社区首页

| 要求 | 实现 |
|---|---|
| 顶部显示**所在社区名称** | ✅ `community/community/1` → `data.name` 写入 `mui-title` |
| 轮播图 | ✅ `rotation/list`，首尾复制节点实现无限循环 + 圆点指示器 |
| **社区通知滚动播放** | ✅ `<marquee scrollamount="4">` 拼接所有 `contentNotice` |
| 宫格 8 个快捷功能 | ✅ 开门 / 我的房屋 / 我的车位 / 物业缴费 / 扫码取件 / 社区公告 / 社区电话 / 投诉建议 |
| 社区活动横向列表 | ✅ `flex` + `overflow-x:auto`，含图片 + `titile` + `comDistance` |
| 社区动态列表 | ✅ **图片在右**（`mui-pull-right`）+ `titile` + `number`（评论数）+ `createTime` |
| 底部导航 4 个 | ✅ 首页 / 友邻社交 / 社区服务 / 数据分析 |

### 任务2 友邻社交

| 要求 | 实现 |
|---|---|
| 标题栏 + 帖子列表 | ✅ |
| 列表项：图片 / 点赞数 | ✅ `imgUrl` / `likeNum` |
| 点击进详情 | ✅ `extras` + `plus.storage` 双保险 |
| 详情：发布人 / 发布时间 / 发布内容 | ✅ `publishName` / `publishTime` / `publishContent` |
| 评论总数 | ✅ `list.length` |
| 评论：头像 / 昵称 / 日期 / 点赞数 / 内容 | ✅ `avater` / `userName` / `pulishTime` / `likeNum` / `content` |
| 底部发表评论 | ✅ 按钮 + `plus.nativeUI.prompt` 输入，POST 后重新加载评论 |

## 📊 接口清单

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

> ⚠️ 路径是**脱敏后的写法**（去掉了平台前缀）。考场以**现场发放的接口文档**为准，**照抄路径**。

**发布评论 Body**（官方文档）：

```
content        string   必须   评论内容
neighborhoodId integer  必须   帖子id
```

## ⚠️ 字段名坑（已核对官方文档）

| 接口 | 字段 | 说明 |
|---|---|---|
| `community-activity/activity-list` | **`titile`** | 官方就是拼错的 `titile`，**不是 `title`** |
| `community-activity/dynamic-list` | **`titile`** | 同上 |
| `community-activity/dynamic-list` | **`number`** | 评论数（不是 `commentNum`）|
| `community-activity/dynamic-list` | `comDistance` | 距离 |
| `friendly_neighborhood/list` | `title` | ← 这个接口才是正常 `title` |
| `friendly_neighborhood/list` | **`commentNum`** | 评论数 ← 这个接口叫 `commentNum` |
| `friendly_neighborhood/list` | `publishName` | 发布人 |
| `community_notice/list` | `noticeStatus` | **1=已读 / 0=未读**（integer，需转中文）|
| `community_notice/{id}` | `phone` | 联系电话 |
| `community_notice/{id}` | `createTime` | 发布时间 |
| `community/community/{id}` | `name` | 社区名称 |

> 🔴 **两个列表接口的"标题"字段名不一样** —— `community-activity/*` 是 `titile`，`friendly_neighborhood/list` 是 `title`。

## 🛠 技术栈

- **HTML5 / CSS3 / JavaScript**（原生，无构建工具）
- **MUI**（DCloud 移动端 UI 框架）
- **Ajax**：`mui.ajax` + `Authorization: token`
- **HTML5+**：`plus.webview` / `plus.storage` / `plus.nativeUI`
- 打包：Android Studio

## 📂 目录结构

```
.
├── index.html                    登录页（入口）
├── manifest.json                 HBuilderX App 配置
├── exe/
│   ├── page.html                 主框架（底部 4 Tab + subpages）
│   ├── home.html                 首页
│   ├── ylsj.html                 友邻社交列表
│   └── SeiJiaoXinagQing.html     帖子详情 + 发表评论
├── css/
│   ├── mui.css
│   └── mui.min.css
├── js/
│   ├── http.js                   服务器地址配置（需自己填，见下）
│   ├── mui.js / mui.min.js       MUI 框架
├── IMG/                          图片素材（约 8 MB，见下方说明）
└── fonts/
    └── mui.ttf                   MUI 图标字体
```

## 🖼 关于 `IMG/` 目录

- 部分文件**用图片 MD5 值命名**（如 `56eeee9b....jpg`），这是素材库的命名习惯。
- ⚠️ **版权说明**：图片素材**并非本人原创**，版权归原作者所有。
  本仓库仅作个人学习练习，**不做任何商业用途**；如涉及侵权请联系删除。
- 💡 其中有一个 **2 MB 的 GIF**，已在 `.gitignore` 中排除。

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

## 📝 待补 明天

### 🔴 高优先级（占 25 分）

- [ ] **任务3 社区公告** —— `li_6.html` 列表 + 公告详情页
  - 状态菜单栏（全部/未读/已读，`noticeStatus` 1/0 转中文）
  - 列表项：标题 / 状态 / 内容 / 发布时间 / **查看详情按钮**
  - 详情：标题 / **发布时间 `createTime`** / 内容 / 发布单位 / **联系电话 `phone`**
- [ ] **任务4 数据分析** —— `sjfx.html` 三张 echarts 图
  - 条形图 `/api/data/comment/list_1`（`name` 月份 / `woman` / `man`）
  - 折线图 `/api/dataAnalysis/information/list_1`（`name` / `value`）
  - 饼图 `/api/dataAnalysis/activity/list_1`（`name` 前五亲子活动 / `count` 报名人数）

### 🟡 中优先级

- [ ] `ylsj.html` 列表加**发布人** `publishName`（现在只有头像）
- [ ] `page.html` Tab 切换加**当前页高亮**（`mui-active`）
- [ ] 底部评论改成**页面内 `<input>` + 按钮**（现在用 `plus.nativeUI.prompt` 弹窗）
- [ ] 发评论的 `data` 加 `JSON.stringify`（`Content-Type: application/json` 时必须）

### 🟢 低优先级

- [ ] `page.html` 里 `sqfw.html`（社区服务）页面还没建，点 Tab 会报错
- [ ] `home.html` 宫格 8 个入口对应的 `li_1~li_8.html` 都还没建
- [ ] `SeiJiaoXinagQing.html` 的 `currentWebview().extra` 应为 **`extras`**
- [ ] 清理 `console.log` 残留
- [ ] 登录页按钮文字「按钮」→「登录」
- [ ] 打包 release 版 APK

## ⚠️ 说明

- 本仓库为**个人学习练习**，非生产级代码。
- 仓库内**不含**任何赛项原始资料、接口文档或真实服务器地址。
- **图片素材版权归原作者所有**，仅作学习用途。
- MUI 版权归 [DCloud](https://www.dcloud.io/)；ECharts 版权归 Apache 基金会。

## 📄 License

代码部分：学习用途，可自由参考。
图片素材：**不适用**，版权归原作者，请勿二次分发。
