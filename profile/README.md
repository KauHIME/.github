<div align="center">

# 火羽 · 直播档案

直播间 [live.bilibili.com/22748536](https://live.bilibili.com/22748536) · 主页 [space.bilibili.com/2094031249](https://space.bilibili.com/2094031249)

</div>

这里放的是直播围着转的几个项目：把直播当时的中日翻译存成可检索的逐字稿，再把同一份数据
做成录播字幕插件——录播没有字幕，插件补上。

## 有什么

| 仓库 | 内容 |
| --- | --- |
| [live-archive](https://github.com/hibane-hinome/live-archive) | 逐字稿存档站 + 录播字幕插件。**18 场、10 962 条**中日对照，按场次浏览、全库检索 |
| [LiveTranslate](https://github.com/hibane-hinome/LiveTranslate) | 实时翻译工具（fork）。系统音频 → 日语 ASR → 大模型翻译，本仓库加了逐句时间戳落库 |
| [LiveCaptions-Translator](https://github.com/hibane-hinome/LiveCaptions-Translator) | 基于 Windows LiveCaptions 的轻量实时翻译（fork） |

## 存档站

<https://hibane-hinome.github.io/live-archive/>

每场直播一份：话题带、目录、逐条日文原文 + 中文译文，可以全库搜索。数据由 LiveTranslate
（翻译）和 danmaku-it（弹幕 / SC）两个采集端写进同一个 SQLite，数据库本身不入库，只发布整理后的结果。

## 录播字幕插件

把直播当时的逐句翻译叠在录播画面上：日文原文在上（小）、中文译文在下（大），随播放进度走，
点开右下角「译」按钮调字号、高度、对时。数据每天从 Pages 取最新，取不到会依次换 jsDelivr 和
GitHub raw。

- 下载 zip：<https://hibane-hinome.github.io/live-archive/download/hibane-subs-latest.zip>
- 安装与用法：[工具页](https://hibane-hinome.github.io/live-archive/#/tools)

Chrome / Edge 开发者模式加载解压后的文件夹即可。场次按稿件自动匹配（手动选择 → 映射表 → 简介
标记 → 发布时间倒推），对时偏移按稿件记住。时间轴由入库时间与句长反推，误差约 0.7 秒。
