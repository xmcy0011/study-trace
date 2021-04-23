# study-trace
study od,ce and trace wechat

## Depends 

开发依赖：
- vs2017
- [nim_duilib](https://github.com/netease-im/NIM_Duilib_Framework)
- [wechat: 3.1.0.67 (2020-12-24)](https://weixin.qq.com/cgi-bin/readtemplate?lang=zh_CN&t=weixin_faq_list)
- vcpkg

调试工具：
- DebugView：windows内核日志，方便查看dll的日志，调试
- OD(Ollydbg)：汇编调试工具，可断点修改汇编代码等。逆向必备工具
- CE(Cheat Engine)：修改器，可以查找特征，通常用来找各种内存地址。
- 读微信Png图片.exe：网上找的资源，可以快速验证二维码地址是否有效。

## Quick Start

1. install vcpkg, [see](https://github.com/microsoft/vcpkg)
```bash
$ git clone https://github.com/microsoft/vcpkg
$ .\vcpkg\bootstrap-vcpkg.bat
```

2. install depends
```bash
$ vcpkg install crossguid # 跨平台guid，see: https://github.com/graeme-hill/crossguid
```

使用vs2017打开trace_all.sln，把injector设为启动项，运行。选择要注入的dll即可查看效果。

工程说明：
- injectcore：逆向核心代码，静态库可复用。
- injector：微信注入器，界面基于nim_duilib。
- injectordll：注入器测试动态库，使用debugview工具可查看日志。
- loginQRCode：登录二维码HookDemo，可以显示微信登录二维码，包括刷新操作等。
- loginStatusMonit：登录状态监控，每1秒钟打印一次微信的登录状态。
- logHook：微信日志hook，可以通过debugview工具查看微信的日志。
- recvMsgHook：接收消息hook，可以通过debugview工具查看收到的微信消息。

## 学习笔记

- [注入器](./gitbook/0-注入器.md)
- [二维码](./gitbook/1-登录二维码.md)
- [登录状态](./gitbook/2-登录状态和个人信息.md)
- [好友列表](./gitbook/3-好友列表.md)
- [微信日志](./gitbook/4-微信日志hook.md)
- [收消息](./gitbook/5-收消息hook.md)
- [发消息](./gitbook/6-发消息.md)

## 鸣谢

学习过程中，很多思路都是来自于一下视频：
1. 《2019PC微信HOOK逆向分析》：学习了hook的原理，但是因为时间较久，很多方法在最新的微信版本上基本没用了
2. 《易语言TV Pc微信Hook逆向教程》：学习了二维码的逆向思路，通过IHDR的方式搜索很高效。
3. 《微信 3.1.0.72 逆向 HOOK 分析教程》：B站UP主2021年3月份刚上传的教程，里面的方法对最新版的微信收发消息这一块介绍的思路很有效果。

## 免责声明

本项目仅供技术研究，请勿用于任何商业用途，请勿用于非法用途，如有任何人凭此做任何非法事情，均与作者无关，后果自负，特此声明。