# AI Content Safety and Governance 🛡️

> A structured, evidence-based research course on **AI content safety** covering regulations, corporate practices, technical methods, and governance across **China, the United States, and the European Union** (2023–2026).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Pages: 27](https://img.shields.io/badge/Pages-27-blue.svg)](#contents)
[![Language: Chinese](https://img.shields.io/badge/Lang-中文-red.svg)](#contents)
[![Year: 2026](https://img.shields.io/badge/Year-2026-green.svg)](#contents)

---

## 📖 About This Course

This repository contains a deep research report on **AI Content Safety (AI 内容安全)** prepared for practitioners, compliance officers, policy researchers, and AI product teams. It synthesizes:

- **Regulatory frameworks** across three major jurisdictions (China, US, EU)
- **Corporate practices** of leading LLM companies (OpenAI, Anthropic, Google, Baidu, Alibaba, ByteDance, etc.)
- **Technical methods** for both training-time and deployment-time safety
- **10+ real-world enforcement cases** and incidents
- **Practical exercises** and a self-study path

The course was produced using a **multi-agent deep-research workflow** (5 parallel search angles → adversarial verification → synthesis), with confidence ratings (🟢 High / 🟡 Medium / 🔴 Low) on every major claim.

---

## 📚 Contents

| File | Description |
|---|---|
| [`AI内容安全研究课件.md`](./AI内容安全研究课件.md) | **Main course material** (47 KB, 927 lines) — structured Markdown curriculum |
| [`AI内容安全研究课件.pdf`](./AI内容安全研究课件.pdf) | **PDF version** (262 KB, 27 pages, A4) — print-ready |
| [`LICENSE`](./LICENSE) | MIT License |
| [`README.md`](./README.md) | This file |

### Course Structure (5 Parts)

```
0. Learning Map & Objectives
1. Regulations — China | United States | European Union | Soft Law
2. Corporate Practices — Organization | Policies | Process | Technology | Governance
3. Case Studies — 10 real-world enforcement & incident cases
4. Exercises & Q&A — 7 questions (concept / case analysis / hands-on)
5. References — 20+ authoritative sources with direct links
Appendix — Glossary (17 terms) + Confidence Index
```

---

## 🎯 Learning Objectives

After completing this course, you will be able to:

1. ✅ Name the core hard laws on AI content safety in **China, the US, and the EU**, with key articles
2. ✅ Distinguish **"hard law"** (statutes, executive orders, regulations) from **"soft law"** (industry codes, corporate commitments)
3. ✅ Describe the **5 pillars** of LLM corporate content safety governance
4. ✅ Recap **5+ landmark enforcement/incident cases** and understand regulatory logic
5. ✅ Differentiate **training-time** vs. **inference/deployment-time** content safety requirements
6. ✅ Design a **basic content safety program** for a new model launch

---

## 🌍 Three-Jurisdiction Comparison at a Glance

| Dimension | 🇨🇳 China | 🇺🇸 United States | 🇪🇺 European Union |
|---|---|---|---|
| **Philosophy** | Government-led + Filing system | Decentralized + Industry self-regulation | Unified legislation + Risk-based tiers |
| **Core Law** | Generative AI Interim Measures (2023) | EO 14110 (revoked) + State laws | AI Act (2024) + DSA + GDPR |
| **Key Action** | Algorithm filing + Security assessment | NIST AI RMF (voluntary); state laws | Conformity assessment + CE mark |
| **Penalty** | Warnings, fines, takedowns | State-level; FTC: $50K/day | Up to €35M or 7% global turnover |
| **Focus** | Value alignment, political security | Market competition, consumer protection | Fundamental rights, systemic risk |

---

## 🏢 Company Practices Snapshot

| Company | Notable Initiative |
|---|---|
| **Anthropic** | Responsible Scaling Policy (RSP), AI Safety Levels (ASL-1 to ASL-5), Constitutional AI |
| **OpenAI** | Preparedness Framework, Model Spec, Red Team (6 months for GPT-4) |
| **Google DeepMind** | Frontier Safety Framework, SynthID watermarking |
| **Meta** | Llama Guard, AI Safety investments, Llama 3+ safety reports |
| **Microsoft** | Aether ethics committee, Azure AI Content Safety |
| **Baidu** (文心) | Algorithm + LLM dual filing, internal red team |
| **Alibaba** (通义) | Qwen safety reports, signed Seoul Commitments |
| **ByteDance** (豆包) | Large-scale Trust & Safety organization |

---

## 📌 Key Case Studies

1. **Italy's Garante v. OpenAI** (2023) — world's first national-level ban on ChatGPT
2. **Google Gemini image generation controversy** (2024) — over-correction vs. historical accuracy
3. **Canada OPC v. OpenAI** (2024) — first Canadian privacy ruling on generative AI
4. **FCC AI Robocall ban** (2024) — triggered by Biden deepfake robocall
5. **EU DSA investigation of X** (2023–) — first DSA probe of generative AI
6. **China "Qinglang" crackdown** (2024) — takedowns of unregistered AI services
7. **FTC v. OpenAI** (2023–) — US first major generative AI enforcement

---

## 🚀 How to Use This Course

### Self-Study Path (4-Week Plan)

```
Week 1: Read §1.1 (China) + §1.3 (EU AI Act)     → Hard law foundations
Week 2: Read §1.2 (US) + §1.4 (Soft law)           → Global landscape
Week 3: Read §2.1-2.3 (Org / Policies / Process)  → Corporate practices
Week 4: Read §2.4-2.6 (Tech / Governance / Self-regulation)
         + §3 (Case studies) + Do §4 (Exercises)
```

### For Corporate Training

- Suitable for: compliance teams, Trust & Safety onboarding, AI governance training
- Format options: Markdown (interactive), PDF (print/lecture slides)
- Each chapter is ~5-15 minutes read

### For Academic / Policy Research

- 20+ primary source links (gov.cn, EU Commission, FCC, FTC, etc.)
- Confidence ratings on all major claims
- 10+ case studies with verifiable events

---

## ⚠️ Limitations & Disclosure

1. **Network restrictions during research**: Some sources were unable to be fully verified through direct fetch due to enterprise network policies.
2. **Time sensitivity**: AI regulation is evolving rapidly. This course reflects the state of play as of **January 2026**. Some 2024-2025 details may have evolved.
3. **Not legal advice**: This is a research/educational resource. For actual compliance, consult qualified legal counsel in your jurisdiction.
4. **Coverage gaps**: While we focused on LLM/AI companies and 3 major jurisdictions, the course does not deeply cover: (a) financial / healthcare-specific AI regulations; (b) emerging market regulations; (c) industry-by-industry vertical analysis.

---

## 📖 Glossary Highlights

- **RLHF** — Reinforcement Learning from Human Feedback
- **Constitutional AI** — Anthropic's rule-based self-critique alignment method
- **DSP / DPO** — Direct Preference Optimization (Stanford, 2023)
- **C2PA** — Coalition for Content Provenance and Authenticity (content watermarking)
- **RSP / ASL** — Responsible Scaling Policy / AI Safety Levels (Anthropic)
- **DSA / GDPR** — EU Digital Services Act / General Data Protection Regulation
- **DPIA** — Data Protection Impact Assessment
- **FLOPS** — Floating Point Operations Per Second (compute metric)

*Full 17-term glossary in the course document.*

---

## 🤝 Contributing

Contributions are welcome! If you spot:

- A factual error or outdated claim → Open an issue
- A new enforcement case (post-Jan 2026) → Open a PR
- A new jurisdiction's regulation → Add to Part 1
- A new company practice → Add to Part 2
- Improved translations → Welcome

Please maintain the existing structure and confidence-rating convention.

---

## 📄 License

This course is released under the **MIT License**. You are free to:

- ✅ Use commercially
- ✅ Modify and redistribute
- ✅ Use in private projects

Under the conditions:

- 📋 Include the original copyright notice and license in any copy

See [`LICENSE`](./LICENSE) for the full text.

---

## 👤 Author & Acknowledgements

**Author**: Created via deep-research workflow using Claude (Anthropic), August 2026.

**Research methodology**:
- 5 parallel search angles (hard law / technical / Chinese companies / soft law / enforcement)
- Top-15 source fetch with URL deduplication
- 3-vote adversarial verification per claim (≥2/3 refutes to discard)
- Synthesis with confidence ratings

**Special thanks** to the open-source AI safety community and the public regulatory documents that made this research possible.

---

## 📮 Contact

For questions, corrections, or collaboration, please open a [GitHub Issue](../../issues) in this repository.

---

*Last updated: August 2026*
