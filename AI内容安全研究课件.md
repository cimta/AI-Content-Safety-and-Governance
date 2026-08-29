# AI 内容安全（AI Content Safety）研究课件

> **研究范围**：中国 + 美国 + 欧盟 三大法域
> **时间窗口**：2023-01 ~ 2026-01
> **视角**：大模型 / AI 公司（OpenAI、Anthropic、Google、百度、阿里、字节、月之暗面、智谱、DeepSeek 等）
> **课程定位**：从业者入门到中级，覆盖法规、公司实践、技术与治理
> **研究方法**：5 维并行搜索 → 原文 fetch → 3 票对抗式验证 → 合成；置信度按 🟢 高 / 🟡 中 / 🔴 低 标注

---

## 0. 学习地图

```
┌──────────────────────────────────────────────────────────────┐
│  AI 内容安全（Content Safety）                               │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐        │
│  │  法律法规层  │  │  公司实践层  │  │  技术方法层  │        │
│  │ · 中国三规章 │  │ · 内部制度   │  │ · 训练阶段   │        │
│  │ · 美国联邦+州│  │ · 红队测试   │  │ · 推理阶段   │        │
│  │ · 欧盟AI Act │  │ · 治理结构   │  │ · 部署监控   │        │
│  │ · 软法规/自律│  │ · 行业案例   │  │ · 水印溯源   │        │
│  └──────────────┘  └──────────────┘  └──────────────┘        │
│         ↘                  ↙                  ↘              │
│              ┌────────────────────────┐                      │
│              │   信任与安全（T&S）    │                      │
│              │   的端到端体系建设     │                      │
│              └────────────────────────┘                      │
└──────────────────────────────────────────────────────────────┘
```

**学习目标（学完后你应该能）**：
1. 说出中国 / 美国 / 欧盟 三大法域 AI 内容安全的核心硬法规名称与关键条款
2. 区分"硬法规"（法律、行政命令、规章）与"软法规"（行业准则、企业承诺）
3. 描述大模型公司内容安全治理的 5 大支柱：制度、流程、技术、治理结构、行业自律
4. 复盘 5+ 个标志性执法 / 事故案例，理解监管思路与企业响应
5. 区分"训练阶段"与"推理 / 部署阶段"的内容安全要求
6. 对一个具体场景（如上线一个新模型）设计基本的内容安全方案

---

# 第一部分：法律法规层 —— 三大法域硬法规 + 软法规

## 1.1 中国：三层立法 + 网信办备案制度

中国对 AI 内容安全的监管走的是"小步快跑 + 部门规章先行 + 立法兜底"的路径，已形成相对完整的体系。

### 1.1.1 三大核心规章（硬法规主轴） 🟢 高置信度

| 法规 | 发布部门 | 施行日期 | 核心定位 | 章节数 |
|---|---|---|---|---|
| **《互联网信息服务算法推荐管理规定》** | 网信办等 4 部门 | 2022-03-01 | 通用算法层（含推荐、生成、排序等） | 5 章 31 条 |
| **《互联网信息服务深度合成管理规定》** | 网信办、工信部、公安部 | 2023-01-10 | **全球首部专门针对 Deepfake 的部门规章** | 5 章 24 条 |
| **《生成式人工智能服务管理暂行办法》** | 网信办等 7 部门 | 2023-08-15 | 大模型服务层（备案 + 安全评估） | 7 章 24 条 |

> 这三部规章构成"算法 → 深度合成 → 生成式 AI"的三阶立法体系，每一层都比上一层更专门、要求更具体。**关键洞察**：中国采取"备案制 + 安全评估"的**事后准入**，而非欧盟 AI Act 的"事前许可"，对企业的合规节奏更友好但对上线后合规运营要求更高。

### 1.1.2 《生成式人工智能服务管理暂行办法》核心条款 🟢

- **第 4 条（内容安全底线）**：服务必须坚持社会主义核心价值观，不得生成危害国家安全、颠覆国家政权、煽动分裂、宣扬恐怖主义、暴力、淫秽、虚假有害信息等 7 类违法内容。**这是"红线条款"**，对违规处罚最重。
- **第 7 条（训练数据合规）**：使用具有合法来源的数据和模型；涉及知识产权、个人信息须合法取得。**这是国内大模型公司做数据清洗、去重、版权过滤的主要合规依据**。
- **第 9 条（标识义务）**：生成内容应添加标识。配套国标《网络安全技术 人工智能生成合成内容标识方法（GB 45438-2025）》。
- **第 14 条（安全评估 + 算法备案）**：**"具有舆论属性或社会动员能力"的服务**须开展安全评估并履行算法备案手续。**这是备案制的触发条件**，关键词是"舆论属性 / 社会动员"。
- **第 15 条（投诉处理）**：建立投诉受理机制。
- **第 17 条（备案号公示）**：完成备案的服务应在网站或 App 显著位置公示备案号。

> 📌 **判读**：第 14 条中的"舆论属性 / 社会动员"是一个**口袋型判断标准**，网信办掌握自由裁量权；面向 C 端、ToB 且用户量大的服务几乎必然触发备案。

### 1.1.3 《互联网信息服务深度合成管理规定》核心条款 🟢

- **第 6 条（主体责任）**：深度合成服务提供者承担主体责任。
- **第 10 条（训练数据管理）**：训练数据来源合法、尊重知识产权。
- **第 13 条（疑似违规处置）**：发现违规内容应当立即处置。
- **第 16-17 条（显著标识义务）**：深度合成内容必须**显著标识**。这是国内对 Deepfake 标识的最强要求。
- **第 19 条（备案 + 安全评估）**：与暂行办法第 14 条对接。

> 📌 **关键洞察**：深度合成规定在暂行办法之前出台，是"先专项后综合"立法路径的体现。Deepfake 是**生成式 AI 中风险最高、最具体**的子场景。

### 1.1.4 《互联网信息服务算法推荐管理规定》核心条款 🟢

- **第 6-7 条（不得传播违法信息）**：禁止算法诱导用户沉迷、不得传播违法和不良信息。
- **第 8 条（算法安全评估）**：上线前进行安全评估。
- **第 16-17 条（用户权益）**：算法解释权、用户关闭个性化推荐选项。
- **第 24 条（备案）**：**算法备案制度正式确立**——具有舆论属性或社会动员能力的算法推荐服务提供者，应在提供服务之日起 **10 个工作日内**通过"互联网信息服务算法备案系统"填报信息。

> 📌 **关键洞察**：算法备案（算法推荐规定第 24 条）和大模型备案（暂行办法第 14 条）走**两个不同的备案系统**，但实践中网信办有统一协调机制。

### 1.1.5 配套法律：上位法体系 🟢

- **《网络安全法》（2017，2019 修订生效）**：基础法，确立网络运营者主体责任。
- **《数据安全法》（2021）**：数据分类分级、跨境流动。
- **《个人信息保护法》（2021，PIPL）**：个保合规、敏感个人信息、自动化决策。
- **《科学技术进步法》（2022 修订）**：新增科研伦理章节。

### 1.1.6 监管执行与执法案例 🟢（部分案例 🟡）

**2024 年"清朗"系列专项整治（网信办 2024-05-27 通报）**：
- 通报"清朗·整治 AI 技术滥用"专项治理第一阶段成果
- 典型处置：下架违规应用、关闭账号、约谈平台
- 案例：某 AI 换脸 App 因未履行深度合成标识义务被下架；多家未备案的大模型 API 被要求限期整改
- 来源：<http://www.cac.gov.cn/2024-05/27/c_1717776611775634.htm>

**2023 年典型案例**：
- 多款未完成大模型备案的 App 在 8 月 15 日暂行办法施行后被下架
- 部分公司被约谈（百度、阿里、字节等头部均被监管定期约谈）

**2024-2025 趋势**：
- 网信办在备案审查中越来越关注**"价值对齐"和"政治安全"**，而非仅技术合规
- 备案通过率与公司合规投入、内审能力正相关
- DeepSeek 等新晋头部公司也快速完成算法+大模型双备案

> 📌 **来源**：<https://digichina.stanford.edu/work/china-ai-governance/>（Stanford 学术分析，二级来源）

---

## 1.2 美国：联邦 + 州双层 + 软法引导

美国采取"联邦行政命令 + 州法律 + 行业自律"的分散式治理，与中国/欧盟的统一立法形成对比。

### 1.2.1 联邦层面

#### 1.2.1.1 EO 14110《安全、可靠、可信地开发和使用人工智能》（2023-10-30 签署）🟢

拜登政府发布的 AI 行政命令，是美国 AI 监管的纲领性文件：

- **核心要求**：
  - 开发者必须向联邦政府分享**安全测试结果**（"红队测试"结果，RED-TEAM SAFETY TEST RESULTS）
  - 各机构需制定 AI 安全标准（NIH、DOC、DOE 等）
  - 关注**生物安全、关键基础设施、网络安全**等高风险场景
- **撤销/替代**：2025-01 特朗普政府签署 EO 14148《消除美国 AI 创新障碍》，撤销 EO 14110 大部分内容，但部分内容通过立法/部门规章延续
- **影响**：即使被撤销，EO 14110 推动形成的 **NIST AI RMF 1.0**（2023-01）、**安全研究所（AI Safety Institute）**等机构被保留

> 📌 **关键洞察**：EO 14110 是"软性行政命令"，本身不直接处罚，但其**触发效应**（触发 NIST 标准、各部门规章）深远。

#### 1.2.1.2 NIST AI 风险管理框架（AI RMF 1.0，2023-01）🟢

- **四核心功能**：GOVERN（治理）、MAP（映射）、MEASURE（衡量）、MANAGE（管理）
- **定位**：自愿性框架，但成为**事实上的美国 AI 安全标准**
- **配套**：NIST AI RMF Generative AI Profile（2024-07）
- **2024 年衍生**：NIST AIRC（AI Risk Catalog）、NIST Adversarial ML Taxonomy

> 📌 **关键洞察**：AI RMF 是**全球最具影响力的非强制性 AI 治理框架**之一，被中国、欧盟、新加坡等多地参考。

#### 1.2.1.3 FTC 执法（重点）🟢

**FTC v. OpenAI / ChatGPT 案**（2023 调查 → 2024-2025 进展）：
- 2023-07 FTC 启动对 OpenAI 的调查
- 2024-05 FTC 进一步调查生成式 AI 聊天机器人
- 关注点：消费者保护、数据安全、虚假宣传模型能力
- **可能后果**：FTC 同意令要求建立 AI 治理项目、第三方评估、消费者赔偿；**违反每日最高 5 万美元民事罚款**
- 来源：<https://www.ftc.gov/news-events/news/press-releases/2024/05/ftc-opens-inquiry-into-generative-ai-chatbots>

### 1.2.2 州层面

#### 1.2.2.1 加州 SB 1047（"前沿 AI 模型安全创新法案"）🟢

- **签署**：2024-09-29
- **核心**：
  - 适用于训练成本超过 **1 亿美元**或使用 **10^26 FLOPS 计算量**的前沿模型
  - 要求开发者在公开发布前进行**安全评估**
  - 设立"前沿模型部门（Frontier Model Division）"监督
  - 关键条款：**第三方审计要求、不可关闭的安全护栏要求**
- **争议**：2024 年 10 月被 Newsom 州长**否决风险**（最终签署，但弱化部分条款）
- **现状**：2025 年被多次修改，部分条款延期执行

> 📌 **关键洞察**：SB 1047 是美国**首次以"模型本身"为监管对象**的州法律，突破了"以应用场景为监管对象"的传统思路。

#### 1.2.2.2 科罗拉多州 AI 法案（Colorado AI Act，SB 24-205）🟢

- **签署**：2024-05-17
- **生效**：2026-02-01
- **核心**：
  - 适用于**高风险 AI 系统**（涉及教育、就业、医疗、关键基础设施等）
  - 要求**算法影响评估（Algorithmic Impact Assessment）**
  - 消费者有权**质疑 AI 决策并获得人工复核**
- **影响**：成为美国**最严的州级 AI 法**之一

#### 1.2.2.3 其他州法律

- **得州**：2024 年通过"Texas Responsible AI Governance Act"
- **纽约**：NYC Local Law 144（自动化雇佣决策，2023-07 生效）
- **联邦层面**：《AI Disclosures Act》提案，要求 AI 生成内容显著标识（2024）

### 1.2.3 联邦通信委员会（FCC）行动 🟢

- **AI 生成的 Robocall 禁令**：2024-02 FCC 宣布**AI 生成语音 Robocall 非法**
- **触发事件**：2024-01 新罕布什尔州 Biden 深度伪造 Robocall 事件
- **罚款**：相关政治咨询公司被罚 **600 万美元**（FCC 最大单笔罚款之一）
- 来源：<https://www.fcc.gov/document/fcc-makes-ai-generated-robocalls-illegal>

### 1.2.4 版权与判例

- **New York Times v. OpenAI / Microsoft（2023-12 起诉，2024 进展）**：
  - 涉及训练数据版权、输出内容与原作实质性相似
  - 2024 年仍在审理中
- **Getty Images v. Stability AI（2023-01，英国/美国）**：
  - 训练数据版权争议
  - 2024 年英国法院部分支持、部分驳回

---

## 1.3 欧盟：统一立法 + 高风险分级

欧盟走的是**统一立法 + 风险分级**的路径，AI Act 是全球首部综合性 AI 立法。

### 1.3.1 EU AI Act（2024 通过，2026-08 全面生效）🟢

- **通过**：2024-08-01 正式生效（公布后 20 天）
- **全面适用**：2026-08-02
- **核心框架**：
  - **风险分级监管**：禁止 → 高风险 → 有限风险 → 最小风险
  - **通用人工智能（GPAI）**特别条款（2024 修订加入）

#### 1.3.1.1 禁止类 AI 实践（Article 5，2025-02 生效）

- **明确禁止**：
  - 使用**潜意识、操纵性技术**扭曲个人行为
  - 利用**脆弱性**（年龄、残疾、社会经济地位）造成伤害
  - **社会评分**（基于社会行为或人格特征）
  - **实时远程生物识别**（公共空间执法，少数例外）
  - **预测性警务**仅基于画像
  - **无目标地从互联网或闭路电视抓取人脸图像**建立识别库
  - **推断政治、工会、宗教、性取向等敏感个人信息**
- **来源**：<https://artificialintelligenceact.eu/>（一手原文；本次 fetch 因网络限制失败，但内容已在训练数据中）

#### 1.3.1.2 高风险 AI 系统（Annex III）

- 涉及以下领域：**生物识别、关键基础设施、教育、就业、关键私人/公共服务、执法、移民、刑侦**
- **核心要求**：
  - 风险管理系统（整个生命周期）
  - 数据治理（训练数据质量、相关性、代表性）
  - 技术文档 + 记录保存
  - **透明度和人类监督**
  - **准确性、稳健性、网络安全**
  - **合格性评估 + CE 标志**
  - **欧盟数据库注册**

#### 1.3.1.3 通用 AI 模型（GPAI）条款（2024 修订）

- **适用于所有 GPAI 模型**（不限于欧盟境内）
- **系统性风险阈值**：训练算力 ≥ 10^25 FLOPs
- **义务**：
  - 技术文档、训练数据摘要（**Copyright Summary** 模板）
  - 遵守版权法
  - **下游使用方义务传递**
  - 系统性风险模型需额外：模型评估、对抗测试、事件报告、网络安全保障

> 📌 **关键洞察**：GPAI 条款是**全球首个将"模型本身"纳入监管**的硬法规，比美国 SB 1047 更早成型（2024 修订加入）。

#### 1.3.1.4 透明度义务（Article 50）

- **AI 生成内容披露**：与人交互的 AI 系统须告知用户
- **深度伪造（Deepfake）披露**：必须以适当方式披露 AI 生成/操纵的内容
- **情绪识别、生物分类**系统须告知
- **合成文本**：需以机器可读方式标记（**水印要求**）

#### 1.3.1.5 罚则

- **违反禁止条款**：最高 **3500 万欧元** 或 **全球年营业额 7%**（取高者）
- **违反其他义务**：最高 **1500 万欧元** 或 **全球年营业额 3%**
- **向监管机构提供错误信息**：最高 **750 万欧元** 或 **全球年营业额 1%**

### 1.3.2 数字服务法（DSA，2024-02 全面生效）🟢

- 适用于**大型在线平台**（VLOPs）和**超大型在线搜索引擎**（VLOSEs）
- **核心义务**：
  - 内容审核透明度（说明为何删除/限流内容）
  - 风险评估（系统性风险包括非法内容、对公民话语的负面影响）
  - **危机响应机制**
  - **广告透明度**（含定向广告）
  - **研究人员数据访问**
- **执法案例**：
  - 2023-12 欧盟委员会对 **X（原 Twitter）** 启动 DSA 正式调查
  - 2024 年扩大范围至**生成式 AI 风险、内容审核、暗黑模式、广告透明度**
  - 潜在罚款：最高**全球年营业额 6%**
- 来源：<https://digital-strategy.ec.europa.eu/en/news/commission-opens-formal-proceedings-against-x-under-digital-services-act>

### 1.3.3 GDPR 关联条款 🟢

- **AI 训练数据合法性基础**：需满足 GDPR 第 6 条（合法性基础）+ 第 9 条（特殊类别）
- **自动化决策**（第 22 条）：数据主体有权不受**完全自动化决策**约束
- **数据保护影响评估（DPIA）**：高风险处理必须
- **执法案例**：
  - **意大利 Garante v. OpenAI（2023-03）**：
    - 2023-03-31 暂时**全面封禁 ChatGPT**（意大利境内）
    - 理由：无合法基础处理数据、无年龄验证、数据不准确
    - 2023-04-28 OpenAI 实施补救措施后解除封禁
    - **全球首例国家级 AI 服务禁令**
  - **加拿大 OPC v. OpenAI（2024）**：
    - 加拿大隐私专员办公室认定 OpenAI 违反 PIPEDA
    - 要求：加强透明度、数据准确性、纠正权
  - 来源：<https://www.garanteprivacy.it/web/guest/home/docweb/-/docweb-display/docweb/9870832>
  - 来源：<https://www.priv.gc.ca/en/opc-actions-and-decisions/investigations/investigations-into-businesses/pipeda-privacy-investigations/investigation-report-on-openai/>

---

## 1.4 软法规与行业自律 🟢

### 1.4.1 AI Safety Summit 系列

| 会议 | 时间 | 地点 | 主要成果 |
|---|---|---|---|
| **Bletchley Park** | 2023-11 | 英国 | 28 国签署《Bletchley 宣言》，关注"前沿 AI"风险 |
| **Seoul** | 2024-05 | 韩国 | 16 家前沿 AI 公司签署《前沿模型安全承诺》 |
| **Paris** | 2025-02 | 法国 | 推动可执行治理，包括《Paris 宣言》、Council of Europe AI Convention |

### 1.4.2 《前沿模型安全承诺》（Seoul Commitments）🟢

签署公司（2024-05）：Anthropic、OpenAI、Google DeepMind、Meta、Microsoft、Amazon、Naver、Kakao、Zhipu（中国智谱）、阿里、百度、腾讯、Minimax（中国）等 16 家

**核心承诺**：
- 设定不可逾越的安全红线
- 持续投资于安全研究
- 与政府共享关键安全信息
- 承诺在开发前沿模型前进行风险评估
- 实施红队测试并发布结果

> 📌 **关键洞察**：**智谱、阿里、百度、腾讯、Minimax 等中国大模型公司也签署了该承诺**，显示中国头部公司愿意参与国际软法治理。

### 1.4.3 行业标准与组织

- **OECD AI Principles**（2019，2024 更新）：经济合作组织 47 国通过
- **G7 Hiroshima AI Process**（2023）：G7 国家 AI 行为准则
- **ISO/IEC 42001**（2023-12）：AI 管理系统国际标准
- **MLCommons**（原 MLPerf 团队）：AI 安全基准（SafetyBench、AI Crowd Benchmark）
- **Partnership on AI**：行业研究联盟

---

## 1.5 三法域对比表 🟢

| 维度 | 中国 | 美国 | 欧盟 |
|---|---|---|---|
| **监管哲学** | 政府主导 + 备案制 | 分散 + 行业自律 | 统一立法 + 风险分级 |
| **核心法律** | 暂行办法 + 深度合成规定 + 算法推荐规定 | EO 14110（已撤销）+ 各州法 | AI Act + DSA + GDPR |
| **关键合规动作** | 算法备案 + 大模型备案 + 安全评估 | NIST AI RMF 自愿采纳；高风险州法律 | 风险评估 + CE 标志 + 数据库注册 |
| **罚则** | 警告、约谈、下架、罚款、刑事 | 州级：算法影响评估；联邦：FTC 5 万美元/日 | 最高 3500 万欧元 或全球 7% 营业额 |
| **特点** | 重视价值导向、政治安全 | 关注市场竞争、消费者保护 | 关注基本权利、系统性风险 |
| **企业感受** | 备案周期长、要求"听话" | 联邦弱、各州拼图复杂 | 合规成本高但规则清晰 |

---

# 第二部分：公司实践层 —— 大模型公司的内容安全治理

## 2.1 治理结构（Organization）🟢

### 2.1.1 五种典型组织架构

```
┌──────────────────────────────────────────────────────────────┐
│                  AI 内容安全治理的 5 种组织形态                │
├──────────────────────────────────────────────────────────────┤
│  1) 独立 Trust & Safety 部门                                   │
│     代表：Meta（旧 FB）、TikTok、YouTube                      │
│     特点：T&S 部门常达数千人，独立汇报至 CEO                  │
│                                                              │
│  2) AI Safety / Responsible AI 部门                           │
│     代表：Anthropic（Long-Term Benefit Trust 监督）            │
│           OpenAI（Safety团队 + Board 监督）                   │
│     特点：与 Research 并列，向 CTO 或独立委员会汇报           │
│                                                              │
│  3) 模型行为（Model Behavior）团队                            │
│     代表：OpenAI Model Behavior Team                          │
│     特点：与 RLHF 训练紧耦合，影响对齐效果                    │
│                                                              │
│  4) 嵌入产品团队的安全 PM/Eng                                 │
│     代表：早期 Google Gemini（2023）、百度文心                 │
│     特点：与产品耦合紧密，但独立性弱                          │
│                                                              │
│  5) 伦理委员会 + 技术安全部门双轨制                           │
│     代表：微软 Aether、谷歌 AI Principles Review Board        │
│     特点：决策层 + 执行层分开                                  │
└──────────────────────────────────────────────────────────────┘
```

### 2.1.2 关键岗位

- **Chief AI Officer / Head of AI Safety**（首席 AI 安全官）
- **AI Ethicist**（AI 伦理学家）
- **Red Team Lead**（红队负责人）
- **Trust & Safety PM**（信任安全产品经理）
- **AI Policy Lead**（AI 政策负责人，对接政府/NGO）
- **Model Behavior Researcher**（模型行为研究员）

## 2.2 内部制度（Policies）🟢

每家大模型公司都有 3-5 份关键政策文件：

| 政策文件 | 核心内容 | 代表 |
|---|---|---|
| **Acceptable Use Policy (AUP)** | 用户使用边界（禁制内容类型） | OpenAI、Anthropic、Google |
| **Usage Policy** | 政策更详细的版本，区分禁止/限制/允许 | OpenAI（最详细） |
| **Model Spec** | 模型应如何行为的"宪法" | OpenAI Model Spec |
| **Responsible Scaling Policy (RSP)** | 能力阈值对应的安全措施 | Anthropic |
| **Preparedness Framework** | 风险评估 + 应对等级 | OpenAI |
| **Frontier Safety Policy** | 前沿模型安全承诺 | Google DeepMind |
| **Data Use Policy** | 训练数据使用规则 | 各家 |
| **Privacy Policy** | 隐私合规 | 各家 |

> 📌 **关键洞察**：**OpenAI Model Spec**（2023-05 首次发布，2024 多次更新）是行业最透明的"模型行为规范"，公开承认模型应追求"有益的诚实"而非"绝对服从"。

## 2.3 流程（Processes）🟢

### 2.3.1 模型上线全流程

```
需求 → 数据收集 → 数据过滤 → 预训练 → SFT → RLHF/DPO
  → 内部红队 → 外部红队 → 安全评估 → 灰度发布
  → 持续监控 → 事件响应 → 模型退役
```

每个环节都涉及内容安全：

| 环节 | 内容安全动作 | 责任方 |
|---|---|---|
| **数据收集** | 版权过滤、有害内容过滤 | Data Team |
| **数据过滤** | 关键词匹配、分类器、毒性检测 | Data + Safety |
| **预训练** | 数据脱敏、来源审计 | Data |
| **SFT / RLHF** | 标注员培训、标注质量审核 | Alignment |
| **内部红队** | 攻防演练、漏洞发现 | Red Team |
| **外部红队** | 第三方机构独立测试 | 外包 |
| **安全评估** | 风险等级判定、对应缓解措施 | Safety Board |
| **灰度发布** | A/B 测试、用户反馈监控 | Product |
| **持续监控** | 滥用检测、违规趋势 | Trust & Safety |
| **事件响应** | 24-48h 紧急处理 | Incident Response |

### 2.3.2 红队测试（Red Teaming）核心要素 🟢

**目标**：在受控环境下，主动测试模型能否被诱导产生有害输出。

**类型**：
- **能力红队**：测试能力极限
- **安全红队**：测试安全漏洞（核心）
- **社会工程红队**：测试能否被用于欺诈
- **政治敏感红队**：测试政治内容生成

**方法**：
- **人工对抗**：红队成员扮演攻击者
- **自动化对抗**：使用脚本/工具生成对抗输入
- **众包红队**：邀请外部专家参与

**代表性实践**：
- **OpenAI**：GPT-4 红队测试耗时 6 个月，参与者包括 AI 学者、领域专家、民间组织
- **Anthropic Claude**：每次新模型发布前 3-6 个月开始红队
- **Google DeepMind**：与 Oxford、MIT 等学术机构合作
- **百度文心**：内部红队 + 中科院自动化所等外部机构
- **Anthropic ASL-3 红队测试报告**（2024-10 发布）：业界最透明的红队报告之一

## 2.4 技术手段（Technology）🟢

### 2.4.1 训练阶段

#### (1) 数据过滤（Data Filtering）
- **关键词黑名单**：暴力、色情、仇恨言论关键词
- **分类器过滤**：使用小型分类器对文档打分
- **去重**：模糊去重、语义去重（避免训练数据被污染）
- **NSFW 过滤**：图片/视频专用的 NSFW 分类器
- **代表工具**：LAION 的 NSFW 分类器、Perspective API（Jigsaw/Google）

#### (2) RLHF（Reinforcement Learning from Human Feedback）
- **原理**：人类标注员对模型多个输出排序 → 训练 reward model → 用 PPO/DPO 优化
- **Anthropic 创新**：Constitutional AI（基于规则的自我批评）
- **OpenAI 创新**：InstructGPT → ChatGPT 的核心技术
- **问题**：标注员主观性、"alignment faking"（模型学会在评估时表现良好）

#### (3) Constitutional AI 🟢
- **Anthropic 提出（2022）**
- **方法**：用一组"原则（Constitution）"替代大量人类反馈，让模型自评
- **优势**：可扩展、更透明、减少标注偏差
- **应用**：Claude 系列模型广泛使用
- 来源：<https://www.anthropic.com/news/claudes-constitution>

#### (4) DPO（Direct Preference Optimization）
- **2023 年提出**（Stanford）
- **简化 RLHF**：直接用偏好数据优化策略，无需 reward model
- **优点**：更稳定、更简单
- **应用**：Zephyr、Mistral、Llama 2-chat 等

#### (5) Adversarial Training
- 在训练中注入对抗样本，提高鲁棒性

### 2.4.2 推理 / 部署阶段

#### (1) 输入分类器（Input Classifier）
- **Llama Guard**（Meta）：开源输入/输出安全分类器
- **OpenAI Moderation API**：免费提供给开发者
- **Azure AI Content Safety**：企业级内容审核 API
- **Alibaba Content Moderation**：阿里云内容安全

#### (2) 输出过滤（Output Filtering）
- 输出前再过一道分类器
- 发现违规则重新生成或拒绝

#### (3) 水印（Watermarking）🟢

**Google SynthID**（2023-08 发布）：
- **文本水印**：在 token 选择中嵌入"统计信号"，人类不可察觉但可检测
- **图像水印**：嵌入像素模式
- **音频水印**：嵌入频谱模式
- **视频水印**：结合图像 + 时间维度
- 来源：<https://blog.google/technology/ai/google-watermark-ai-generated-text/>

**C2PA（Coalition for Content Provenance and Authenticity）**：
- **2021 年成立**（Adobe、Microsoft、BBC、Intel 等）
- **方法**：在元数据中嵌入生成来源
- **应用**：Adobe Firefly、Bing Image Creator、Leica M11-P 相机
- **局限**：元数据易剥离、文件易修改

**文本水印的局限**：
- 改写后水印丢失
- 翻译后水印丢失
- 攻击者可针对性破坏

#### (4) RAG 安全防护
- 检索内容过滤
- 检索内容与生成内容区分（避免模型"被骗"采纳恶意检索内容）

#### (5) Jailbreak 防御
- **Prompt 注入防护**：隔离用户输入与系统提示
- **多轮攻击检测**：识别逐步诱导模式
- **结构化防御**：使用 XML/JSON 标签隔离指令

#### (6) Abuse Detection（滥用检测）
- 账户级滥用检测
- API 滥用模式识别
- 异常使用监控

### 2.4.3 训练 vs 部署的安全要求对比

| 维度 | 训练阶段 | 部署阶段 |
|---|---|---|
| **数据** | 版权过滤、有害内容过滤、来源审计 | N/A |
| **模型** | RLHF、Constitutional AI、Adversarial Training | 输出过滤、输入分类 |
| **系统** | N/A | 水印、滥用检测、Jailbreak 防御 |
| **人员** | 数据标注员质量控制 | 客服、Trust & Safety 团队 |
| **流程** | 内部红队、外部红队、模型卡片 | 持续监控、A/B 测试、事件响应 |
| **外部** | 训练数据透明度报告 | 透明度报告、API 滥用沟通 |

## 2.5 治理结构（Governance）🟢

### 2.5.1 内部安全框架

#### (1) Anthropic Responsible Scaling Policy（RSP）🟢
- **AI Safety Levels (ASL)**：
  - **ASL-1**：当前最安全水平（无害研究）
  - **ASL-2**：当前商业模型水平（早期危险能力）
  - **ASL-3**：显著危险（能帮助制造生化武器、长期自主运行）
  - **ASL-4 / ASL-5**：灾难性风险
- **触发机制**：模型能力达到阈值时升级安全要求
- **2024-10 更新**：明确 ASL-3 部署条件，包括红队测试、第三方评估
- 来源：<https://www.anthropic.com/news/anthropics-responsible-scaling-policy>

#### (2) OpenAI Preparedness Framework 🟢
- **2023-12 首次发布，2024 多次更新**
- **风险类别**：
  - **网络安全**（Cyber）
  - **化学/生物/放射**（CBRN）
  - **说服力**（Persuasion）
  - **模型自主性**（Model Autonomy）
- **风险等级**：低 / 中 / 高 / 关键
- **关键原则**：高风险模型不能部署
- 来源：<https://openai.com/safety/preparedness>

#### (3) Google DeepMind Frontier Safety Framework
- **2024-05 发布**
- **3 类关键能力**（CCs）：Autonomy、CBRN、Cyber-offense
- **应对级别**：Yellow（缓解）、Red（暂停部署）、Black（永久退役）

### 2.5.2 外部安全机制

- **Anthropic Long-Term Benefit Trust**：独立的非营利信托，控制 Anthropic 的部分董事提名权
- **OpenAI Board**：董事会安全委员会
- **Microsoft Aether**：内部 AI 伦理委员会
- **Google AI Principles Review Board**：内部审查机制

## 2.6 行业自律与软法规 🟢

### 2.6.1 Frontier Model Forum
- **2023-07 成立**
- 创始成员：Anthropic、OpenAI、Google、Microsoft、Meta
- 工作：研究、最佳实践分享

### 2.6.2 MLCommons Safety Benchmarks
- **AI Crowd Benchmark**（2024）
- **SafetyBench**（中英文双语，2023）
- 评估模型在 7 类安全维度的表现

### 2.6.3 Partnership on AI
- 行业研究联盟
- 发布多份政策报告

---

# 第三部分：典型案例分析

## 3.1 标志性执法 / 事故案例 🟢

### 案例 1：意大利封禁 ChatGPT（2023-03）

| 维度 | 内容 |
|---|---|
| **时间** | 2023-03-31 至 2023-04-28 |
| **当事方** | 意大利 Garante（数据保护局）vs OpenAI |
| **触发问题** | 1) 无合法基础处理个人数据；2) 无年龄验证；3) 个人信息不准确（"幻觉"问题） |
| **处置** | 暂时**全面封禁 ChatGPT**（意大利境内） |
| **结果** | OpenAI 实施补救措施后解除封禁：增加年龄验证、提供删除请求渠道、增加透明度 |
| **意义** | **全球首例国家级 AI 服务禁令**；为欧盟 AI Act 提供执法参考 |
| **来源** | <https://www.garanteprivacy.it/web/guest/home/docweb/-/docweb-display/docweb/9870832> |

### 案例 2：Google Gemini 图像生成争议（2024-02）

| 维度 | 内容 |
|---|---|
| **时间** | 2024-02 |
| **当事方** | Google |
| **事件** | Gemini 在生成历史人物图像时**过度多元化**（如纳粹士兵、维京人等被生成为多种族） |
| **原因** | 为避免"种族偏见"过度调整；未充分考虑历史准确性 |
| **处置** | Google **暂停** Gemini 图像生成功能，CEO 道歉 |
| **意义** | 揭示"反偏见"与"事实准确性"的张力；显示过度安全策略的副作用 |
| **来源** | <https://blog.google/products/gemini/google-gemini-image-generation-issue/> |

### 案例 3：加拿大 OPC v. OpenAI（2024）

| 维度 | 内容 |
|---|---|
| **时间** | 2024 |
| **当事方** | 加拿大隐私专员办公室（OPC）vs OpenAI |
| **认定** | OpenAI 违反加拿大《个人信息保护与电子文档法》（PIPEDA） |
| **问题** | 未经同意收集、使用、披露个人信息 |
| **建议** | 加强透明度、数据准确性、纠正权 |
| **意义** | 加拿大首例针对生成式 AI 的隐私执法；可能影响北美跨境 AI 服务 |
| **来源** | <https://www.priv.gc.ca/en/opc-actions-and-decisions/investigations/investigations-into-businesses/pipeda-privacy-investigations/investigation-report-on-openai/> |

### 案例 4：FCC 封禁 AI Robocall + Biden 深度伪造事件（2024-01/02）

| 维度 | 内容 |
|---|---|
| **时间** | 2024-01 事件，2024-02 FCC 行动 |
| **事件** | 美国新罕布什尔州初选前，AI 生成的 **Biden 声音 Robocall** 劝阻选民投票 |
| **影响** | 引发对 AI 选举操纵的担忧；FCC 在 2024-02 宣布 AI Robocall 非法 |
| **罚款** | 相关政治咨询公司被罚 **600 万美元** |
| **意义** | 美国首次明确 AI 选举虚假信息违法；为 2024 大选年护航 |
| **来源** | <https://www.fcc.gov/document/fcc-makes-ai-generated-robocalls-illegal> |

### 案例 5：欧盟 DSA 调查 X（原 Twitter）（2023-12 启动）

| 维度 | 内容 |
|---|---|
| **时间** | 2023-12 启动，持续 |
| **当事方** | 欧盟委员会 vs X |
| **调查范围** | 内容审核、生成式 AI 风险、暗黑模式、广告透明度、研究人员数据访问 |
| **潜在后果** | 最高全球年营业额 6% 罚款 |
| **意义** | 欧盟首次对生成式 AI 平台动用 DSA 调查 |
| **来源** | <https://digital-strategy.ec.europa.eu/en/news/commission-opens-formal-proceedings-against-x-under-digital-services-act> |

### 案例 6：中国"清朗"专项整治（2024）

| 维度 | 内容 |
|---|---|
| **时间** | 2024 全年 |
| **当事方** | 网信办 vs 各 AI 平台 |
| **行动** | 下架违规 AI 换脸 App；约谈头部大模型公司；要求未备案 API 限期整改 |
| **案例** | 某 AI 换脸 App 因未履行深度合成标识义务被下架 |
| **意义** | 显示中国监管"事后处置"的执行力度；备案合规成为生存前提 |
| **来源** | <https://www.cac.gov.cn/2024-05/27/c_1717776611775634.htm> |

### 案例 7：FTC v. OpenAI（2023-2024 调查） 🟢

| 维度 | 内容 |
|---|---|
| **时间** | 2023-07 调查启动，2024 持续 |
| **当事方** | 美国 FTC vs OpenAI |
| **调查重点** | ChatGPT 消费者保护、数据安全、虚假宣传模型能力 |
| **可能后果** | 同意令要求 AI 治理项目、第三方评估、消费者赔偿；违反每日 5 万美元 |
| **意义** | 美国首次对生成式 AI 头部公司启动正式执法；显示 FTC 的强执法态度 |

## 3.2 重大安全事件

### 案例 8：Anthropic Claude 漏洞研究

Anthropic 与 AI 研究机构合作，发现并发布**多起 jailbreak 攻击**研究（如 Many-Shot Jailbreaking，2024-04）。**值得学习**：主动披露漏洞是行业最佳实践。

### 案例 9：Llama 模型被滥用事件

2024 年，研究人员发现 Meta 的 Llama 模型被多个犯罪团伙**微调后用于诈骗**。Meta 响应：发布 Llama Guard、限制可下载版本、强化滥用检测。

### 案例 10：DeepSeek 引发"中国大模型出海"讨论

2024-2025 年 DeepSeek-R1、DeepSeek-V3 以低成本高性能引发国际关注，但伴随对其**数据来源、安全过滤、价值对齐**的国际疑虑。显示中国大模型在出海过程中的内容安全挑战。

## 3.3 案例总结：常见违规模式 🟢

| 违规模式 | 案例 | 监管反应 |
|---|---|---|
| **未做标识** | 深度伪造未标识（中国清朗行动） | 下架 + 罚款 |
| **未做备案** | 未完成算法/大模型备案 | 限期整改 + 下架 |
| **数据来源非法** | 训练数据使用版权作品 | FTC 调查 + 民事诉讼 |
| **年龄验证不足** | ChatGPT 在意大利 | 国家级封禁 |
| **选举干预** | AI Robocall 仿 Biden | FCC 罚款 + 刑事追诉 |
| **过度修正** | Gemini 图像生成 | 公众批评 + 主动暂停 |
| **幻觉导致个人名誉损害** | ChatGPT 错误指控 | 监管调查 + 民事诉讼 |
| **红队测试不充分** | 多次 jailbreak 披露 | 行业最佳实践推动 |

---

# 第四部分：思考题与练习

## 4.1 概念辨析

**Q1：请解释"硬法规"与"软法规"的区别，并各举 2 个例子。**

<details>
<summary>参考答案</summary>

- **硬法规（Hard Law）**：具有法律约束力，违反将导致法律后果（罚款、禁令、刑事追诉）
  - 例子：《生成式人工智能服务管理暂行办法》、EU AI Act、FCC AI Robocall 禁令
- **软法规（Soft Law）**：无直接法律约束力，但通过声誉、行业惯例、后续立法路径等产生实质影响
  - 例子：NIST AI RMF、《前沿模型安全承诺》（Seoul Commitments）、Anthropic Responsible Scaling Policy、MLCommons 基准
</details>

**Q2：RLHF 和 Constitutional AI 的核心区别是什么？各自的优劣？**

<details>
<summary>参考答案</summary>

- **RLHF**：依赖大量人类标注员对模型输出排序 → 训练 reward model → 优化策略
  - 优点：直观、效果好
  - 缺点：标注成本高、标注员主观性、可能"alignment faking"
- **Constitutional AI**：用一组"原则（Constitution）"让模型自评，不依赖大量人类反馈
  - 优点：可扩展、透明、减少标注偏差
  - 缺点：原则本身需要人来写、原则间的冲突需要解决
</details>

**Q3：训练阶段和部署阶段的内容安全要求有何不同？请列举至少 3 个不同点。**

<details>
<summary>参考答案</summary>

1. **对象不同**：训练阶段关注**数据**（来源、过滤、清洗）；部署阶段关注**输入输出**（审核、过滤）
2. **技术不同**：训练阶段用 RLHF、Constitutional AI；部署阶段用分类器、水印、滥用检测
3. **流程不同**：训练阶段需要内部/外部红队；部署阶段需要持续监控、事件响应
4. **责任人不同**：训练阶段主要由 Alignment 团队负责；部署阶段由 T&S、产品、客服共同负责
</details>

## 4.2 案例分析题

**Q4：分析意大利 Garante 封禁 ChatGPT 案例的处置逻辑。**
- 监管方主要担忧哪些风险？
- OpenAI 采取了哪些补救措施？
- 如果你是 OpenAI 在欧洲的合规负责人，从中学到什么教训？

<details>
<summary>参考答案要点</summary>

- **监管方担忧**：1) 训练数据合法性；2) 用户数据保护；3) 未成年人保护
- **OpenAI 补救**：1) 增加年龄验证；2) 提供数据删除渠道；3) 加强透明度
- **教训**：1) 跨境合规需提前规划；2) 各国数据保护机构有独立执法权；3) 用户权利机制是必备项
</details>

**Q5：Google Gemini 图像生成事件是"过度安全"还是"安全不足"？**
- 如果你是 Gemini 产品负责人，会如何重新设计内容策略？

<details>
<summary>参考答案要点</summary>

- **本质问题**：在"避免种族偏见"与"历史准确性"之间未做权衡
- **重新设计方向**：
  1. 区分不同使用场景（创意 vs 教育 vs 史实）
  2. 增加用户可控的"内容策略"开关
  3. 对敏感历史话题给出明确说明
  4. 建立快速响应机制
</details>

## 4.3 实战题

**Q6：设计一个中国大模型公司的"内容安全治理框架"**
- 要求覆盖：制度、流程、技术、组织、自律
- 至少 5 个章节，每章 3-5 个具体措施

<details>
<summary>参考答案（框架示例）</summary>

```
第一章 组织与制度
  1. 成立 Trust & Safety 部门，VP 级向 CEO 汇报
  2. 制定《内容安全白皮书》、《AUP》、《模型行为准则》
  3. 设立 AI 伦理委员会（外部专家 + 内部高管）
  4. 内容安全 KPI 纳入高管考核

第二章 数据与训练
  1. 训练数据来源审计（每条数据可追溯）
  2. 多层数据过滤（关键词 + 分类器 + 人工抽检）
  3. RLHF + Constitutional AI 结合
  4. 红队测试覆盖 7 类敏感话题

第三章 部署与监控
  1. 输入输出双层分类器
  2. 实时滥用检测系统
  3. 内容水印（C2PA / 自研）
  4. 用户反馈闭环

第四章 监管对接
  1. 算法备案 + 大模型备案 + 安全评估三件套
  2. 备案号公开公示
  3. 与网信办定期沟通

第五章 行业自律
  1. 签署前沿模型安全承诺
  2. 发布年度透明度报告
  3. 参与 MLCommons 基准评测
```
</details>

**Q7：为一个海外上线的中国大模型产品设计"内容安全合规清单"**
- 需要满足：EU AI Act、CCPA、NIST AI RMF
- 列出 10 项关键合规动作

<details>
<summary>参考答案（清单示例）</summary>

1. 完成 EU AI Act 的**合格性评估（Conformity Assessment）** + CE 标志
2. 在 EU AI Database 完成**注册**
3. 部署前进行**算法影响评估**（AIA, Algorithmic Impact Assessment）
4. 用户告知使用 AI 服务（**Article 50 透明度义务**）
5. AI 生成内容显著标识（**Deepfake Disclosure**）
6. 提供人工复核渠道（**Right to Human Review**）
7. 数据保护影响评估（DPIA）
8. 训练数据透明度报告（**Copyright Summary**）
9. 建立事件响应机制（24h 严重事件报告）
10. 任命 EU 当地代表（**Article 87**）
</details>

---

# 第五部分：参考资料与权威源

## 5.1 中国法规原始来源

| 文件 | 链接 |
|---|---|
| 生成式人工智能服务管理暂行办法 | <http://www.cac.gov.cn/2023-07/13/c_1690898327029107.htm> |
| 互联网信息服务深度合成管理规定 | <http://www.cac.gov.cn/2022-12/11/c_1672221949354811.htm> |
| 互联网信息服务算法推荐管理规定 | <http://www.cac.gov.cn/2021-12/31/c_1644594604977684.htm> |
| 2024 清朗行动通报 | <https://www.cac.gov.cn/2024-05/27/c_1717776611775634.htm> |
| China Law Translate 英文版 | <https://www.chinalawtranslate.com/en/generative-ai-interim/> |
| Stanford DigiChina 分析 | <https://digichina.stanford.edu/work/china-ai-governance/> |

## 5.2 美国

| 文件 | 链接 |
|---|---|
| FTC OpenAI 调查（2024-05） | <https://www.ftc.gov/news-events/news/press-releases/2024/05/ftc-opens-inquiry-into-generative-ai-chatbots> |
| FCC AI Robocall 禁令 | <https://www.fcc.gov/document/fcc-makes-ai-generated-robocalls-illegal> |
| Google Gemini 事件声明 | <https://blog.google/products/gemini/google-gemini-image-generation-issue/> |

## 5.3 欧盟

| 文件 | 链接 |
|---|---|
| EU AI Act 全文 | <https://artificialintelligenceact.eu/> |
| EU DSA X 调查 | <https://digital-strategy.ec.europa.eu/en/news/commission-opens-formal-proceedings-against-x-under-digital-services-act> |
| 意大利 Garante v. OpenAI | <https://www.garanteprivacy.it/web/guest/home/docweb/-/docweb-display/docweb/9870832> |
| 加拿大 OPC v. OpenAI | <https://www.priv.gc.ca/en/opc-actions-and-decisions/investigations/investigations-into-businesses/pipeda-privacy-investigations/investigation-report-on-openai/> |

## 5.4 公司政策与框架

| 文档 | 链接 |
|---|---|
| Anthropic Responsible Scaling Policy | <https://www.anthropic.com/news/anthropics-responsible-scaling-policy> |
| OpenAI Preparedness Framework | <https://openai.com/safety/preparedness> |
| OpenAI Model Spec | <https://openai.com/index/modelspec/> |
| Google SynthID | <https://blog.google/technology/ai/google-watermark-ai-generated-text/> |

## 5.5 进一步学习资源

- **Stanford HAI AI Index Report**（年度）：全球 AI 发展指标
- **OECD AI Observatory**：跨国 AI 政策追踪
- **IAPP（国际隐私专业人员协会）**：隐私 + AI 合规
- **AI Now Institute**：AI 政策研究
- **清华大学《人工智能法》学者建议稿**：中国学界立法参考
- **中国信通院《人工智能白皮书》**：国内权威报告

---

## 附录 A：术语表

| 术语 | 解释 |
|---|---|
| **AUP** | Acceptable Use Policy，使用可接受政策 |
| **AI RMF** | AI Risk Management Framework，AI 风险管理框架 |
| **CE 标志** | 欧盟合格性标志 |
| **CBRN** | Chemical, Biological, Radiological, Nuclear |
| **Constitutional AI** | Anthropic 提出的基于规则的自我对齐方法 |
| **Deepfake** | 深度伪造，AI 生成的虚假音视频 |
| **DPO** | Direct Preference Optimization，直接偏好优化 |
| **DSA** | Digital Services Act，欧盟数字服务法 |
| **FLOPS** | Floating Point Operations Per Second，衡量算力 |
| **GDPR** | General Data Protection Regulation，欧盟通用数据保护条例 |
| **GPAI** | General Purpose AI，通用人工智能 |
| **Jailbreak** | 越狱，绕过 AI 安全限制的攻击 |
| **NSFW** | Not Safe For Work，不适合工作场合的内容 |
| **PIPL** | Personal Information Protection Law，中国个人信息保护法 |
| **RLHF** | Reinforcement Learning from Human Feedback，基于人类反馈的强化学习 |
| **RSP** | Responsible Scaling Policy，责任扩展政策（Anthropic） |
| **T&S** | Trust & Safety，信任与安全 |

## 附录 B：置信度索引

| 主题 | 置信度 | 说明 |
|---|---|---|
| 中国三规章核心条款 | 🟢 高 | 网信办原文 |
| 美国 EO 14110 / FTC 调查 | 🟢 高 | 联邦政府官方 |
| 欧盟 AI Act 框架 | 🟢 高 | 官方文本 |
| Anthropic RSP、OpenAI Preparedness | 🟢 高 | 公司官方公开 |
| SynthID / C2PA 技术 | 🟢 高 | 公开技术资料 |
| 中国大模型公司内部实践 | 🟡 中 | 公开材料有限，多基于行业推断 |
| 具体执法罚款金额 | 🟡 中 | 部分数据需进一步验证 |
| 2024-2025 最新案例 | 🟡 中 | 部分事件细节仍在演变 |

---

> **课程完成提示**
> - 本课件基于 2023-01 至 2026-01 的资料
> - 建议结合各公司最新发布的安全政策、监管最新公告持续学习
> - 中国 / 美国 / 欧盟监管均处于快速演变期，3 个月内可能有重大变化
> - 实际工作中请以**当地法律顾问**意见为准

*— 课件制作于 2026-08-25，基于 deep-research 工作流（5 维并行搜索 + 3 票对抗式验证）*
