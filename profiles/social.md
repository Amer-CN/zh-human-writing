# profiles/social.md
# zh-human-writing v1 — social profile

---

## 编辑目标

- 提升简洁度和平台适配性
- 保持品牌一致性和平台规范
- 减少模板化表达

---

## 重点保护项

| 保护项 | 说明 |
|--------|------|
| 品牌名称 | 逐字保护 |
| 产品名称 | 逐字保护 |
| 链接和标签 | 逐字保护 |
| 促销信息 | 逐字保护（数字、日期、折扣） |
| 平台特定格式 | 保留（# 标签、@ 提及） |
| emoji | 不得删除或替换（除非用户要求） |

---

## 允许的语气

- 口语化、轻松
- 互动性表达（社媒中的常态）
- 第二人称（社媒中的常态）
- 短句和碎片句（社媒中的常态）
- emoji 和表情符号（原文已有的）
- 网络用语和流行词（原文已有的）

---

## 合法但容易误判的表达

| 表达 | 误判原因 | 正确处理 |
|------|---------|---------|
| 第二人称"你" | 被当作假互动 | 社媒中二人称是常态 |
| 短句和碎片句 | 被当作断奏戏剧 | 社媒中短句是常态 |
| 反问句 | 被当作公式化挑战结构 | 社媒中反问是互动手段 |
| emoji 堆叠 | 被当作格式化痕迹 | 社媒中 emoji 是常态 |
| "先…再…" | 被当作阶段递进 | 社媒中的步骤说明是合法的 |
| 口语化表达 | 被当作填充短语 | 社媒中口语化是常态 |
| 网络用语 | 被当作非正式 | 社媒中网络用语是常态 |

---

## 禁止自动执行的动作

- 删除 emoji（除非用户要求）
- 统一为书面语
- 删除平台特定格式（# 标签、@ 提及）
- 改变链接
- 增加原文没有的互动话术
- 增加原文没有的 emoji
- 改变促销信息

---

## 默认 strategy

由 source 推导：
- author_written → preserve
- ai_draft → balance
- mixed → balance
- unknown → preserve

---

## 加载的模式包

- `references/patterns/hard-residue.md`（诊断发现时）
- `references/patterns/strong-contextual.md`（诊断发现时，假互动阈值放宽 ×2.0）
- `references/patterns/advisory-only.md`（output=diff 或 audit 时）
- `references/protected-spans.md`（始终加载）
- `references/false-positive-protection.md`（始终加载）

---

## 默认策略

- 假互动的阈值放宽（×2.0）
- 短句不检测（不当作"断奏戏剧"）
- 第二人称不当作假互动
- 口语化不当作填充短语
