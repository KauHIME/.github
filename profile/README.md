<div align="center">

# 火羽 · 直播档案

直播间 [live.bilibili.com/22748536](https://live.bilibili.com/22748536) · 主页 [space.bilibili.com/2094031249](https://space.bilibili.com/2094031249)

</div>

围着直播转的几个项目：把当时的中日翻译存成可检索的逐字稿，给没有字幕的录播补上字幕，
再把同一套识别与翻译流程搬到手机上——电脑在听，手机也能听。

## 仓库

| 仓库 | 内容 |
| --- | --- |
| [live-archive](https://github.com/hibane-hinome/live-archive) | 逐字稿存档站 + 录播字幕插件。**25 场、17 296 条**中日对照，按场次浏览、全库检索 |
| [LiveTranslate](https://github.com/hibane-hinome/LiveTranslate) | Windows 实时翻译（fork）。系统音频 → VAD → ASR → 大模型流式翻译 → 置顶悬浮窗；本仓库增加了逐句时间戳落库、手机远程接入与 ReazonSpeech 引擎 |
| [LiveTranslateClient](https://github.com/hibane-hinome/LiveTranslateClient) | Android 客户端。抓取其他应用播放的音频推到电脑，复用电脑的 ASR 与翻译，悬浮窗同步显示原文和译文 |
| [danmaku-it](https://github.com/hibane-hinome/danmaku-it) | 弹幕与 SC 采集，和翻译记录写进同一个 SQLite |
| [LiveCaptions-Translator](https://github.com/hibane-hinome/LiveCaptions-Translator) | 基于 Windows LiveCaptions 的轻量实时翻译（fork） |

## 实时翻译

电脑端用 WASAPI loopback 抓系统声音（可选混入麦克风），32 ms 分块过 Silero VAD，
本地跑 ASR（SenseVoice / faster-whisper / Anime-Whisper / ReazonSpeech），再交给任意
OpenAI 兼容接口逐字流式翻译，结果显示在透明置顶悬浮窗里。

手机端（Android 10+）通过 MediaProjection 的音频回放捕获，选择一个应用共享它的声音，
16 kHz 单声道 PCM 经 WebSocket 推到电脑，复用电脑的模型与翻译，结果同时回到手机悬浮窗，
样式与电脑端一致。同一时间只接受一台手机；局域网点「连接」即可，访问令牌可留空。

## 存档站

<https://hibane-hinome.github.io/live-archive/>

每场一份：话题带、目录、逐条日文原文 + 中文译文，支持全库搜索。数据由 LiveTranslate
（翻译）和 danmaku-it（弹幕 / SC）写进同一个 SQLite，数据库本身不入库，只发布整理后的结果。

## 录播字幕插件

把直播当时的逐句翻译叠在录播画面上：日文原文在上（小）、中文译文在下（大），随播放进度走，
右下角「译」按钮可调字号、高度、对时。数据每天从 Pages 取最新，失败时依次换 jsDelivr 和
GitHub raw。

- 下载 zip：<https://hibane-hinome.github.io/live-archive/download/hibane-subs-latest.zip>
- 安装与用法：[工具页](https://hibane-hinome.github.io/live-archive/#/tools)

场次按稿件自动匹配（手动选择 → 映射表 → 简介标记 → 发布时间倒推），对时偏移按稿件记住。
时间轴由入库时间与句长反推，误差约 0.7 秒。
