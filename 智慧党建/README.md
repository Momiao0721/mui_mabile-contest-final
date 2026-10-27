# 智慧党建 App（DangJianDongTai）

> 中职移动应用与开发赛项备赛练习项目，基于 DCloud MUI 框架。
> 主题为**智慧党建**：党员中心、首页、党建动态、数据分析。

很菜喵，慢慢来 OVO，有路过的大佬愿意指点指点就太感谢了 ^_^

---

## 📱 页面功能

| 页面 | 文件 | 标题 | 主要接口 |
|---|---|---|---|
| 登录页 | `index.html` | — | `/api/login` |
| 主框架 | `exe/page.html` | — | 底部 5 个 Tab |
| 首页 | `exe/home.html` | — | `building/banner/list`、`model/list` |
| 党建动态 | `exe/dydt.html` | — | `building/banner/list`、`hero/list`、`activity/list` |
| 数据分析 | `exe/sjfx.html` | 数据分析 | 三张图表接口 |
| 党员中心 | `exe/syzx.html` | 党员中心 | `common/user/getInfo`、`logout` |
| 修改密码 | `exe/GemGaiMiMai.html` | 修改密码 | `/api/login`（见下方说明）|
| 活动列表（组织活动）| `exe/GengDuoList.html` | 活动列表 | `activity/list` |
| 活动列表（基层动态）| `exe/JIChengDongTa.html` | 活动列表 | `activity/list` |

## 🎯 功能实现情况

### 底部导航（`exe/page.html`）

5 个 Tab：**党员学习 / 党建动态 / 首页 / 数据分析 / 党员中心**

用 `mui.init({subpages:[...]})` + `plus.webview.getWebviewById(id).show()` 切换。

### 首页（`exe/home.html`）

| 要求 | 实现 |
|---|---|
| 顶部轮播图 | ✅ `building/banner/list`，首尾复制节点实现无限循环 + 圆点指示器 |
| 快捷功能宫格 3 个 | ✅ **党旗 / 党章 / 党徽**，`mui-col-xs-4`（每行 3 个）|
| 热点新闻列表 | ✅ `model/list`，默认 5 条，点「更新」按钮 +5 |
| 新闻字段 | `title`（标题）/ `name` / `content` |
| 底部 5 个导航 | ✅ 见上 |

### 党建动态（`exe/dydt.html`）

| 区域 | 实现 |
|---|---|
| 顶部轮播图 | ✅ `building/banner/list` |
| 中间基层动态 | ✅ `hero/list`，带「查看更多」|
| 下半组织活动 | ✅ `activity/list`，最多 3 条，带「查看更多」|
| 查看更多 → 列表页 | ✅ `JIChengDongTa.html` / `GengDuoList.html` |

### 数据分析（`exe/sjfx.html`）

| 图表 | 接口 | 说明 |
|---|---|---|
| **条形图** | `/api/data/comment/list_2` | `name`（月份）/ `woman` / `man` 双系列 |
| **折线图** | `/api/read/book/list_1` | `name`（月份）/ `value` |
| **饼状图** | `/api/read/book/list/type_1` | `name` / `count` → 组装成 `{name, value}` |

饼图 label：`formatter: '{b},{d}%'`（名称 + 比例）

### 党员中心（`exe/syzx.html`）

| 要求 | 实现 |
|---|---|
| 用户头像 | ✅ `avatar` |
| 用户名 | ✅ `userName` |
| 学习记录入口 | ✅ |
| 个人档案入口 | ✅ |
| 修改密码入口 | ✅ → `GemGaiMiMai.html` |
| 点击退出可退出登录 | ✅ `logout` 接口 |

### 修改密码（`exe/GemGaiMiMai.html`）

标签栏标题 ✅、返回图标 ✅、旧密码 / 新密码 / 再次输入 ✅、确定按钮 ✅

> ⚠️ 提交时调的是 `/api/login`（登录接口），因为现有接口平台没有专门的改密码接口。

## 🎯 练到的知识点

| 技能 | 位置 |
|---|---|
| 登录 + token | `index.html` |
| 底部 5 Tab + subpages | `page.html` |
| 轮播图首尾复制循环 | `home.html` / `dydt.html` |
| 宫格（每行 3 个）| `home.html`（`mui-col-xs-4`）|
| 列表「查看更多」+5 条 | `home.html` |
| 多段页面（轮播 + 两个列表区）| `dydt.html` |
| 事件委托 + IIFE 闭包 | `dydt.html` |
| echarts 柱 / 折 / 饼 | `sjfx.html` |
| 手动组装图表数据 | `sjfx.html` 饼图 |
| 退出登录 | `syzx.html` |

## 🛠 技术栈

- **HTML5 / CSS3 / JavaScript**（原生，无构建工具）
- **MUI**（DCloud 移动端 UI 框架）
- **ECharts**（`js/echarts.js`）
- **Ajax**：`mui.ajax` + `Authorization: token`
- **HTML5+**：`plus.webview` / `plus.storage` / `plus.nativeUI`
- 打包：HBuilderX（已产出过 release APK）

## 📂 目录结构

```
.
├── index.html                    登录页（入口）
├── manifest.json                 HBuilderX App 配置
├── exe/                          业务页面（8 个）
│   ├── page.html                 主框架（底部 5 Tab + subpages）
│   ├── home.html                 首页
│   ├── dydt.html                 党建动态
│   ├── sjfx.html                 数据分析（三图）
│   ├── syzx.html                 党员中心
│   ├── GemGaiMiMai.html          修改密码
│   ├── GengDuoList.html          活动列表
│   └── JIChengDongTa.html        活动列表
├── css/
│   ├── mui.css
│   └── mui.min.css
├── js/
│   ├── http.js                   服务器地址配置（需自己填，见下）
│   ├── mui.js / mui.min.js       MUI 框架
│   ├── echarts.js                图表库
│   └── BigitalLife/index.html    早期遗留的登录页副本
├── IMG/                          图片素材（15 个，约 7 MB）
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
| 首页轮播 | GET | `/api/building/banner/list` |
| 热点新闻列表 | GET | `/api/model/list` |
| 基层动态 | GET | `/api/hero/list` |
| 组织活动 | GET | `/api/activity/list` |
| 活动列表 | GET | `/api/activity/list` |
| 用户信息 | GET | `/api/common/user/getInfo` |
| 退出登录 | POST | `/api/logout` |
| 图表·条形 | GET | `/api/data/comment/list_2` |
| 图表·折线 | GET | `/api/read/book/list_1` |
| 图表·饼图 | GET | `/api/read/book/list/type_1` |

> ⚠️ 路径是**脱敏后的写法**（去掉了平台前缀）。考场以**现场发放的接口文档**为准，**照抄路径**。

**字段名注意**

| 接口 | 字段 | 说明 |
|---|---|---|
| `model/list` | `title` / `name` / `content` | 新闻标题 / 作者 / 内容 |
| `common/user/getInfo` | `avatar` / `userName` | 头像 / 用户名 |
| `data/comment/list_2` | `name` / `woman` / `man` | 月份 / 女性 / 男性评论数 |
| `read/book/list_1` | `name` / `value` | 月份 / 每月阅读数量 |
| `read/book/list/type_1` | `name` / `count` | 书籍类型 / 数量 |

## 🚀 本地运行

用 **HBuilderX** 打开本文件夹，然后「运行 → 运行到手机或模拟器」。

**配置服务器地址**（编辑 `js/http.js`）：

```javascript
var http    = 'http://YOUR_SERVER_HOST:PORT';            // 调接口
var httpimg = 'http://YOUR_SERVER_HOST:PORT/prod-api';   // 显示图片
```

> ⚠️ 两个变量区别：
> - `http` —— 只用来**调接口**，末尾**不带** `/prod-api`、**也不带** `/`
> - `httpimg` —— 只用来**显示图片**，末尾**带** `/prod-api` 且**不要再加 `/`**
>
> 因为接口返回的图片字段（如 `/profile/p1.jpg`）本身以 `/` 开头，
> 两边都带斜杠会拼成 `//profile/p1.jpg`，图片就加载不出来。

**接口约定**：

```json
{ "code": 200, "msg": "操作成功", "rows": [ ... ], "total": 10 }
```

需要认证的接口带：`headers: { 'Authorization': localStorage.getItem('token') }`

## 📝 待优化

### 🔴 结构问题

- [ ] **`exe/dyxx.html`（党员学习）不存在** —— `page.html` 的 `subpages` 声明了它，
      点「党员学习」Tab 时 `getWebviewById('dyxx')` 返回 `null`，`.show()` 会报错。
      建议建这个页面，或先删掉该 Tab
- [ ] `GengDuoList.html` 和 `JIChengDongTa.html` **内容完全相同**（MD5 一致），
      建议分别改成「组织活动列表」和「基层动态新闻列表」
- [ ] `js/BigitalLife/index.html` 是早期遗留的重复登录页，可删

### 🟡 功能细节

- [ ] **底部 Tab 切换没有颜色标记**（题目要求「颜色标记当前页面所在导航栏」）
      —— `YeiMian()` 里只 `show()`，没有切 `mui-active`
- [ ] `GemGaiMiMai.html` 里**有两个 `id="username"`**（重复 id），且调的是登录接口
- [ ] 党员中心「学习记录」「个人档案」只有文字，没绑点击事件（题目只要求"入口"，可不改）
- [ ] 各页面 `<title>` 为空，建议补上

### 🟢 交付

- [ ] 打包 release 版 APK（`DigitalLife.apk`）

## ⚠️ 说明

- 本仓库为**个人学习练习**，非生产级代码。
- 仓库内**不含**任何赛项原始资料、接口文档或真实服务器地址。
- **图片素材版权归原作者所有**，仅作学习用途。
- MUI 版权归 [DCloud](https://www.dcloud.io/)；ECharts 版权归 Apache 基金会。

## 📄 License

代码部分：学习用途，可自由参考。
图片素材：**不适用**，版权归原作者，请勿二次分发。
