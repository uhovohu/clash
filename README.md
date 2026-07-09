
### 使用说明
本配置具备dns防泄漏
各平台app设置：关闭ipv6 关闭dns覆写 开启tun模式（ niiki等 TCP模式：TPROXY  UDP模式：TUN ）

请尽量使用最新内核
理论上mihomo内核高于v1.18.6 链式代理配置可用

> uhovohu-mihomo-lite.yaml # 含链式代理 精简分组
>
> uhovohu-mihomo-nolink-lite.yaml # 不含链式代理 精简分组
>
> uhovohu-mihomo-nolink.yaml # 不含链式代理 完整分组
>
> uhovohu-mihomo.yaml # 含链式代理 完整分组

建议使用纯节点的订阅链接填入配置文件

### 更新了策略组图标  建议使用 zashboard 面板
### 设置：外观 -- 策略组图标尺寸 24 -- 策略组图标间距 6
| <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-phone-dark.png" width="100%"> | <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-phone-light.png" width="100%"> |
|:---:|:---:|
| Dark | Light |

| <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-pc-dark.png" width="100%"> | <img src="https://raw.githubusercontent.com/uhovohu-glitch/clash/main/icons/zashboard-pc-light.png" width="100%"> |
|:---:|:---:|
| Dark | Light |

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