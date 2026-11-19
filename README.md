# iOS / iPadOS 游戏移植与侧载 Skill

一个面向 Codex 的中文工作流：先调查设备和游戏，再选择构建、侧载、数据传输和排障路径。支持 NX2Apple、S2Arm 等场景，并把"多个应用共用一个侧载名额"的容器方案作为独立路线纳入决策，历史故障整理为匿名化案例。**不是游戏分发包或一键保证兼容的工具。**

## 从这里开始

1. [设备与兼容性](skills/ios-game-porting/references/devices.md)：设备、系统、内存、GPU 和电脑环境。
2. [侧载工具选择与避坑](skills/ios-game-porting/references/sideloading.md)：AltStore、SideStore、Sideloadly 等的差别、签名、续期、名额与安装排障。
3. [容器方案](skills/ios-game-porting/references/container.md)：用一个宿主承载多个应用，绕开 3 个侧载名额的限制；数据布局、迁移步骤、传输速率与兼容性边界。
4. [完整构建与部署流程](skills/ios-game-porting/references/workflow.md)：输入调查、构建、IPA、资源、存档、校验和验收。
5. [MetalFX、画面与帧率](skills/ios-game-porting/references/graphics.md)：分辨率、超分、插帧、补丁和对照测试。
6. [故障与历史案例](skills/ios-game-porting/references/pitfalls.md)：着色器、闪退、黑闪、后台、手柄与容器迁移问题。
7. [第三方项目及引用](THIRD_PARTY.md)：开源仓库、官方资料和各自许可证。

> 第二版新增容器方案这一条路线。它解决的是名额，不是兼容性：宿主本身仍占一个名额、仍要续签，装入的应用能不能跑取决于宿主给不给它所需的能力。

## 安装 Skill

将 [skills/ios-game-porting](skills/ios-game-porting) 整个目录安装到 Codex 的 skills 目录，或通过支持 GitHub 的 Skill 安装工具选择本仓库的 `skills/ios-game-porting` 子目录。启动新的 Codex 会话后可使用 `$ios-game-porting`。

示例：`使用 $ios-game-porting，根据我的设备和系统选择侧载方案，检查游戏和存档后继续。`

适用性依设备、系统、账号、引擎及游戏版本而异，使用前核对上游文档。请使用自己有权使用的游戏和输入；仓库不含游戏、IPA、ROM、固件、密钥、证书或存档。
