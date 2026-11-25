# uhovohu mihomo 配置

适用于 mihomo 内核的分流配置,已针对 DNS 泄漏与 UDP 泄漏进行防护设计。内核版本要求 **v1.19.19** 及以上。

## 配置文件

| 文件名 | 链式代理 | 版本 |
|---|:---:|:---:|
| `uhovohu-mihomo.yaml` | ✅ | 完整版 |
| `uhovohu-mihomo-lite.yaml` | ✅ | 精简版 |
| `uhovohu-mihomo-nolink.yaml` | ❌ | 完整版 |
| `uhovohu-mihomo-nolink-lite.yaml` | ❌ | 精简版 |

- **完整版**:按服务细分策略组,并提供地区节点分组。
- **精简版**:仅保留常用服务;其余海外流量由 Final 组承接,国内流量由兜底规则直连。

规则集均引用自 [uhovohu/mihomo-rules](https://github.com/uhovohu/mihomo-rules),每日自动更新。本仓库 `Rules/` 目录已停止维护,仅为兼容旧链接保留。

## 客户端设置

**mihomo 内核类应用**

| 设置项 | 推荐值 |
|---|---|
| IPv6 | 开启 |
| TUN 模式 | 开启 |
| DNS 模式 | fake-ip |
| DNS 覆写 | 关闭 |

**OpenClash / Nikki 等路由器插件**

| 设置项 | 推荐值 |
|---|---|
| IPv6 代理 | 局域网已分配 IPv6 时开启 |
| DNS 模式 | fake-ip |
| DNS 覆写 | 关闭 |
| TCP 代理模式 | TPROXY |
| UDP 代理模式 | TUN |

- Windows 平台如仍检测到 DNS 泄漏,请关闭「多宿主名称解析策略」,参见 [教程](https://wildprobe.com/soft-technical/dnsleak/)。

## IPv6

本配置支持 IPv6 连接,但不进行 IPv6 DNS 解析:

- `ipv6: true`:接管设备的 IPv6 流量,防止其绕过代理,并可连接 IPv6 节点。
- `dns.ipv6: false`:不向设备返回 IPv6 地址,应用通过 IPv4 访问网站。

以上两项请保持不变。iOS 设备由无 IPv6 网络切换至有 IPv6 网络后,需重新连接一次。

## 链式代理

在配置文件开头的 `proxy-providers` 中填入订阅:

- **provider1 / provider2**:入口(IN 组),填入中转节点或机场节点订阅。
- **Link-OUT**:出口(OUT 组),填入家宽节点或落地节点订阅。

建议使用仅包含节点信息的纯节点订阅。

<img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/link-preview.png" width="100%">

## 策略组

各服务策略组默认指向 Proxy 组;Microsoft、Apple、Bilibili、Steam、Epic、TapTap 默认指向 CN 组,CN 组默认直连。

**完整版**

| 类别 | 策略组 |
|---|---|
| 入口 | Proxy(链式版另含 IN、OUT) |
| AI | OpenAI、Anthropic、AI |
| 海外服务 | YouTube、Google、GitHub、Microsoft、Adobe、Apple、Android |
| 社交 | X、Meta、Telegram、Discord、Social |
| 影音 | TikTok、Netflix、Spotify、Media、Emby、Bilibili |
| 游戏 | Steam、Epic、TapTap |
| 加密货币 | Crypto(含各交易所及行情工具) |
| 支付 | PayPal、Wise、Pay |
| 托管与 CDN | Cloudflare、Amazon、Akamai |
| 工具 | IPtest、Speedtest、SaaS、ProxyMisc |
| 兜底 | CN、Final |
| 地区节点 | HK、TW、JP、KR、SG、US、OTHERS1、OTHERS2 |

**精简版**

Proxy(链式版另含 IN、OUT)、OpenAI、Anthropic、AI、YouTube、Google、GitHub、Microsoft、Apple、X、Telegram、TikTok、Netflix、Spotify、Steam、CN、Final。

**支付分组(仅完整版)**

- **PayPal**:PayPal、Braintree、Venmo、Xoom。
- **Wise**:Wise。
- **Pay**:通用支付网关、风控、人机验证与身份认证(KYC)服务,如 Stripe、Adyen、Sift、Forter、hCaptcha、Sumsub。各服务专属的风控域名归属该服务的分组,Pay 仅承接通用部分。

Pay 日常建议跟随 Proxy。在某一服务中付款或实名认证时,如该服务的分组未选择 Proxy,建议将 Pay 临时切换至同一节点,避免因 IP 不一致触发风控。

**SaaS 分组(仅完整版)**

承接海外应用内嵌的第三方服务,如 Sentry、RevenueCat、OneTrust;国内部分由 CN 组承接。这些服务为多个应用共用,建议日常跟随 Proxy。

## 面板

推荐使用 **zashboard** 面板,外观设置:`策略组图标尺寸 24 / 策略组图标间距 6`。

| <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-phone-dark.png" width="100%"> | <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-phone-light.png" width="100%"> |
|:---:|:---:|
| Dark | Light |

| <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-pc-dark.png" width="100%"> | <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-pc-light.png" width="100%"> |
|:---:|:---:|
| Dark | Light |

## 问题反馈

如发现规则遗漏或误分流,请提交 Issue。

> [!WARNING]
> **免责声明 / Disclaimer**
>
> 本仓库内容**仅供个人技术学习与研究使用**。**严禁**在**中国大陆地区**以任何形式公开传播、转载本仓库内容与配置文件,或将其用于任何商业用途。请遵守所在地区的法律法规,因滥用本仓库内容造成的一切后果由使用者自行承担。
