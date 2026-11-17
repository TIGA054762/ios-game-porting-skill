---
name: ios-game-porting
description: Guide iPhone and iPad game porting, device compatibility, iOS sideloading choices, NX2Apple or S2Arm builds, external data, saves, MetalFX, and evidence-led troubleshooting. Use for game porting and sideloading projects; verify device and tool versions before acting.
---

# iOS 游戏移植与排障

先理解当前目标：构建游戏、选择侧载方式、部署应用和数据、迁移存档、比较引擎、解决画面或性能问题。先确认设备、操作系统与电脑平台，再检查当前状态；历史案例不是当前事实。

## 开始前

1. 阅读适用的 AGENTS.md 与用户最新要求。删除任何文件、目录前遵守现行删除授权规则；不要用清理、重建或重签推定删除授权。保护游戏源、存档、着色器、缓存、已有应用及其依赖。
2. 了解游戏、版本、Build ID、区域、输入资源、设备系统、引擎、签名方式、运行状态与目标。确认现有数据和空闲空间；先查现场、日志与产物，不凭旧文档断言路径存在。
3. 尊重用户已有侧载和签名偏好；需要释放名额时由用户决定停用哪个应用，先导出并校验最新存档。不要索取 Apple 账号密码或验证码。
4. 只处理用户提供且有使用权的游戏和构建输入；不得把游戏文件、存档、密钥、证书、账号信息、设备标识上传到 GitHub 或第三方。公开或分享构建材料前先审查其内容。

## 选择参考资料

- 首先读 [设备与兼容性](references/devices.md)，确认机型、系统、存储、能力与电脑环境，不根据芯片名或系统版本保证效果。
- 选侧载工具或排查签名问题：读 [侧载选择与排障](references/sideloading.md)。
- 新游戏从输入调查到安装验收：读 [构建与部署流程](references/workflow.md)。安装包、外部资源和签名是不同步骤，不能混为一谈。
- 画面、MetalFX、分辨率和帧率：读 [图形与性能](references/graphics.md)，不要混淆超分、插帧和解锁游戏帧率。
- 遇到编译、安装、黑屏、语言、帧率、触控或后台问题：读 [故障与避坑](references/pitfalls.md)，先取当前日志，再改变单一变量验证。
- 需要借鉴已有调查时读 [匿名化案例](references/cases.md)；不把案例表现泛化为所有设备或游戏。
- 若版本行为或工具能力可能变化，先查 [上游入口](references/sources.md) 的当前官方文档，再决定方案。不能把某次 Windows 构建成功扩大为所有游戏都能一键构建。

## 核心交付原则

记录输入版本、工具链、命令与产物、保存策略、日志、体积、校验方法和设备实际验证。区分编译完成、安装完成、资源读回校验、启动成功、用户确认存档与长时间游玩；哪一步未验证就明确写出。需要用户在设备上配合时给出具体动作，不干扰其他应用。

每次试验前备份用户进度；高风险补丁按游戏版本和 Build ID 匹配，默认可回退。设备配置每次只改变一个变量，记录基线、改动、重启与对照，记录看到的结果而非预设结论。结束时说明保留了什么、变更了什么、如何恢复以及尚未解决的问题。
