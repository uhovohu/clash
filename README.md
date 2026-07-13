
### 使用说明
**本配置具备 DNS 防泄漏 UDP 防泄漏**
- DNS 配置 nameserver（兜底） 使用 53明文 8.8.8.8 是为了最大程度兼容家宽，因为有些家宽禁止加密 DNS
- 如果你在win下使用本配置后还是出现 DNS 泄漏问题，请参考下列教程 关闭多宿主名称解析策略
- https://wildprobe.com/soft-technical/dnsleak/

**mihomo 核心 app 通用设置：**
- 关闭 ipv6 
- 关闭 dns 覆写 
- 开启 tun 模式
- 使用 fakeip 模式

**OpenClash nikki 等通用设置：**
- 关闭 ipv6 
- 关闭 dns 覆写
- 使用 fakeip 模式
- TCP 模式：TPROXY
- UDP 模式：TUN

### 链式代理说明
配置文件 机场订阅 Proxy Providers 模块（配置文件最前部分）

> **provider1 provider2 作为 入口（IN组）**
> 建议引用 线路机节点 或 机场节点 作为入口
> 
> **Link-OUT 作为 出口（OUT组**）
> 建议引用 家宽节点 或 落地机节点 作为落地出口

尽量使用纯节点的订阅链接填入
请尽量使用最新内核，理论上mihomo内核高于v1.18.6 链式代理配置可用

<img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/link-preview.png" width="100%">

> uhovohu-mihomo-lite.yaml # 含链式代理 精简分组
>
> uhovohu-mihomo-nolink-lite.yaml # 不含链式代理 精简分组
>
> uhovohu-mihomo-nolink.yaml # 不含链式代理 完整分组
>
> uhovohu-mihomo.yaml # 含链式代理 完整分组

### 策略组说明
建议使用 zashboard 面板 适配策略组图标

> **各 app 分组 默认 Proxy 组**
> **例：apple 组选择 Proxy，Proxy 组选择 OUT ，最终 apple 组 出口为 OUT 内节点**

### 更新了策略组图标  建议使用 zashboard 面板
### 设置：外观 -- 策略组图标尺寸 24 -- 策略组图标间距 6
| <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-phone-dark.png" width="100%"> | <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-phone-light.png" width="100%"> |
|:---:|:---:|
| Dark | Light |

| <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-pc-dark.png" width="100%"> | <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-pc-light.png" width="100%"> |
|:---:|:---:|
| Dark | Light |

仓库未引用规则 有需要请自行引用
- binance
- bitget
- bookmap
- bybit
- htx
- okx
- coinpoker
- natural8
- tradingview
- truthsocial



### 更新了github的用户名，文件链接有所变化
> 例 
> 
> 变更前 https://raw.githubusercontent.com/uhovohu-glitch/clash/refs/heads/main/uhovohu-mihomo-nolink.yaml
> 
> 变更后 https://raw.githubusercontent.com/uhovohu/clash/refs/heads/main/uhovohu-mihomo-nolink.yaml
> 
> 请将 uhovohu-glitch 替换为 uhovohu

> 各app规则使用过程如有遗漏请提交 issue 我会及时修正补充

> [!WARNING]
> ## ⚠️ 免责声明 / Disclaimer
> 
> 本模板及其包含的所有分流规则、DNS 配置及代码片段**仅供个人技术学习与自用研究**。
> 
> 🚫 **严禁**将本库内容、配置文件或相关指南在**中国大陆地区**进行任何形式的公开传播、搬运分享或用于任何商业用途。
> 
> 请务必严格遵守您所在地区的法律法规，合理合法使用网络工具。因滥用本模板造成的任何后果由使用者自行承担。
