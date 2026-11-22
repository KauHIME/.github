<div align="center">

# konohana-saku8

直播间 [live.bilibili.com/22748536](https://live.bilibili.com/22748536) · 主页 [space.bilibili.com/2094031249](https://space.bilibili.com/2094031249)

</div>

直播相关的一组工具：实时翻译、逐字稿存档、弹幕采集。

> 本组织由观众自发维护，**与主播本人无关**，也不是官方账号，这里的一切内容不代表主播及其团队的立场。
> 逐字稿与弹幕可能存在识别错误，引用前请核对原直播，不要断章取义；更不要拿这些内容去给主播带节奏、挑事或引战。

## 仓库

| 仓库 | 内容 |
| --- | --- |
| [live-archive](https://github.com/hibane-hinome/live-archive) | 逐字稿存档站。**25 场、17 296 条**中日对照，按场次浏览、全库检索 |
| [LiveTranslate](https://github.com/hibane-hinome/LiveTranslate) | Windows 实时翻译（fork）。系统音频 → VAD → ASR → 大模型流式翻译 → 置顶悬浮窗；本仓库增加了逐句时间戳落库、手机远程接入与 ReazonSpeech 引擎 |
| [LiveTranslateClient](https://github.com/hibane-hinome/LiveTranslateClient) | Android 客户端。抓取其他应用播放的音频推到电脑，复用电脑的 ASR 与翻译，悬浮窗同步显示原文和译文 |
| [danmaku-it](https://github.com/hibane-hinome/danmaku-it) | 弹幕与 SC 采集，和翻译记录写进同一个 SQLite |
| [live-capture](https://github.com/hibane-hinome/live-capture) | 旧手机上的常驻定时服务：弹幕 / SC / 礼物 / 动态采集、场次切分与直播录像，Flask + Vue 网页端管理与查阅 |
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
