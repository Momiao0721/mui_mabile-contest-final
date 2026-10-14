# MUI 移动端练习项目 · 时代楷模完整版0.2

> 个人练习 Demo —— 中职移动应用与开发赛项备赛练习，基于 DCloud MUI 框架。
> 这一版：登录、首页、英雄列表、身边英雄、学习感言、数据分析（echarts）

很菜喵，慢慢来 OVO，有路过的大佬愿意指点指点就太感谢了 ^_^

---

## 📱 页面功能

| 页面 | 文件 | 标题 | 接口 | 说明 |
|---|---|---|---|---|
| 登录页 | `index.html` | 手机号登录 | `/api/phone/login` | 手机号 + 密码登录，存 token 跳主框架 |
| 主框架 | `exe/page.html` | — | — | 底部 Tab 切换 |
| 首页 | `exe/home.html` | — | `building/banner/list`<br>`model/list` | 轮播图 + 新闻列表 |
| 英雄列表 | `exe/li_1.html` | 英雄列表 | `hero/list` | 列表渲染 |
| 身边英雄 | `exe/li_2.html` | 身边英雄 | `around/list` | 列表渲染 |
| 英雄详情 | `exe/YingXingListHTML.html` | 标题 | `hero/{id}`<br>`hero/evaluate/list` | 详情 + 评论列表 |
| 英雄详情（另一版） | `exe/YingXungHTML.html` | 英雄LIst详情页 | — | 页面已写，接口待接 |
| 学习感言 | `exe/xd.html` | 学习感言 | `testimonials/list` | 感言列表 |
| **数据分析** | `exe/sjfx.html` | 数据分析 | `data/comment/list_2`<br>`read/book/list_1` | **echarts 图表** |
| 公益活动 | `exe/gy.html` | 公益活动 | — | 较简略（919 B）|
| 页面模板 | `ShengbianYinXingHTL.html` | — | — | 375 B 模板 |
| li_3 ~ li_6 | `exe/li_3 ~ li_6.html` | — | — | **空壳** |

## 📊 数据分析页（`exe/sjfx.html`）现状

| 图表 | 接口 | 状态 |
|---|---|---|
| 条形图（评论数·按性别） | `/api/data/comment/list_2` | ✅ 已调 |
| 折线图（阅读书籍数趋势） | `/api/read/book/list_1` | ✅ 已调 |
| **饼状图（书籍类型占比）** | `/api/read/book/list/type_1` | ⚠️ **还没调** |

> 📌 赛题要求**三张图**（条形 / 折线 / 饼状），饼图接口是
> `/api/read/book/list/type_1`，返回 `data.name[]` / `data.count[]` / `data.data[]`。
> 图表库 `js/echarts.js` 已经在项目里了。

## 🎯 这个练习练到了什么

| 技能 | 体现在哪 |
|---|---|
| **手机号登录** | `index.html` —— 传 `phone` + `password` |
| **轮播图无限循环** | `home.html` —— 首尾复制节点 + 圆点指示器 |
| **多种列表渲染** | 英雄列表 / 身边英雄 / 学习感言 |
| **详情页 + 评论列表** | `YingXingListHTML.html` —— 两个接口配合 |
| **echarts 图表** | `sjfx.html` —— 柱状图 / 折线图 |
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
├── ShengbianYinXingHTL.html      页面模板
├── exe/                          业务页面
│   ├── page.html                 主框架
│   ├── home.html                 首页（轮播 + 新闻）
│   ├── li_1.html                 英雄列表
│   ├── li_2.html                 身边英雄
│   ├── YingXingListHTML.html     英雄详情 + 评论
│   ├── YingXungHTML.html         英雄详情（另一版）
│   ├── xd.html                   学习感言
│   ├── sjfx.html                 数据分析（echarts）
│   ├── gy.html                   公益活动
│   └── li_3 ~ li_6.html          空壳
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

共 17 个文件、约 **8 MB**，是从**备赛素材库**复制的练习用图片。

- 部分文件**用图片的 MD5 值命名**（例如 `56eeee9b7cf007f3df2b4ac6027371df.jpg`）。
- ⚠️ **版权说明**：图片素材**并非本人原创**，版权归原作者所有。
  本仓库仅作个人学习练习，**不做任何商业用途**；如涉及侵权请联系删除。
- 💡 其中有一个 **2 MB 的 GIF**，若想让仓库小一点可以压缩或排除。

## 🔌 用到的接口

| 功能 | 方法 | 路径 |
|---|---|---|
| 手机号登录 | POST | `/api/phone/login` |
| 首页轮播 | GET | `/api/building/banner/list` |
| 首页新闻 | GET | `/api/model/list` |
| 英雄列表 | GET | `/api/hero/list` |
| 英雄详情 | GET | `/api/hero/{id}` |
| 英雄评论列表 | GET | `/api/hero/evaluate/list?heroId=` |
| 身边英雄 | GET | `/api/around/list` |
| 学习感言列表 | GET | `/api/testimonials/list` |
| 图表·条形（评论数） | GET | `/api/data/comment/list_2` |
| 图表·折线（阅读量） | GET | `/api/read/book/list_1` |
| 图表·饼图（书籍类型） | GET | `/api/read/book/list/type_1` |

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
> - `httpimg` —— 只用来**显示图片**，末尾**带** `/prod-api`
>
> 写错的话接口会 404 或图片全部裂开。

### 3. 接口约定

返回结构一般为：

```json
{ "code": 200, "msg": "操作成功", "rows": [ ... ], "total": 10 }
```

`code` 为 200 表示成功。需要认证的接口在请求头带：

```javascript
headers: { 'Authorization': localStorage.getItem('token') }
```

## 📝 待办

- [ ] `exe/sjfx.html` —— 补上**饼状图**（`/api/read/book/list/type_1`）
- [ ] `exe/YingXungHTML.html` —— 确认是否要和 `YingXingListHTML.html` 合并（两版详情页重复）
- [ ] `exe/li_3 ~ li_6.html` —— 空壳页面内容
- [ ] `exe/gy.html` —— 公益活动页只有 919 B，内容待补
- [ ] 打包练习：产出 release 版 APK

## ⚠️ 说明

- 本仓库为**个人学习练习**，代码以「能跑通、看得懂」为主，非生产级代码。
- 仓库内**不含**任何赛项原始资料、接口文档或真实服务器地址。
- **图片素材版权归原作者所有**，仅作学习用途。
- MUI 框架版权归 [DCloud](https://www.dcloud.io/) 所有；ECharts 版权归 Apache 基金会，均仅作学习使用。

## 📄 License

代码部分：学习用途，可自由参考。
图片素材：**不适用**，版权归原作者，请勿二次分发。
