# 🧠 Brainstorm Skill

> 自动化脑暴系统 — 让创意源源不断

一个为 [OpenClaw](https://openclaw.ai) 设计的 Skill，通过多 Agent 协作，自动收集热点信息、生成创意、评估筛选，输出结构化创意报告。

---

## ✨ 功能亮点

- 🔥 **热点感知** — 自动抓取微博、知乎、抖音、B站等平台热点
- 💡 **创意生成** — 跨领域碰撞、问题驱动、趋势延伸等多种方法
- 📊 **自动评估** — 可行性 × 市场潜力 × 创新度三维打分
- 📅 **定时触发** — 每日 9:00 自动脑暴，每周一深度研究
- 🚨 **热点突发** — 热度超阈值自动触发临时脑暴
- 📋 **结构化输出** — 创意分级（S/A/B/C）+ 每日/周报

---

## 🚀 快速开始

### 安装

```bash
# 通过 ClawHub 安装（推荐）
clawhub install brainstorm

# 或手动复制 SKILL.md 到你的 skills 目录
```

### 使用

```bash
# 快速脑暴
brainstorm quick --topic "AI+教育"

# 标准脑暴（30分钟）
brainstorm start --topic "新能源出行"

# 深度脑暴（2小时）
brainstorm deep --topic "量子计算应用"

# 查看今日成果
brainstorm today

# 查看本周 Top 10
brainstorm top --period week --limit 10
```

---

## 🏗️ 工作流程

```
触发（定时 / 手动 / 热点事件）
        ↓
Brainstorm Manager 接收指令
        ↓
并行信息收集（热点 + 热梗 + 科技动态）
        ↓
Idea Catalyst 交叉碰撞 → 生成创意
        ↓
评估筛选 → S/A/B/C 分级
        ↓
输出报告 + 飞书通知
```

---

## 📁 输出文件

| 文件 | 说明 |
|------|------|
| `memory/brainstorm/reports/YYYY-MM-DD.md` | 每日脑暴报告 |
| `memory/brainstorm/ideas-pool.md` | 创意池（持续累积）|

---

## 📦 依赖

- [OpenClaw](https://openclaw.ai) >= 1.0
- 飞书 Skill（用于通知推送）

---

## 🤝 适用场景

- 产品创意孵化
- 内容选题生成
- 市场机会发现
- 竞品差异化分析

---

## 📄 License

MIT © [wss](https://github.com/2657193522w-bit)
