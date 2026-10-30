中职移动应用与开发 · 参赛练习项目集
中职移动应用开发成品（未必但是很快就会完整，每天更新），基于 DCloud MUI 框架开发。 A vocational mobile app development project — work in progress, updated daily. Built with the DCloud MUI framework.

很菜喵，慢慢来 OVO，有路过的大佬愿意指点指点就太感谢了 ^_^

📖 这是什么
面向 2026 山西省第二十届职业院校技能大赛（中职组）移动应用与开发赛项的参赛练习项目集。

全部基于原生 HTML5 + CSS3 + JavaScript + MUI 3.7.3 + HBuilderX， 无构建工具，用 HBuilderX 打开即可运行。

共 4 个主题项目、44 个业务页面

📂 目录结构
代码块


.
├── 时代楷模/
│   └── GongnengLianXi2/                 ⭐ 19 个页面 · 最完整
├── 数字社区（新）持续更新/                 7 个页面 · 当前主力版本
├── 智慧党建/                            8 个页面
└── mui-signup-practice(数字社区持续更新)/    10 个页面 · 旧版（已被新版替代）
🏆 项目一览
项目	主题	页面数	状态
时代楷模	楷模新闻 / 英雄 / 公益 / 心得 / 数据	19	✅ 最完整
数字社区（新）	社区 / 友邻社交 / 公告	7	✅ 当前主力
智慧党建	党员中心 / 党建动态 / 数据	8	✅ 可运行
数字社区（旧）	社区 / 友邻社交 / 公告	10	⚠️ 已被新版替代
1️⃣ 时代楷模 —— 19 个页面（最完整）
赛项经典题材，也是这个仓库里功能最全的一个。

页面	文件	功能
登录页	index.html	账号密码登录
主框架	exe/page.html	底部 Tab + subpages
首页	exe/home.html	轮播图 + 新闻列表
英雄列表	exe/li_1.html	英雄列表
身边英雄	exe/li_2.html	身边英雄列表
英雄详情	exe/YingXingListHTML.html	详情 + 评论
英雄详情（另一版）	exe/YingXungHTML.html	详情（对比版本）
数据分析	exe/li_5.html / exe/sjfx.html	echarts 三图（两版）
学习心得	exe/xd.html	心得列表
添加感言	exe/addGY.html	表单提交
添加笔记	exe/addBJ.html	表单提交
编辑笔记	exe/editBJ.html	表单提交
公益活动	exe/gy.html	公益项目列表
报名详情	exe/BaoMIngXiangQingHTML.html	报名页
公益项目详情	exe/GongYiXiangMuXiangQing.html	项目详情
用户中心	exe/YongHu.html	个人信息
更多	exe/li_3.html / li_4.html / li_6.html	各列表页
页面模板	ShengbianYinXingHTL.html	模板
亮点

✅ 轮播图首尾复制节点实现无限循环 + 圆点指示器
✅ 增删改（CRUD） 三套表单：加感言、加笔记、编笔记
✅ 报名流程：确认框 → POST → 重新请求刷新人数 → 防重复报名
✅ 返回刷新：beforeback + mui.fire(opener, 'refresh')
✅ echarts 柱 / 折 / 饼三图，饼图手动组装 {name, value}
2️⃣ 数字社区（新）—— 7 个页面（当前主力）
页面	文件	功能
登录页	index.html	手机号 / 账号登录
主框架	exe/page.html	底部 4 Tab（含切换高亮）
首页	exe/home.html	社区名称 + 轮播 + 通知滚动 + 宫格 + 活动/动态列表
友邻社交	exe/ylsj.html	帖子列表
帖子详情	exe/SeiJiaoXinagQing.html	详情 + 评论 + 发表评论
社区公告	exe/li_6.html	全部 / 未读 / 已读 三页签
公告详情	exe/QuanBuHTML.html	标题 / 时间 / 内容 / 单位 / 电话
数据分析	exe/sjfx.html	echarts 三图
亮点

✅ 社区通知滚动播放：<marquee> 拼接所有通知内容
✅ 宫格 8 个真实功能名：开门 / 我的房屋 / 我的车位 / 物业缴费 / 扫码取件 / 社区公告 / 社区电话 / 投诉建议
✅ 社区动态列表：图片在右（mui-pull-right）+ 标题 + 评论数 + 时间
✅ 公告页签真筛选：loadNotice({noticeStatus: 0/1}, 容器)
✅ 分段控件 + 接口条件查询
📌 旧版 mui-signup-practice(数字社区持续更新) 是同一个主题的早期版本（10 页）， README 里已标注「废弃版」，保留仅作对比。

3️⃣ 智慧党建 —— 8 个页面
页面	文件	功能
登录页	index.html	账号密码登录
主框架	exe/page.html	底部 5 Tab：党员学习 / 党建动态 / 首页 / 数据分析 / 党员中心
首页	exe/home.html	轮播 + 宫格（党旗 / 党章 / 党徽）+ 热点新闻（5 条 +5）
党建动态	exe/dydt.html	轮播 + 基层动态 + 组织活动 + 两个「查看更多」
活动列表	exe/GengDuoList.html	组织活动列表
活动列表（另一版）	exe/JIChengDongTa.html	基层动态列表
党员中心	exe/syzx.html	头像 / 用户名 / 学习记录 / 个人档案 / 修改密码 / 退出
修改密码	exe/GemGaiMiMai.html	旧密码 / 新密码 / 再次输入
数据分析	exe/sjfx.html	echarts 三图
亮点

✅ 三段式页面：顶部轮播 + 中间基层动态 + 下半组织活动
✅ 宫格 mui-col-xs-4 精确实现「每行 3 个」
✅ 多 Tab（5 个）+ 子页面全套
🛠 技术栈
类别	内容
基础	HTML5 / CSS3 / JavaScript（原生 ES5 为主）
UI 框架	MUI 3.7.3（DCloud）
图表	ECharts（柱状图 / 折线图 / 饼图）
网络	mui.ajax + Authorization: token
原生能力	HTML5+：plus.webview / plus.storage / plus.nativeUI
开发工具	HBuilderX
打包	HBuilderX 云打包（release APK）
🎯 已练到的知识点
 登录：判空校验、POST /login + JSON.stringify、存 token、跳主框架
 底部导航：mui.init({subpages}) + plus.webview.getWebviewById().show() （MUI 对 .mui-tab-item 自动切 mui-active 高亮，无需手写）
 轮播图：首尾复制节点无限循环、圆点指示器、自动播放
 宫格布局：mui-grid-view mui-grid-9 + mui-col-xs-4（每行 3 个）
 列表渲染：循环拼 HTML → 一次性写入 innerHTML
 列表分页：「查看更多」每次 +5 条
 跨页传参：extras + plus.storage 双保险
 返回刷新：beforeback + mui.fire(opener, 'refresh')
 增删改：表单页 + POST / PUT / DELETE
 报名功能：确认框 → POST → 重刷人数 → 防重复
 分段控件 + 条件筛选：mui-segmented-control + 接口 noticeStatus 参数
 通知滚动播放：<marquee>
 ECharts 三图：柱状图双系列、折线图、饼图（手动组装数据）
 图片地址拼接：接口相对路径 + httpimg
🚀 怎么跑起来
1. 打开项目
用 HBuilderX 打开某一个主题项目文件夹（不要打开整个仓库）：

代码块


HBuilderX → 文件 → 打开目录 → 选择 数字社区（新）持续更新/
2. 配置服务器地址
每个项目的 js/http.js 需要自己填：

javascript


var http    = 'http://YOUR_SERVER_HOST:PORT';            // 调接口（不带 /prod-api）
var httpimg = 'http://YOUR_SERVER_HOST:PORT/prod-api';   // 显示图片（带 /prod-api）
示例：

javascript


// 浏览器调试
var http    = 'http://127.0.0.1:9000';
var httpimg = 'http://127.0.0.1:9000/prod-api';

// 模拟器 / 真机（用本机局域网 IP）
var http    = 'http://192.168.1.100:9000';
var httpimg = 'http://192.168.1.100:9000/prod-api';
⚠️ 两个变量的区别很重要

http —— 只用来调接口，末尾不带 /prod-api、也不带 /
httpimg —— 只用来显示图片，末尾带 /prod-api，且不要再加 /
因为接口返回的图片字段（如 /profile/p1.jpg）本身以 / 开头， 两边都带斜杠会拼成 //profile/p1.jpg，图片就加载不出来。

3. 运行
HBuilderX →「运行」→「运行到手机或模拟器」

底部 Tab、轮播等依赖 HTML5+ 的能力需要真机或模拟器，浏览器里跑不完全。

4. 接口返回格式
json


{ "code": 200, "msg": "操作成功", "rows": [ ... ], "total": 10 }
code == 200 表示成功。需要认证的接口带：

javascript


headers: { 'Authorization': localStorage.getItem('token') }
📌 关于接口
本仓库不包含任何接口文档，也不含任何真实服务器地址。

各项目的接口路径是脱敏后的相对路径（如 /api/login、/api/activity/list）
实际练习/比赛时，路径以现场发放的接口文档为准
想跑起来需要自己准备后端服务，或对接练习用的模拟接口
📝 后续计划
 补完数字社区的 sqfw.html（社区服务）页面
 时代楷模的宫格入口补齐对应页面
 各项目打包 release 版 APK
 继续按赛题迭代（每天更新）
⚠️ 说明
本仓库为个人学习练习记录，代码以「能跑通、看得懂」为主，非生产级代码。
部分项目是同一功能的多个迭代版本，保留历史版本用于对比学习。
图片素材版权归原作者所有，仅作学习用途，不做任何商业用途。 如涉及侵权请联系删除。
仓库内不含任何赛项原始资料、官方文档或选手个人信息。
MUI 框架版权归 DCloud 所有，采用 MIT 开源协议，已保留原版权声明。
ECharts 版权归 Apache 基金会所有。
📄 License
代码部分：学习用途，可自由参考。

框架与第三方库：遵循各自开源协议（MUI - MIT，ECharts - Apache 2.0）。

图片素材：不适用，版权归原作者，请勿二次分发。

<div align="center">
每天更新中，欢迎 ⭐ star 关注进度～

</div>****
