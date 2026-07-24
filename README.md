# 展会市场调研 Skill

面向国际会展企业的只读市场调研与企业分析 Skill，主要运行在飞书智能体中。

它根据企业名称、产品和目标市场，优先查询已接入的 CRM、Selection 企业库、Selection Buyers/CDP、飞书 Base、历史展商素材库和内容中心，再联网核验企业、展会、关税与政策信息，最终生成飞书云文档报告。

## 能做什么

- 判断中国企业是否为历史客户，查询 CRM 中的客户、商机、合同和拜访关系。
- 查询 Selection 企业库中的中国企业、展商、产品、行业和出口信息。
- 从 Selection Buyers / CDP 筛选海外买家，并分析可能采购的具体产品。
- 从飞书 Base 查询展会照片、展位、现场记录和历史同行。
- 从历史展商素材库查询同行海报、单页和历史展会素材。
- 从内容中心按国家和产品查询已包装、已推送的运营素材。
- 联网打开网页正文，核验企业、展会、关税、认证、准入和最新政策；正文逐条标注来源编号，来源表提供可点击链接和检索日期。
- 推荐最多 3 个市场、10 家买家和 5 个展会，并创建飞书云文档报告。

报告会先判断输入是否达到完整研究门槛：

- **市场进入决策报告**：产品、目标市场和业务目标明确，可给出市场比较、买家开发、准入路径和行动计划。
- **市场验证报告**：产品族和应用明确但 SKU 或合规信息不足时，输出验证方向和补充条件。
- **市场机会探索简报**：只有企业名称或泛产品方向时，不伪造精确买家、HS 税率或市场排名。

报告重点交付市场进入命题、同口径市场比较、买家/渠道/竞品分层、展会 go/no-go 条件以及 30/60/90 天行动计划，而不是单纯汇总内部资料。

## 工作流

```text
输入企业名称、产品或目标市场
        ↓
内部客户、企业、买家、展会和同行资料查询
        ↓
联网核验企业、产品、展会、关税和政策
        ↓
市场评分、买家匹配、同行与展会分析
        ↓
查询内容中心补充素材
        ↓
创建飞书云文档报告
```

## 只读与隐私规则

- CRM、Selection、Base、买家库和素材库只读。
- 只创建最终飞书云文档，不修改业务数据。
- 默认隐藏 CRM 金额、联系人、联系方式、个人身份信息和不必要的合同细节。
- 水单、付款凭证等财务资料不属于本 Skill 的研究范围。
- 推断的 HS 编码必须标注“待确认”，不能替代正式报关归类。
- 内部记录与外部核验结果分开呈现，不自动覆盖原始数据。

## 飞书接入

首次使用时，将以下逻辑数据源映射到飞书智能体中已经接入的工具入口：

```text
CRM 客户/合同入口
Selection 企业库入口
Selection Buyers / CDP 入口
飞书 Base 展会历史入口
历史展商素材库入口
内容中心入口
联网搜索入口
飞书云文档创建入口
```

不要求新增 Base 或配置表，也不要求拥有底层数据库完整后台权限。Skill 按飞书智能体实际暴露的入口和权限执行。

## 输入示例

```text
请调研江苏某某机械有限公司，主营工业激光切割设备，重点分析德国、波兰和土耳其市场，推荐海外买家和适合参加的展会，并生成飞书云文档报告。
```

## 仓库内容

- [Skill 主文件](exhibition-market-research/SKILL.md)
- [完整使用介绍](exhibition-market-research/README.md)
- [数据源适配规范](exhibition-market-research/references/data-source-adaptation.md)
- [市场评分规则](exhibition-market-research/references/market-scoring.md)
- [报告质量门槛](exhibition-market-research/references/report-quality-gates.md)
- [市场进入论证](exhibition-market-research/references/market-entry-analysis.md)
- [买家、渠道与竞品分层](exhibition-market-research/references/buyer-and-benchmark.md)
- [HS 编码与关税规则](exhibition-market-research/references/tariff-and-hs.md)
- [报告模板](exhibition-market-research/references/report-template.md)
- [验收测试场景](exhibition-market-research/references/test-cases.md)

## 验证状态

Skill 结构校验、数据源路由、只读规则、敏感字段脱敏、HS 编码待确认规则和文档链接检查已通过。当前验收清单已覆盖 23 个场景，包括市场比较、泛行业数据、买家库噪音、同行库不可用、来源不可用、网页核验、来源回链和报告质量门槛。真实 CRM、Selection、Base、联网搜索和飞书云文档的端到端测试，需要在飞书智能体中使用脱敏测试企业执行 [验收场景](exhibition-market-research/references/test-cases.md)。
