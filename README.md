# 使用说明

本配置已针对 **DNS 泄漏** 与 **UDP 泄漏** 进行防护设计。

## DNS 说明

- 兜底 `nameserver` 使用明文 53 端口的 `8.8.8.8`,目的是最大限度兼容家庭宽带环境——部分家宽运营商会拦截或劣化加密 DNS。
- 若在 Windows 平台使用本配置后仍检测到 DNS 泄漏,请参考以下教程关闭「多宿主名称解析策略」(Smart Multi-Homed Name Resolution):
  https://wildprobe.com/soft-technical/dnsleak/

## 客户端通用设置

<table>
<tr>
<td valign="top">

**mihomo 内核类 App:**

| 设置项 | 推荐值 |
|---|---|
| IPv6 | 关闭 |
| DNS 覆写 | 关闭 |
| TUN 模式 | 开启 |
| DNS 模式 | fake-ip |

</td>
<td valign="top">

**OpenClash / Nikki 等路由器插件:**

| 设置项 | 推荐值 |
|---|---|
| IPv6 | 关闭 |
| DNS 覆写 | 关闭 |
| DNS 模式 | fake-ip |
| TCP 代理模式 | TPROXY |
| UDP 代理模式 | TUN |

</td>
</tr>
</table>

# 链式代理说明

链式代理由配置文件起始部分的 `proxy-providers` 模块(机场订阅)定义:

> **provider1 / provider2 —— 入口(IN 组)**
> 建议填入线路机(中转)节点或机场节点的订阅。
>
> **Link-OUT —— 出口(OUT 组)**
> 建议填入家宽节点或落地机节点的订阅,作为最终落地出口。

注意事项:

- 订阅链接请尽量使用仅含节点信息的「纯节点订阅」。
- 请尽量使用最新版 mihomo 内核;链式代理配置理论上要求内核版本不低于 **v1.18.6**。

<img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/link-preview.png" width="100%">

## 配置文件说明

| 文件名 | 链式代理 | 策略分组 |
|---|:---:|:---:|
| `uhovohu-mihomo.yaml` | ✅ | 完整 |
| `uhovohu-mihomo-lite.yaml` | ✅ | 精简 |
| `uhovohu-mihomo-nolink.yaml` | ❌ | 完整 |
| `uhovohu-mihomo-nolink-lite.yaml` | ❌ | 精简 |

# 策略组说明

- 各应用分组默认指向 **Proxy** 组。
- 出口链路示例:`apple 组 → Proxy 组 → OUT 组`,即当 apple 组选择 Proxy、Proxy 组选择 OUT 时,apple 组的最终出口为 OUT 组内所选节点。

## 面板与图标

策略组图标已更新,建议配合 **zashboard** 面板使用以获得最佳显示效果。

推荐外观设置:`设置 → 外观 → 策略组图标尺寸 24 / 策略组图标间距 6`

| <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-phone-dark.png" width="100%"> | <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-phone-light.png" width="100%"> |
|:---:|:---:|
| Dark | Light |

| <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-pc-dark.png" width="100%"> | <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-pc-light.png" width="100%"> |
|:---:|:---:|
| Dark | Light |

# 未默认引用的规则

以下规则集已包含在仓库中,但未在配置文件内默认引用,如有需要请自行添加:

`binance` · `bitget` · `bookmap` · `bybit` · `htx` · `okx` · `coinpoker` · `natural8` · `tradingview` · `truthsocial`

# 仓库地址变更

GitHub 用户名已由 `uhovohu-glitch` 变更为 `uhovohu`,原始文件(raw)链接随之变化:

> 变更前:`https://raw.githubusercontent.com/uhovohu-glitch/clash/refs/heads/main/uhovohu-mihomo-nolink.yaml`
>
> 变更后:`https://raw.githubusercontent.com/uhovohu/clash/refs/heads/main/uhovohu-mihomo-nolink.yaml`

如订阅或规则链接失效,请将链接中的 `uhovohu-glitch` 替换为 `uhovohu`。

# 问题反馈

各应用分流规则如有遗漏或误分流,欢迎提交 Issue。

> [!WARNING]
> ## ⚠️ 免责声明 / Disclaimer
>
> 本仓库及其包含的所有分流规则、DNS 配置与代码片段**仅供个人技术学习与研究使用**。
>
> 🚫 **严禁**在**中国大陆地区**以任何形式公开传播、转载分享本库内容与配置文件,或将其用于任何商业用途。
>
> 请严格遵守您所在地区的法律法规,合理合法使用网络工具。因滥用本仓库内容造成的一切后果,由使用者自行承担。