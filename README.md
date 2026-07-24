# Exhibition Market Research Skill

Read-only market research and company analysis workflow for international exhibition businesses. It is designed for Feishu AI Agents and similar agent platforms.

The Skill combines internal business data with verified web research to help marketing and sales teams answer: what to sell, where to enter, who to approach, which trade shows to evaluate, and what to validate next.

## English Overview

### Core capabilities

- Search connected CRM, company-selection, buyer/CDP, Feishu Base, historical exhibitor, and content-center sources.
- Identify historical customer relationships and exhibition history without exposing sensitive CRM fields.
- Analyze product-market fit, target countries, buyers, channels, competitors, exhibitions, tariffs, HS-code candidates, and market-entry policies.
- Restrict exhibition recommendations to current, product- and country-matched Miolante projects, with the same project ID carried through the report.
- Generate decision-oriented reports in Feishu Cloud Documents.
- Use a report mode appropriate to the available evidence: market-entry decision, market validation, or opportunity exploration.

### Workflow

```text
Company / product / target market input
        ↓
Read-only internal source queries
        ↓
Web search and full-page verification
        ↓
Market comparison, buyer matching, competitor and exhibition analysis
        ↓
Source-linked report and 30/60/90-day action plan
```

### Evidence and source traceability

Search snippets are discovery clues only. External facts must be verified by opening the source page, confirming the publisher and date, recording the evidence and retrieval date, and adding a source ID such as `[S1]` in the report. The source table must contain a clickable URL. Unavailable, conflicting, or snippet-only sources are marked `待核验` and cannot support a definitive ranking, tariff conclusion, buyer recommendation, or exhibition go/no-go decision.

### Safety and integration boundaries

- Business systems are read-only; only the final Feishu Cloud Document may be created.
- No new Base or configuration table is required.
- CRM amounts, contacts, phone numbers, emails, personal information, and unnecessary contract details are hidden by default.
- HS codes are candidates until confirmed by the appropriate customs, importer, or compliance party.
- Additional market recommendations must come from current, product-matched Miolante project countries; generic public exhibition lists are not used as replacements.
- The actual tool names, fields, and permission filters are adapted to the connected Feishu Agent environment.

### Documentation

- [Chinese detailed documentation](#中文说明)
- [Skill instructions](exhibition-market-research/SKILL.md)
- [Evidence and citation rules](exhibition-market-research/references/research-evidence.md)
- [Feishu report template](exhibition-market-research/references/report-template.md)
- [Acceptance test scenarios](exhibition-market-research/references/test-cases.md)

---

## 中文说明

面向国际会展企业的只读市场调研与企业分析 Skill，主要运行在飞书智能体中。

它根据企业名称、产品和目标市场，优先查询已接入的 CRM、Selection 企业库、Selection Buyers/CDP、飞书 Base、历史展商素材库和内容中心，再联网核验企业、展会、关税与政策信息，最终生成结论先行、来源可追溯的飞书云文档报告。

第一阶段以飞书智能体为主要运行环境。Skill 不要求新增 Base、配置表或底层数据库权限，只按照智能体实际暴露的入口和权限执行。

## 能做什么

- 判断中国企业是否为历史客户，查询 CRM 中的客户、商机、合同和拜访关系。
- 查询 Selection 企业库中的中国企业、展商、产品、行业和出口信息。
- 从 Selection Buyers / CDP 筛选海外买家，并分析可能采购的具体产品。
- 从飞书 Base 查询展会照片、展位、现场记录和历史同行。
- 从历史展商素材库查询同行海报、单页和历史展会素材。
- 从内容中心按国家和产品查询已包装、已推送的运营素材。
- 联网打开网页正文，核验企业、展会、关税、认证、准入和最新政策；正文逐条标注来源编号，来源表提供可点击链接和检索日期。
- 只从当前有效、产品和国家匹配的米奥兰特项目中推荐展会；指定市场之外最多从米奥兰特项目国家/地区中补充 1-2 个市场。
- 推荐最多 3 个市场、10 家买家和 5 个米奥兰特项目，并创建飞书云文档报告。

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

## 来源核验规则

联网搜索结果只用于发现候选来源，不能直接把搜索摘要写成结论。对准备写入报告的外部事实，必须完成：

1. 搜索候选页面。
2. 打开网页正文，确认页面标题、发布方、日期和相关原文。
3. 记录来源编号、可点击 URL、检索日期和关键证据摘录。
4. 对关税、政策、市场规模、买家采购事实、展会信息等关键命题进行独立来源交叉核验。
5. 在正文对应事实后标注 `[S1]` 等来源编号，并在文末来源表回链到可点击链接。

网页无法打开、链接失效、只有搜索摘要或来源之间存在冲突时，必须标注“待核验”，降低结论等级并给出补证动作。

## 报告输出

根据输入完整度自动选择报告类型：

- **市场进入决策报告**：产品、目标市场和业务目标明确，输出市场比较、买家开发、准入路径、展会判断和行动计划。
- **市场验证报告**：产品族和应用明确，但 SKU、采购或合规细节仍需验证。
- **市场机会探索简报**：只有企业名称或泛产品方向时，输出假设、渠道画像和待核验线索，不伪造精确买家、HS 税率或市场排名。

完整报告通常包含：

- 执行摘要和市场进入结论；
- 企业与产品的市场化能力；
- 候选市场比较和证据完整度；
- 买家、渠道、竞品和下游标杆分层；
- 候选 HS 编码、关税、准入和政策；
- 展会及替代获客渠道的 go/no-go 条件；
- 30/60/90 天销售与市场行动计划；
- 来源、核验状态、研究边界和待验证事项。

推荐数量采用“固定上限、证据不足则减少”：最多 3 个市场、10 家买家、5 个米奥兰特项目和 10 条内容素材。每个重要来源、同行、HS 和政策事实都必须有面向销售/市场的商业解读。

## 只读与隐私规则

- CRM、Selection、Base、买家库和素材库只读。
- 只创建最终飞书云文档，不修改业务数据。
- 默认隐藏 CRM 金额、联系人、联系方式、个人身份信息和不必要的合同细节。
- 水单、付款凭证等财务资料不属于本 Skill 的研究范围。
- 推断的 HS 编码必须标注“待确认”，不能替代正式报关归类。
- 内部记录与外部核验结果分开呈现，不自动覆盖原始数据。

CRM 金额、联系人、手机号、邮箱、个人身份信息和不必要的合同细节默认不进入报告。Skill 只允许创建最终飞书云文档，不写回 CRM、Selection、Base、买家库、素材库或内容中心。

## 飞书接入

首次使用时，将以下逻辑数据源映射到飞书智能体中已经接入的工具入口：

```text
CRM 客户/合同入口
Selection 企业库入口
Selection Buyers / CDP 入口
飞书 Base 展会历史入口
米奥兰特项目/展会入口
历史展商素材库入口
内容中心入口
联网搜索入口
飞书云文档创建入口
```

不要求新增 Base 或配置表，也不要求拥有底层数据库完整后台权限。Skill 按飞书智能体实际暴露的入口和权限执行。

首次接入或工具入口变化时，需要先确认每个入口的查询对象、参数、返回字段和权限过滤，并将适配结果保存在 Skill 或飞书智能体配置中，不新增业务表。

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
- [米奥兰特项目与市场选择](exhibition-market-research/references/miolante-project-selection.md)
- [HS 编码与关税规则](exhibition-market-research/references/tariff-and-hs.md)
- [报告模板](exhibition-market-research/references/report-template.md)
- [验收测试场景](exhibition-market-research/references/test-cases.md)

## 验证状态

Skill 结构校验、数据源路由、只读规则、敏感字段脱敏、HS 编码待确认规则和文档链接检查已通过。当前验收清单已覆盖 31 个场景，包括米奥兰特项目硬过滤、当前日期筛选、来源解读、同行案例、HS 商业分析、市场机会与政策利好。真实 CRM、Selection、Base、联网搜索和飞书云文档的端到端测试，需要在飞书智能体中使用脱敏测试企业执行 [验收场景](exhibition-market-research/references/test-cases.md)。
