# iOS / iPadOS 侧载选择、安装与避坑

先区分**应用宿主**、**签名证书**、**安装/续签工具**和**游戏数据**：引擎或游戏库不是签名方式；一个应用内承载多个游戏也不等于绕过签名。用户账号类型、地区、系统与项目能力不同，规则随时变化。

## 如何选择

| 方案 | 特点与条件 | 适合 / 注意 |
|---|---|---|
| [AltStore Classic](https://github.com/altstoreio/AltStore) | 使用 AltServer 和 Apple 账号；可在设备管理安装、续签及停用应用 | 适合已有 AltStore 用户；Windows 端核对其当前 Apple 驱动、服务和网络要求；不是 AltStore PAL 的同义词 |
| [SideStore](https://github.com/SideStore/SideStore) | AltStore 的开源分支，初装需电脑，后续使用设备端流程、配对、Wi-Fi 和 VPN | 适合希望设备端刷新的人；先核对最新官方安装文档，不保证无需人工干预 |
| [Sideloadly](https://sideloadly.io/) | 桌面端安装 IPA，官方列出自动刷新及无线功能 | 可比较对大包、扩展和签名的实际表现；本项目只引用其官网，不将它描述成已确认开源或本项目依赖 |
| [LiveContainer](https://github.com/LiveContainer/LiveContainer) | 在已安装的宿主中运行部分 IPA | 本身仍需安装，应用兼容性、文件访问和运行限制各异；不是全部游戏都能用，也不保证可满足特殊权限 |
| [TrollStore](https://github.com/opa334/TrollStore) | 利用受支持系统版本上的特定机制安装应用 | 仅限官方列明的版本和安装条件，不推断最新系统可用，也不要求用户更改系统 |

AltStore Classic 的官方文档记载：免费个人开发账号常见的限制包括 7 天刷新、最多 3 个活跃侧载 App，以及 7 天内最多 10 个 App ID；App 扩展可消耗额外 ID。实际以账户、系统、工具与官方当前规则为准，不能把“活跃应用数”和“App ID 数”混为一谈。停用通常由 AltStore 备份后移除 App，仍应先独立备份并验证重要存档。见 [激活应用](https://faq.altstore.io/altstore-classic/activating-apps)、[App IDs](https://faq.altstore.io/altstore-classic/app-ids)。

## Windows / macOS 安装流程

1. 从工具官方来源获取安装程序，检查平台和版本。Windows 按工具文档准备 Apple 驱动/服务（部分流程对 Apple 直装或商店版依赖不同）；macOS 按当前版本文档准备。不要为排障直接卸载已有组件。
2. 解锁设备、连接 USB、按设备提示信任电脑；工具须实际识别设备。按需要由用户在设备打开开发者模式和信任开发者，重启及确认流程见 [Apple 官方说明](https://developer.apple.com/documentation/xcode/enabling-developer-mode-on-a-device)。
3. 用户自行在可信界面处理 Apple 登录和验证码；不要向聊天或日志输出凭据、配对记录、签名证书或设备标识。先确认签名能力和已有 App，备份最新存档。
4. 以所选工具签名安装 IPA；等待最终成功，并查询实际安装的 App / 签名后 bundle ID。应用更新是否保留容器取决于 bundle ID、签名方式和安装行为，更新前仍应备份；不要先卸载再赌存档保留。
5. 按该应用支持的文件共享或其他正式入口传资源。检查应用实际数据路径、容量、分块传输和哈希，启动游戏验证，再按工具要求续签。不同 App 或框架的 entitlement 不可假设一致。

## 常见错误和定位

- **电脑能看到设备，工具却不能**：检查 USB、解锁和信任、Apple 设备服务、驱动版本与工具的识别结果；不要反复重装全部 iTunes 或清理其他软件。
- **到期 / 不能激活**：区分证书到期、刷新失败、三应用槽和 App ID 数量；查看工具里的错误码、当前 App IDs 和到期时间。换签名工具不必然消除 Apple 账号限制。
- **安装失败或 `PackageExtractionFailed`**：记录工具、系统、包大小、实际 ZIP 结构、条目数量、空间及签名日志。先校验 IPA，再看是否为大型 ZIP、资源、文件数量或签名问题；需要分体时先证实宿主支持外置资源。
- **几百 MB IPA 与十几 GB 游戏**：宿主可能将 ROMFS、DLC、shader 外置，不能按体积猜测；确认 App 的数据路径和挂载日志。外置路径与大小写按引擎版本而定。
- **数据上传中断**：若支持续传，先比对已有前缀和目标真实长度，再续传；最后逐文件校验大小与同算法哈希。不要对未确认的路径追加或覆盖。
- **设备列举到 App 但 Documents 无权限**：确认签名后真实 bundle ID、文件共享能力及正确容器；例如 HouseArrest 的 documents-only 模式可能需要从 `/Documents` 访问而非 `/`。
- **侧载工具切换/停用应用**：先确定工具是否接管已有签名、是否保留应用数据和扩展；截图、日志及备份必须分属正确游戏。大包临时中转不要擅用别的游戏目录。

SideStore 具体要求参见 [准备条件](https://docs.sidestore.io/docs/installation/prerequisites) 和 [安装指南](https://docs.sidestore.io/docs/installation/install.html)。
