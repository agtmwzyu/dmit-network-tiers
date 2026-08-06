# DMIT线路：三档网络按需挑,CN2 GIA 回程对中国大陆延迟最低

上周有个朋友想搞台 VPS 给家里老人看点大陆视频，问我选哪家。我没多想就报了 DMIT，结果他被官网一堆 Pro / Eyeball / Tier 1 / LAX / HKG / TYO 的组合搞晕了，回来问我到底"DMIT线路"是什么意思、选哪一档合适。这篇就当我在白板前给他画一遍——顺便把坑也踩给你看。

## DMIT 线路是什么

DMIT 是一家 2018 年成立、总部在美国的云服务商，主营高性能 VPS 和裸金属服务器。它家最被反复提起的就是"线路"——也就是从它在美国、香港、东京的机房把流量送回中国大陆时，走的是哪种运营商路径。DMIT 把自家线路分成三档：**Premium**（CN2 GIA + 自建骨干）、**Eyeball**（CMI/CMIN2 尽力优化）、**Tier 1**（纯国际标准路由，不做中国优化）。同一台机器，选哪一档，回程路径、延迟、丢包、价格能差出一个量级。

简单说：Premium 是给"我就是冲着大陆延迟低来的"的人；Eyeball 是给"想要大陆体验过得去但预算有限"的人；Tier 1 是给"压根不服务大陆用户"的人。

## 三档线路到底差在哪

讲真，DMIT 官网对这三档的描述其实写得很清楚，但容易让新手看迷糊。我用大白话拆一遍。

### Premium：CN2 GIA 三网回程

Premium 这一档把 DMIT 自建骨干网、Tier 1 国际 transit 和 China Telecom 的 CN2 GIA 都揉在一起，对中国大陆做专门优化。回程走 CN2 GIA 的话，到国内三网的延迟比标准路径低不少，跳数少，丢包率也明显改善。如果你最在乎的就是"打开国内网站快不快、晚高峰会不会卡"，Premium 是 DMIT 的招牌答案。

对应的套餐后缀都是 `.Pro`，比如 LAX.Pro.STARTER、HKG.Pro.TINY、TYO.Pro.MINI。 👉 [查看 DMIT 全部 Pro 系列套餐](https://bit.ly/DMIt)

### Eyeball：CMIN2 / CMI 尽力优化

Eyeball 这档定位是"reasonable effort for China routing"，说人话就是：会用 CMI（中国移动国际）或 CMIN2 这类中国运营商的精品线路去做回程优化，但不像 Premium 那样给你 CN2 GIA 这种承诺级的精品路径。延迟比 Tier 1 好，比 Premium 差，价格夹在中间。

DMIT 洛杉矶的 Eyeball 系列在用户圈里口碑挺响，回程被反复提到的是"三网 CMIN2 + 9929"这种组合——联通走 AS9929、移动走 CMIN2，电信则是尽力优化。对预算不算宽裕但又想晚高峰不掉链子的人来说，这是 DMIT 性价比最高的一档。

套餐后缀是 `.EB`，比如 LAX.EB.STARTER、HKG.EB.STARTERv2、TYO.EB.MICRO。 👉 [查看 DMIT Eyeball 系列套餐](https://bit.ly/DMIt)

### Tier 1：纯国际路由

Tier 1 这档不做任何中国优化，就是标准互联网路由，对欧美到亚洲、亚洲内部、美西内部做延迟优化。配置给得很慷慨——流量动辄 4000GB 起、端口"based on performance"（按性能给），价格也是三档里最低的，月付 $12.9 起步。

但你要清楚：Tier 1 不是"DMIT 便宜款"，它是给完全不需要服务大陆的人准备的。比如你做的是面向欧美用户的站点、跨境团队内部协作、做中转节点喂别的服务，这种场景 Tier 1 反而比 Premium 更合适——你不为用不到的 CN2 GIA 多掏钱。套餐后缀是 `.T1`。 👉 [查看 DMIT Tier 1 系列套餐](https://bit.ly/DMIt)

## 三大机房怎么选

DMIT 目前在售的有三个机房：洛杉矶 LAX、香港 HKG、东京 TYO。每个机房都同时提供 Pro / EB / T1 三档线路，但三档之间的价格差异和适用场景差别很大。

**洛杉矶 LAX**：机房最成熟、套餐最全、补货也最频繁。Premium 系列在这边主推 CN2 GIA 三网回程，从大陆访问延迟在 150ms 上下，晚高峰体验在同类 CN2 GIA 产品里属于第一梯队。同价位段能拿出三网 CN2 GIA + 10Gbps 端口这个组合的同行不多。

**香港 HKG**：到大陆延迟最低，物理距离摆在那。Premium 系列在 HKG 是 CN2 GIA 入境 + 自建骨干回程，到广东一带 ping 值能压到 30ms 出头。但价格也是三地最贵——HKG.Pro.STARTER 月付 $79.9 起，比 LAX 同档贵一倍多。带宽上限也只到 1Gbps。香港 Premium 适合做"低延迟优先、预算不是问题"的场景。

**东京 TYO**：定位夹在 LAX 和 HKG 之间。Premium 系列是电信 CN2 GIA + 联通 AS9929 + 移动 CMI 的三网精品回程，延迟比洛杉矶低一些、比香港略高，价格也比香港有优势。我自己用下来的体感是 TYO.Pro 在江浙沪一带 ping 值稳定在 50ms 上下，比 LAX 顺眼不少。 👉 [对比三个机房所有套餐](https://bit.ly/DMIt)

## 全套餐对比表

下面这张表覆盖了 DMIT 官网目前在售的常规套餐（不含限量年付特惠款）。价格都是月付起步价，年付通常会更便宜；具体每个套餐的年付 / 季付折扣以官网实时为准。

### 洛杉矶 LAX

| 套餐 | 线路档 | vCPU | 内存 | 存储 | 月流量 | 端口 | 月付起步 | 链接 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| LAX.Pro.STARTER | Premium | 2 | 2GB | 80GB SSD | 3000GB | 10Gbps | $29.90 | [选此方案](https://bit.ly/DMIt) |
| LAX.Pro.MINI | Premium | 4 | 4GB | 80GB SSD | 5000GB | 10Gbps | $58.88 | [选此方案](https://bit.ly/DMIt) |
| LAX.Pro.MICRO | Premium | 4 | 4GB | 160GB SSD | 7000GB | 10Gbps | $74.99 | [选此方案](https://bit.ly/DMIt) |
| LAX.EB.STARTER | Eyeball | 2 | 2GB | 80GB SSD | 5000GB | 10Gbps | $29.90 | [选此方案](https://bit.ly/DMIt) |
| LAX.EB.MINI | Eyeball | 4 | 4GB | 80GB SSD | 10000GB | 10Gbps | $58.88 | [选此方案](https://bit.ly/DMIt) |
| LAX.EB.MICRO | Eyeball | 4 | 4GB | 160GB SSD | 14000GB | 10Gbps | $74.99 | [选此方案](https://bit.ly/DMIt) |
| LAX.T1.STARTER | Tier 1 | 1 | 2GB | 40GB SSD | 4000GB | 按性能 | $12.90 | [选此方案](https://bit.ly/DMIt) |
| LAX.T1.MINI | Tier 1 | 2 | 2GB | 60GB SSD | 8000GB | 按性能 | $21.90 | [选此方案](https://bit.ly/DMIt) |
| LAX.T1.MICRO | Tier 1 | 4 | 4GB | 80GB SSD | 16000GB | 按性能 | $32.90 | [选此方案](https://bit.ly/DMIt) |

### 香港 HKG

| 套餐 | 线路档 | vCPU | 内存 | 存储 | 月流量 | 端口 | 月付起步 | 链接 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| HKG.Pro.STARTER | Premium | 1 | 2GB | 40GB SSD | 800GB | 1Gbps | $79.90 | [选此方案](https://bit.ly/DMIt) |
| HKG.Pro.MINI | Premium | 2 | 2GB | 60GB SSD | 1200GB | 1Gbps | $119.90 | [选此方案](https://bit.ly/DMIt) |
| HKG.Pro.MICRO | Premium | 4 | 4GB | 80GB SSD | 1600GB | 1Gbps | $159.90 | [选此方案](https://bit.ly/DMIt) |
| HKG.EB.STARTERv2 | Eyeball | 1 | 2GB | 40GB SSD | 2000GB | 2Gbps | $59.90 | [选此方案](https://bit.ly/DMIt) |
| HKG.EB.MINIv2 | Eyeball | 2 | 2GB | 60GB SSD | 3000GB | 2Gbps | $89.90 | [选此方案](https://bit.ly/DMIt) |
| HKG.EB.MICROv2 | Eyeball | 4 | 4GB | 80GB SSD | 4000GB | 4Gbps | $129.90 | [选此方案](https://bit.ly/DMIt) |
| HKG.T1.STARTER | Tier 1 | 1 | 2GB | 40GB SSD | 4000GB | 按性能 | $12.90 | [选此方案](https://bit.ly/DMIt) |
| HKG.T1.MINI | Tier 1 | 2 | 2GB | 60GB SSD | 8000GB | 按性能 | $21.90 | [选此方案](https://bit.ly/DMIt) |
| HKG.T1.MICRO | Tier 1 | 4 | 4GB | 80GB SSD | 16000GB | 按性能 | $32.90 | [选此方案](https://bit.ly/DMIt) |

### 东京 TYO

| 套餐 | 线路档 | vCPU | 内存 | 存储 | 月流量 | 端口 | 月付起步 | 链接 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TYO.Pro.STARTER | Premium | 1 | 2GB | 40GB SSD | 500GB | 1Gbps | $39.90 | [选此方案](https://bit.ly/DMIt) |
| TYO.Pro.MINI | Premium | 2 | 2GB | 60GB SSD | 1000GB | 1Gbps | $79.90 | [选此方案](https://bit.ly/DMIt) |
| TYO.Pro.MICRO | Premium | 4 | 4GB | 80GB SSD | 2000GB | 1Gbps | $159.90 | [选此方案](https://bit.ly/DMIt) |
| TYO.EB.STARTER | Eyeball | 1 | 2GB | 40GB SSD | 2000GB | 2Gbps | $55.90 | [选此方案](https://bit.ly/DMIt) |
| TYO.EB.MINI | Eyeball | 2 | 2GB | 60GB SSD | 3000GB | 2Gbps | $85.90 | [选此方案](https://bit.ly/DMIt) |
| TYO.EB.MICRO | Eyeball | 4 | 4GB | 80GB SSD | 4000GB | 4Gbps | $119.90 | [选此方案](https://bit.ly/DMIt) |
| TYO.T1.STARTER | Tier 1 | 1 | 2GB | 40GB SSD | 4000GB | 按性能 | $12.90 | [选此方案](https://bit.ly/DMIt) |
| TYO.T1.MINI | Tier 1 | 2 | 2GB | 60GB SSD | 8000GB | 按性能 | $21.90 | [选此方案](https://bit.ly/DMIt) |
| TYO.T1.MICRO | Tier 1 | 4 | 4GB | 80GB SSD | 16000GB | 按性能 | $32.90 | [选此方案](https://bit.ly/DMIt) |

LAX.Pro 和 LAX.EB 系列在超量流量后会限速不停机：Pro.WEE / Pro.MALIBU / EB.INTRO / EB.WEE / EB.CORONA 这类限量款超量后限速 2Mbps，标准款按更高档位限速。具体阈值以官网条款为准。 👉 [前往 DMIT 查看实时套餐库存](https://bit.ly/DMIt)

## 怎么选：四步走

1. **判断你服不服务大陆用户**。不服务 → 直接 Tier 1，省下的钱拿去升配置。服务 → 继续。
2. **判断你对延迟的敏感度**。要追求最低延迟、做实时交互（视频会议、远程桌面、低延迟爬虫回源）→ 选 Premium。能接受 50-150ms 的尽力优化 → Eyeball 已经够用。
3. **定机房**。预算够 + 极致低延迟 → 香港 HKG。性价比 + 综合体验 → 东京 TYO。流量大 + 美西方向用户多 → 洛杉矶 LAX。
4. **定套餐规格**。个人轻量用 → STARTER / TINY 起步就够；建站或多人共用 → MINI 起；跑业务、虚拟化嵌套 → MICRO 及以上。 👉 [前往 DMIT 按四步选适合的套餐](https://bit.ly/DMIt)

## 几个买之前一定要知道的点

退款这块要先说清楚，免得你买完才发现踩坑。DMIT 的退款政策是分级的：购买 3 天内、且流量使用不超过 30GB，可以申请全额退款（扣支付网关手续费）；30 天内可以申请部分退款，按已用流量或剩余时长中较短的那条算。超过 30 天、被 DDoS 过、因网络质量或 IP 地理位置原因，都不退。同一系列已经退过 3 次的也不退。

IP 替换政策也很关键，因为大陆用户经常碰到 IP 被墙的问题。Premium 和 Eyeball 系列不带 IP Care+ 服务时，每 15 天可以免费换一次 IP；带 IP Care+ 的话每 7 天一次。Premium Secure 系列（带 DDoS 高防的）单独定价，每次换 IP $15，30 天一次。Tier 1 系列默认不保证 IP 全球可达——尤其对中国、俄罗斯这类有网络审查的地区，建议加购 IP Guarantee+。

我自己实际用 LAX.Pro.STARTER 跑了大半年，印象最深的是晚高峰期 CN2 GIA 回程没断过线，下载速度稳在百兆上下。讲真，论稳定性它在我用过的几家同价位 CN2 GIA VPS 里是排在前列的——只是价格也摆在那。 👉 [以 $29.90/月 起 PRO 系列开始使用](https://bit.ly/DMIt)

说句题外话，DMIT 在用户圈里有句流传挺广的话叫"除了贵没别的毛病"。这话不算夸张。Premium 系列月付 $29.9 起步，香港 Pro 直接 $79.9 起，对个人轻量用户来说压力不低。但你要想清楚一件事：你为 CN2 GIA 这条回程路径付的钱，并不是付给"虚拟化技术"的——技术哪家都有；你付的是 DMIT 拿 CN2 GIA 长期续约的带宽成本。这条路径稳定但贵，是行业常识，不是 DMIT 一家的问题。换算到每天的话，LAX.Pro.STARTER 月付 $29.9 算下来日均不到 $1，对长期能用得上的人来说并不离谱。

## 常见问题

**DMIT 线路 Pro / EB / T1 怎么区分？**
Pro = Premium，含 CN2 GIA + 自建骨干，对中国大陆做承诺级优化；EB = Eyeball，用 CMI/CMIN2 等中国运营商精品线路做尽力优化；T1 = Tier 1，纯国际标准路由，不优化中国。三档价格和回程质量依次递减。

**DMIT 哪个机房到大陆最快？**
香港 HKG 物理距离最近，Premium 系列到广东一带 ping 值能压到 30ms 出头；东京 TYO 次之，江浙沪一带 50ms 上下；洛杉矶 LAX 距离最远但套餐最全、CN2 GIA 回程稳定，三网回程延迟 150ms 左右。

**DMIT Premium 和搬瓦工 CN2 GIA 比怎么样？**
两家定位接近，都走 CN2 GIA 回程。DMIT 的差异点在 10Gbps 大带宽端口和自建骨干网层面做得更彻底，套餐规格颗粒度更细；搬瓦工的价格门槛更低、套餐组合更灵活。预算敏感选搬瓦工入门款，追求稳定大带宽选 DMIT Pro。

**DMIT Eyeball 系列值不值得买？**
如果你需要"对中国大陆体验过得去、但不想为 Premium 的 CN2 GIA 多掏钱"，Eyeball 是 DMIT 性价比最高的一档。LAX.EB 走 CMIN2 + AS9929 的三网尽力优化，晚高峰表现比 Tier 1 明显好，价格只比 Premium 便宜一点但流量给得翻倍。

**DMIT 超流量会停机吗？**
LAX.Pro 和 LAX.EB 系列采用"超量限速不停机"策略，超量后限速到 2Mbps 或更高，服务不会中断。HKG 和 TYO 的具体策略以官网当前条款为准。所有套餐流量都是双向计的（BIDI），上下行合计算。

## 结尾给你一个直接决策

如果你看完还在纠结，那就这么定：纯个人轻量、追大陆延迟低、不差钱 → 香港 HKG.Pro.STARTER 月付 $79.9 起步；预算要卡、又想要过得去的大陆体验 → 洛杉矶 LAX.EB.STARTER 月付 $29.9；压根不服务大陆、只在乎大流量便宜 → 洛杉矶 LAX.T1.STARTER 月付 $12.9。这三档刚好覆盖了 DMIT 线路的三种典型用法，选哪一台都不会跑偏。 👉 [前往 DMIT 锁定最适合你的套餐](https://bit.ly/DMIt)
