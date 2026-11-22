<div align="center">

# konohana-saku8

直播间 [live.bilibili.com/22748536](https://live.bilibili.com/22748536) · 主页 [space.bilibili.com/2094031249](https://space.bilibili.com/2094031249)

</div>

> 本组织由个人维护。主播是个人势、没有团队；这里的内容不代表主播及其粉丝的立场，也与主播本人无关。
> 逐字稿与弹幕可能存在识别错误，引用前请核对原直播，不要断章取义；更不要拿这些内容去给主播带节奏、挑事或引战。

直播相关的一组工具：实时翻译、逐字稿存档、弹幕采集。

## 仓库

| 仓库 | 内容 |
| --- | --- |
| [live-archive](https://github.com/konohana-saku8/live-archive) | 逐字稿存档站。**25 场、17 296 条**中日对照，按场次浏览、全库检索 |
| [LiveTranslate](https://github.com/konohana-saku8/LiveTranslate) | Windows 实时翻译。抓系统声音实时识别并翻译，结果显示在透明置顶悬浮窗；也可接收手机推送的音频 |
| [LiveTranslateClient](https://github.com/konohana-saku8/LiveTranslateClient) | Android 客户端。把手机上其他应用的声音交给电脑翻译，手机悬浮窗同步显示原文与译文 |
| [danmaku-it](https://github.com/konohana-saku8/danmaku-it) | B 站弹幕 / SC 采集工具。悬浮弹幕机可看直播、发弹幕，记录可导出 NDJSON / CSV |
| [live-capture](https://github.com/konohana-saku8/live-capture) | 旧手机上的常驻定时服务。记录直播的弹幕 / SC / 礼物 / 动态与场次切分、录像，网页端管理与导出 |
| [LiveCaptions-Translator](https://github.com/konohana-saku8/LiveCaptions-Translator) | 读取 Windows 实时字幕并翻译，重写字幕显示（fork） |

## 实时翻译

电脑端抓系统声音（可选混入麦克风）实时识别，交给任意 OpenAI 兼容接口流式翻译，
结果显示在透明置顶悬浮窗里。

手机端（Android 10+）选择一个应用共享它的声音，结果同时回到手机悬浮窗，样式与电脑端一致。
同一时间只接受一台手机；局域网点「连接」即可，访问令牌可留空。

## 存档站

<https://konohana-saku8.github.io/live-archive/>

每场一份：话题带、目录、逐条日文原文 + 中文译文，支持全库搜索。数据来自 LiveTranslate
的翻译和 danmaku-it 的弹幕 / SC 记录，整理后发布；数据库本身不入库。
