# Hermes Agent — Product Delivery MVP Skill

一个面向 Hermes Agent 的产品交付自动化技能包。输入一句产品任务，自动完成：

```
需求澄清 → Product Brief → 产品方案 → 用户流程
→ 低保真可点击 HTML 原型 → 规则评审 → 双 Persona 模拟验收
→ [最多 2 轮自动修订] → 精简 PRD → 交付产品包
```

## 文件说明

| 文件 | 用途 |
|---|---|
| `SKILL.md` | 主技能文件，PM Orchestrator 核心规则 |
| `AGENT_PRODUCT.md` | Product Agent 角色规则 |
| `AGENT_UX.md` | UX + 原型 Agent 角色规则 |
| `AGENT_REVIEWER.md` | 独立 Reviewer Agent 角色规则 |
| `AGENT_PERSONA.md` | 模拟用户 Persona Agent 角色规则 |
| `project-template.yaml` | 项目状态模板，每个新任务复制一份 |
| `config.yaml` | Hermes Agent 角色与委派策略配置文件 |

## 安装方法

```bash
# 克隆到 Hermes 技能目录
git clone https://github.com/cy1380990555-gif/hermes-product-delivery-mvp.git \
  ~/.hermes/skills/product-delivery-mvp

# 重新加载技能
hermes skills reload
```

## 使用方法

安装后在配置完你的 `config.yaml` 之后，直接对 Hermes 说：

```
启动产品交付 MVP 流程。

任务：为【目标用户】设计【产品/功能】，解决【核心问题】。
约束：平台 / 范围 / 明确不做的内容。
```

触发关键词：帮我做产品需求、写 PRD、产品方案、做原型、用户流程

## 自循环机制

- **规则 Reviewer**：检查完整性、流程闭合、范围和追踪；
- **双 Persona 模拟**：主用户 + 异常用户直接操作 HTML 原型；
- **定向修订**：FAIL 后只修改受影响的产物，最多 2 轮；
- **硬退出**：同一问题连续 2 次未解决则停止并请求人工决策。

## 最终交付物

- `01-product-brief.md`
- `02-product-solution.md`
- `03-user-flow.md`
- `04-prototype.html`（可点击低保真原型）
- `05-lite-prd.md`
- `06-validation-report.md`
