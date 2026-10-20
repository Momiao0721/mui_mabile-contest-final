# MUI 移动端练习项目 · 数字社区（LianXiGongNeng003）

> 个人练习 Demo —— 中职移动应用与开发赛项备赛练习，基于 DCloud MUI 框架。
> 主题是**数字社区**：社区首页、友邻社交、社区公告、社区服务、数据分析。

很菜喵，慢慢来 OVO，有路过的大佬愿意指点指点就太感谢了 ^_^

---

## 📱 页面功能

| 页面 | 文件 | 标题 | 主要接口 |
|---|---|---|---|
| 登录页 | `index.html` | 数字社区 | `/api/login` |
| 主框架 | `exe/page.html` | — | 底部 5 个 Tab |
| 首页 | `exe/home.html` | — | `rotation/list`（轮播）、`community/community/1` |
| 友邻社交 · 列表 | `exe/ylsj.html` | — | `community/friendly_neighborhood/list` |
| 友邻社交 · 详情 | `exe/XiangQingHTML.html` | 详情 | `community/friendly_neighborhood/{id}` |
| 友邻列表（另一版） | `exe/DOmeKong.html` | 标题 | `community/friendly_neighborhood/list` |
| 社区公告 | `exe/li_6.html` | 社区公告 | `community/community_notice/list` |
| **数据分析** | `exe/sjfx.html` | 数据分析 | **3 个图表接口** |
| 数据分析（空壳） | `exe/ajfx.html` | 数据分析 | — （709 B，只有标题栏 + 引了 echarts）|

## 📊 数据分析（`exe/sjfx.html`）

| 图表 | 接口 |
|---|---|
| 条形图（评论数·按性别） | `/api/data/comment/list_1` |
| 信息统计 | `/api/dataAnalysis/information/list_1` |
| 活动统计 | `/api/dataAnalysis/activity/list_1` |

> ⚠️ 注意：这个主题的图表接口用的是 `_1` 后缀
> （`data/comment/list_1`），和「时代楷模」主题的 `list_2` **不一样**。
> **考场照抄文档，别凭记忆写。**

## 🎯 这个练习练到了什么

| 技能 | 体现在哪 |
|---|---|
| **登录** | `index.html` —— 账号密码、判空、存 token |
| **底部 5 Tab + subpages** | `page.html` —— 含中间一个「+」大图标 Tab |
| **轮播图** | `home.html` —— `rotation/list` |
| **列表渲染** | 友邻列表、社区公告 |
| **详情页 + 传参** | `ylsj.html` → `XiangQingHTML.html` |
| **echarts 图表** | `sjfx.html` —— 3 个接口 |
| **Ajax + token** | 所有请求走 `mui.ajax`，请求头带 `Authorization` |
| **图片地址拼接** | 接口返回相对路径，用 `httpimg` 拼服务器地址 |

## 🛠 技术栈

- **HTML5 / CSS3 / JavaScript**（原生，无构建工具）
- **MUI**（DCloud 移动端 UI 框架）
- **ECharts**（数据可视化，`js/echarts.js`）
- **Ajax**：`mui.ajax` 调 RESTful 接口
- 打包：HBuilderX

## 📂 目录结构

```
.
├── index.html                    登录页（入口）
├── manifest.json                 HBuilderX App 配置
├── exe/
│   ├── page.html                 主框架（底部 5 Tab）
│   ├── home.html                 首页（轮播 + 社区信息）
│   ├── ylsj.html                 友邻社交列表
│   ├── XiangQingHTML.html        友邻详情
│   ├── DOmeKong.html             友邻列表（另一版）
│   ├── li_6.html                 社区公告
│   ├── sjfx.html                 数据分析（echarts）
│   └── ajfx.html                 数据分析（空壳）
├── css/
│   ├── mui.css
│   └── mui.min.css
├── js/
│   ├── http.js                   服务器地址配置（需自己填，见下）
│   ├── mui.js / mui.min.js       MUI 框架
│   └── echarts.js                图表库
├── IMG/                          图片素材（约 8 MB，见下方说明）
└── fonts/
    └── mui.ttf                   MUI 图标字体
```

## 🖼 关于 `IMG/` 目录

共 15 个文件、约 **8 MB**，是从**备赛素材库**复制的练习用图片。

- 部分文件**用图片的 MD5 值命名**（例如 `56eeee9b7cf007f3df2b4ac6027371df.jpg`），
  这是素材库的命名习惯，同一张图不会重名。
- ⚠️ **版权说明**：图片素材**并非本人原创**，版权归原作者所有。
  本仓库仅作个人学习练习，**不做任何商业用途**；如涉及侵权请联系删除。
- 💡 其中有一个 **2 MB 的 GIF**，若想让仓库小一点可以压缩或在 `.gitignore` 里排除。

## 🔌 用到的接口

| 功能 | 方法 | 路径 |
|---|---|---|
| 登录 | POST | `/api/login` |
| 首页轮播 | GET | `/api/rotation/list` |
| 社区信息 | GET | `/api/community/community/{id}` |
| 友邻列表 | GET | `/api/community/friendly_neighborhood/list` |
| 友邻详情 | GET | `/api/community/friendly_neighborhood/{id}` |
| 社区公告列表 | GET | `/api/community/community_notice/list` |
| 图表·评论数 | GET | `/api/data/comment/list_1` |
| 图表·信息统计 | GET | `/api/dataAnalysis/information/list_1` |
| 图表·活动统计 | GET | `/api/dataAnalysis/activity/list_1` |

> ⚠️ 路径是**脱敏后的写法**（去掉了平台前缀）。考场以**现场发放的接口文档**为准，**照抄路径**。

## 🚀 本地运行

### 1. 打开项目

用 **HBuilderX** 打开本文件夹（不要打开里面的单个文件），
然后「运行 → 运行到手机或模拟器」。

### 2. 配置服务器地址

本项目**不包含任何真实服务器地址**（已脱敏）。运行前编辑 `js/http.js`：

```javascript
var http    = 'http://YOUR_SERVER_HOST:PORT';            // 调接口
var httpimg = 'http://YOUR_SERVER_HOST:PORT/prod-api';   // 显示图片
```

替换成你自己的接口地址，例如：

```javascript
// 浏览器调试
var http    = 'http://127.0.0.1:9000';
var httpimg = 'http://127.0.0.1:9000/prod-api';

// 模拟器 / 真机（用本机局域网 IP）
var http    = 'http://192.168.1.100:9000';
var httpimg = 'http://192.168.1.100:9000/prod-api';
```

> ⚠️ **两个变量的区别很重要**：
> - `http` —— 只用来**调接口**，末尾**不带** `/prod-api`
> - `httpimg` —— 只用来**显示图片**，末尾**带** `/prod-api`，且**末尾不要加 `/`**
>
> 因为接口返回的图片字段（如 `/profile/p1.jpg`）本身就以 `/` 开头，
> 两边都带斜杠会拼成 `//profile/p1.jpg`，图片会加载失败。

### 3. 接口约定

返回结构一般为：

```json
{ "code": 200, "msg": "操作成功", "rows": [ ... ], "total": 10 }
```

`code` 为 200 表示成功。需要认证的接口在请求头带：

```javascript
headers: { 'Authorization': localStorage.getItem('token') }
```

## 🐛 已知问题（记录，未修改）

### ❌ 1. `page.html` 声明了 2 个不存在的页面

```javascript
url:'sjfx.html',   // ✅ 存在
url:'sqfw.html',   // ❌ 缺失（社区服务）
url:'Jia.html',    // ❌ 缺失（中间那个「+」Tab）
url:'ylsj.html',   // ✅ 存在
url:'home.html',   // ✅ 存在
```

**后果**：点「社区服务」和中间「+」两个 Tab **会报错**。

**修法**：建这两个页面，或把 Tab 删掉。

### ⚠️ 2. 两个数据分析页重复

`exe/sjfx.html`（5040 B，有内容）和 `exe/ajfx.html`（709 B，空壳）标题都叫「数据分析」。

**建议**：保留 `sjfx.html`，删掉 `ajfx.html`。

### ⚠️ 3. 两个友邻列表页重复

`exe/ylsj.html`（2560 B）和 `exe/DOmeKong.html`（2870 B）都调
`community/friendly_neighborhood/list`。

**建议**：比较后保留一个。

## 📝 待办

- [ ] 建 `sqfw.html`（社区服务）+ `Jia.html`（+ Tab），或删掉这两个 Tab
- [ ] 清理重复页面（`ajfx.html` / `DOmeKong.html`）
- [ ] 打包练习：产出 release 版 APK

## ⚠️ 说明

- 本仓库为**个人学习练习**，代码以「能跑通、看得懂」为主，非生产级代码。
- 仓库内**不含**任何赛项原始资料、接口文档或真实服务器地址。
- **图片素材版权归原作者所有**，仅作学习用途。
- MUI 框架版权归 [DCloud](https://www.dcloud.io/) 所有；
  ECharts 版权归 Apache 基金会所有，均仅作学习使用。

## 📄 License

代码部分：学习用途，可自由参考。
图片素材：**不适用**，版权归原作者，请勿二次分发。
