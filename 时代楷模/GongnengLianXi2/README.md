# MUI 移动端练习项目 · GongnengLianXi2（功能练习 2）

> 个人练习 Demo —— 中职移动应用与开发赛项备赛练习，基于 DCloud MUI 框架。
> 主要练**手机号登录**、**首页轮播 + 新闻列表**、**英雄列表**这类常见题型。

很菜喵，慢慢来 OVO，有路过的大佬愿意指点指点就太感谢了 ^_^

---

## 📱 页面功能

| 页面 | 文件 | 状态 | 说明 |
|---|---|:---:|---|
| 登录页 | `index.html` | ✅ | **手机号 + 密码**登录（调用手机号登录接口）、判空、存 token、跳主框架 |
| 主框架 | `exe/page.html` | ✅ | 底部 Tab 切换 |
| 首页 | `exe/home.html` | ✅ | **轮播图**（首尾复制节点实现无限循环 + 圆点指示器）、**楷模新闻列表** |
| 英雄列表 | `exe/li_1.html` | ✅ | 调用英雄列表接口，左图右文的列表渲染 |
| 英雄详情 | `exe/YingXingListHTML.html` | 🟡 | 页面模板已建，跳转与内容待补 |
| li_2 ~ li_6 | `exe/li_2 ~ li_6.html` | ⬜ | 空壳（只有标题栏）|

> 📌 空壳页面都是「标题栏 + 返回按钮 + `mui.init()`」的模板，方便后续直接往里写功能。

## 🎯 这个练习练到了什么

| 技能 | 体现在哪 |
|---|---|
| **手机号登录** | `index.html` —— 传 `phone` + `password`（和账号密码登录是两个不同接口）|
| **轮播图无限循环** | `home.html` —— 首尾各复制一张（首 = 最后一张，尾 = 第一张），中间 `for` 循环渲染 |
| **圆点指示器** | 循环图片时同步生成 `<div class="mui-indicator">` |
| **列表渲染** | 循环拼 HTML → 一次性写入 `innerHTML`（列表项含缩略图 + 标题 + 内容）|
| **图片地址拼接** | 接口返回相对路径，用 `httpimg` 拼服务器地址 |
| **Ajax + token** | 所有请求走 `mui.ajax`，请求头带 `Authorization` |

## 🛠 技术栈

- **HTML5 / CSS3 / JavaScript**（原生，无构建工具）
- **MUI**（DCloud 移动端 UI 框架）
- **Ajax**：`mui.ajax` 调 RESTful 接口
- 打包：HBuilderX

## 📂 目录结构

```
.
├── index.html                登录页（入口）
├── manifest.json             HBuilderX App 配置
├── exe/
│   ├── page.html             主框架（底部 Tab）
│   ├── home.html             首页（轮播 + 新闻列表）
│   ├── li_1.html             英雄列表
│   ├── YingXingListHTML.html 英雄详情（模板）
│   └── li_2 ~ li_6.html      空壳页面
├── css/
│   ├── mui.css
│   └── mui.min.css
├── js/
│   ├── http.js               服务器地址配置（需自己填，见下）
│   ├── mui.js
│   └── mui.min.js
├── fonts/
│   └── mui.ttf               MUI 图标字体
└── IMG/                      图片素材（见下方说明）
```

## 🖼 关于 `IMG/` 目录

```
IMG/    17 个文件，合计约 8.1 MB
```

**说明：**

- 这里放的是练习用的**图片素材**，大部分是从**素材库(浏览器)**复制过来的。
- 其中有几张**文件名就是图片的 MD5 值**（例如 `56eeee9b7cf007f3df2b4ac6027371df.jpg`）——
  素材库习惯用 MD5 命名，好处是同一张图不会重名。
- ⚠️ **`隰县职业中学logo.png` / `隰县职业中学logo120.120.jpg`** 是**学校标识**。
  **上传到公开仓库前建议删掉或重命名**，避免暴露个人信息。
- ⚠️ **版权说明**：图片素材**并非本人原创**，版权归原作者所有。
  本仓库仅作个人学习练习，**不做任何商业用途**；如涉及侵权请联系删除。
- 💡 素材体积偏大（其中有一个 2 MB 的 GIF）。如果想让仓库小一点，
  可以先压缩再上传，或者用 `.gitignore` 排除大文件。

## 🔌 用到的接口

| 页面 | 方法 | 路径 | 说明 |
|---|---|---|---|
| 登录 | POST | `/api/phone/login` | 传 `phone` / `password`，返回 token |
| 首页轮播 | GET | `/api/building/banner/list` | 返回 `rows` 数组 |
| 首页新闻 | GET | `/api/model/list` | 楷模新闻列表 |
| 英雄列表 | GET | `/api/hero/list` | 英雄故事列表 |

> ⚠️ 路径是**脱敏后的写法**（去掉了平台前缀）。考场以**现场发放的接口文档**为准，**照抄路径**。

## 🚀 本地运行

### 1. 打开项目

用 **HBuilderX** 打开本文件夹（不要打开里面的单个文件），
然后「运行 → 运行到手机或模拟器」。

也可以直接用浏览器打开 `index.html`，但底部 Tab 等原生能力需要真机/模拟器。

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

- [ ] `exe/li_2 ~ li_6.html` —— 各列表/详情页内容
- [ ] `exe/YingXingListHTML.html` —— 英雄详情跳转与内容
- [ ] 首页「查看更多」分页（如果需要）
- [ ] 打包练习：产出 release 版 APK

## ⚠️ 说明

- 本仓库为**个人学习练习**，代码以「能跑通、看得懂」为主，非生产级代码。
- 仓库内**不含**任何赛项原始资料、接口文档或真实服务器地址。
- **图片素材版权归原作者所有**，仅作学习用途，详见上方「关于 IMG 目录」。
- MUI 框架版权归 [DCloud](https://www.dcloud.io/) 所有，此处仅作学习使用。

## 📄 License

代码部分：学习用途，可自由参考。
图片素材：**不适用**，版权归原作者，请勿二次分发。
