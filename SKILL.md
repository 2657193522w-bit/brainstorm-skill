---
name: brainstorm
description: Brainstorm Squad 自动化脑暴系统。支持定时/手动/事件触发，多 Agent 协作生成创意，自动评估筛选，输出结构化报告。
---

# Brainstorm Skill 🧠

自动化脑暴系统，让创意源源不断。

## 快速开始

### 启动脑暴

```bash
# 每日自动脑暴（定时触发）
brainstorm start

# 指定主题脑暴
brainstorm start --topic "AI+教育" --duration 30min

# 快速脑暴
brainstorm quick --topic "新能源"

# 深度脑暴
brainstorm deep --topic "量子计算应用" --duration 2h
```

### 查看成果

```bash
# 今日创意
brainstorm today

# 本周 Top 10
brainstorm top --period week --limit 10

# 创意池
brainstorm pool

# 查看报告
brainstorm report --date 2026-03-12
```

## 命令参考

### 脑暴命令

| 命令 | 说明 | 示例 |
|------|------|------|
| `start` | 启动脑暴 | `brainstorm start --topic "AI+医疗"` |
| `quick` | 快速脑暴（15分钟） | `brainstorm quick --topic "区块链"` |
| `deep` | 深度脑暴（2小时） | `brainstorm deep --topic "元宇宙"` |
| `collect` | 仅收集信息 | `brainstorm collect --source hot` |
| `generate` | 仅生成创意 | `brainstorm generate --method cross` |
| `evaluate` | 评估创意 | `brainstorm evaluate --idea-id idea-001` |

### 查询命令

| 命令 | 说明 | 示例 |
|------|------|------|
| `today` | 今日成果 | `brainstorm today` |
| `top` | Top 创意 | `brainstorm top --period week` |
| `pool` | 创意池 | `brainstorm pool --filter S` |
| `report` | 查看报告 | `brainstorm report --date 2026-03-12` |
| `status` | 查看状态 | `brainstorm status` |

### 管理命令

| 命令 | 说明 | 示例 |
|------|------|------|
| `schedule` | 设置定时 | `brainstorm schedule --enable --time 09:00` |
| `config` | 查看配置 | `brainstorm config` |
| `archive` | 归档旧创意 | `brainstorm archive --before 2026-01-01` |

## 自动化机制

### 1. 定时触发（Cron）

```yaml
# brainstorm.yaml
automation:
  schedule:
    daily:
      enabled: true
      cron: "0 9 * * *"  # 每天 9:00
      duration: "30min"
      topic: "auto"      # 自动检测热点
    
    weekly:
      enabled: true
      cron: "0 9 * * 1"  # 每周一 9:00
      duration: "2h"
      topic: "deep"      # 深度研究
```

### 2. 热点突发触发

```yaml
automation:
  hot_trigger:
    enabled: true
    threshold: 8        # 热度超过 8 分
    platforms:
      - weibo
      - zhihu
      - douyin
    cooldown: "2h"      # 冷却时间，避免频繁触发
```

### 3. 事件驱动触发

```yaml
automation:
  event_trigger:
    - type: "mention"
      pattern: "@brainstorm_manager"
      action: "start_quick"
    
    - type: "keyword"
      pattern: "脑暴|创意|想法"
      action: "suggest_topic"
```

## 工作流程

```
┌─────────────────────────────────────────────────────────┐
│  触发机制（定时/手动/事件）                                 │
└─────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│  Brainstorm Manager 接收指令                              │
│  - 解析主题和参数                                         │
│  - 确定脑暴类型（快速/标准/深度）                          │
└─────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│  信息收集阶段（并行执行）                                   │
│  ├─ Trend Hunter → 抓取热点                              │
│  ├─ Meme Scout → 挖掘热梗                                │
│  └─ Tech Watcher → 监控科技                              │
└─────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│  创意生成阶段                                             │
│  Idea Catalyst ← 整合信息 → 交叉碰撞 → 产出创意            │
└─────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│  评估筛选阶段                                             │
│  Brainstorm Manager ← 评估可行性 → 筛选分级 → Top 排序     │
└─────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────┐
│  成果输出                                                 │
│  ├─ 保存报告：memory/brainstorm/reports/YYYY-MM-DD.md     │
│  ├─ 更新创意池：memory/brainstorm/ideas-pool.md           │
│  └─ 通知 Leo：飞书消息/文档                               │
└─────────────────────────────────────────────────────────┘
```

## 配置说明

### 完整配置示例

```yaml
# ~/.openclaw/brainstorm.yaml

team:
  name: "Brainstorm Squad"
  leader: "brainstorm_manager"
  members:
    - brainstorm_analyst
    - brainstorm_creative
    - brainstorm_security

# 信息源配置
sources:
  hot:
    weibo:
      url: "https://s.weibo.com/top/summary"
      enabled: true
    zhihu:
      url: "https://www.zhihu.com/hot"
      enabled: true
    douyin:
      url: "https://www.douyin.com/hot"
      enabled: true
    bilibili:
      url: "https://www.bilibili.com/v/popular/rank/all"
      enabled: true
  
  meme:
    douban:
      url: "https://www.douban.com/group/explore"
      enabled: true
    hupu:
      url: "https://bbs.hupu.com/all-gambia"
      enabled: true
    twitter:
      url: "https://twitter.com/explore/tabs/trending"
      enabled: true
  
  tech:
    producthunt:
      url: "https://www.producthunt.com"
      enabled: true
    github:
      url: "https://github.com/trending"
      enabled: true
    techcrunch:
      url: "https://techcrunch.com"
      enabled: true

# 创意生成方法
methods:
  - name: "cross_domain"
    enabled: true
    weight: 0.3
  - name: "problem_driven"
    enabled: true
    weight: 0.3
  - name: "trend_extension"
    enabled: true
    weight: 0.2
  - name: "reversal"
    enabled: true
    weight: 0.1
  - name: "extreme"
    enabled: true
    weight: 0.1

# 评估标准
evaluation:
  criteria:
    feasibility:
      weight: 0.3
      factors:
        - technical_difficulty
        - resource_requirement
        - time_cost
    
    market_potential:
      weight: 0.4
      factors:
        - target_user_size
        - willingness_to_pay
        - competition_intensity
    
    innovation:
      weight: 0.3
      factors:
        - differentiation
        - technical_barrier
        - moat

# 自动化配置
automation:
  enabled: true
  
  schedule:
    daily:
      enabled: true
      cron: "0 9 * * *"
      duration: "30min"
      topic: "auto"
    
    weekly:
      enabled: true
      cron: "0 9 * * 1"
      duration: "2h"
      topic: "deep"
  
  hot_trigger:
    enabled: true
    threshold: 8
    platforms:
      - weibo
      - zhihu
      - douyin
    cooldown: "2h"
  
  event_trigger:
    enabled: true
    triggers:
      - type: "mention"
        pattern: "@brainstorm_manager"

# 通知配置
notification:
  enabled: true
  channels:
    - feishu
  
  templates:
    daily:
      format: "brief"
      include_top: 3
    
    weekly:
      format: "full"
      include_all: true
    
    urgent:
      format: "alert"
      threshold: "S"

# 创意池管理
ideas_pool:
  location: "memory/brainstorm/ideas-pool.md"
  max_size: 1000
  auto_archive: true
  archive_after: "90d"
  
  categories:
    - name: "S"
      description: "立即实施"
      color: "red"
    - name: "A"
      description: "值得深入"
      color: "orange"
    - name: "B"
      description: "记录观察"
      color: "blue"
    - name: "C"
      description: "存档备用"
      color: "gray"

# 报告配置
reports:
  location: "memory/brainstorm/reports/"
  formats:
    - markdown
    - json
  retention: "1y"
  
  template: |
    # 脑暴报告 {date}
    
    ## 概览
    - 热点：{hot_count} 个
    - 热梗：{meme_count} 个
    - 科技：{tech_count} 个
    - 生成创意：{idea_count} 个
    
    ## Top {top_n} 创意
    {top_ideas}
    
    ## 详细清单
    {all_ideas}
    
    ## 待深入方向
    {todo_list}
```

## 输出示例

### 每日简报

```markdown
[脑暴日报] 2026-03-12 09:30
━━━━━━━━━━━━━━━━━━━━━
🔥 今日热点：3个 | 🎭 热梗：2个 | 🔭 科技：4个

💡 Top 3 创意：
1. 【AI虚拟伴侣】可行性 7/10 | 市场 9/10 | S级
   → 下一步：竞品调研
   
2. 【AI社交匹配】可行性 6/10 | 市场 8/10 | A级
   → 下一步：技术验证
   
3. 【AI话题生成器】可行性 8/10 | 市场 7/10 | A级
   → 下一步：MVP设计

📊 完整报告：memory/brainstorm/reports/2026-03-12.md
💬 回复"详情"查看完整清单
```

### 深度报告

```markdown
# 脑暴深度报告 AI+教育（2026-03-12）

## 信息概览
### 热点分析
...

### 热梗文化
...

### 科技动态
...

## 创意清单（15个）
### 创意 1：AI虚拟伴侣
...

## Top 5 推荐
...

## 待深入方向
...
```

## 与其他团队集成

```yaml
integration:
  content_team:
    trigger: "创意需要内容化"
    action: "通知 content_strategist"
  
  marketing_team:
    trigger: "发现增长机会"
    action: "通知 growth_lead"
  
  tech_team:
    trigger: "产品创意可实施"
    action: "通知 engineering_manager"
  
  finance_team:
    trigger: "创业机会"
    action: "通知 finance_manager"
```

## 故障排除

### 脑暴未自动启动

1. 检查自动化配置是否启用
2. 检查 Monitor Agent 是否正常运行
3. 检查 cron 配置是否正确

### 创意质量不高

1. 调整评估标准权重
2. 增加信息源覆盖
3. 调整创意生成方法权重

### 通知未收到

1. 检查飞书配置
2. 检查通知模板设置
3. 检查网络连接

## 最佳实践

1. **定期回顾**：每周回顾创意池，更新优先级
2. **快速验证**：S级创意立即安排调研
3. **跨界思维**：鼓励不同领域碰撞
4. **记录灵感**：随时记录突发灵感
5. **迭代优化**：根据反馈调整脑暴流程

---

*Version: 1.0.0*
*Created: 2026-03-12*
