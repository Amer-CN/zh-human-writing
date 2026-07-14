# profiles/essay.md
# zh-human-writing v1 — essay profile

---

## 编辑目标

- 减少模板化机器表达
- 提升自然度和可发布性
- 保持作者的个人声音和观点归属

---

## 重点保护项

| 保护项 | 说明 |
|--------|------|
| 作者个人观点和立场 | 不得被改变、软化或反转 |
| 作者的语气和语域 | 不得被统一为另一种腔调 |
| 个人经历和细节 | 不得被删除或篡改 |
| 引用和转述 | 不得被改写 |
| 数字、日期、人名 | 逐字保护（参见 `core/invariants.md`） |

---

## 允许的语气

- 口语化表达（合理范围内）
- 个人评论和判断
- 第一人称叙述（原文已有的）
- 不工整但真实的表达
- 带情绪色彩的措辞（原文已有的）

---

## 合法但容易误判的表达

| 表达 | 误判原因 | 正确处理 |
|------|---------|---------|
| "不是A而是B"（作者真实对比） | 被当作二元对立结构壳 | 检查是否有实质对比内容，有则保留 |
| 口语化冗余（如"就是说"） | 被当作填充短语 | author_written 路径假设是作者说话方式 |
| 不工整的对仗 | 被当作 AI 排比 | 检查是否承载信息，承载则保留 |
| 第一人称观点 | 被当作假互动 | 原文已有的第一人称是作者声音 |
| 反问句 | 被当作公式化挑战结构 | 检查是否承载真实质疑，承载则保留 |
| 长段引用 | 被当作无信息铺垫 | 引用是 protected span，不改 |

---

## 禁止自动执行的动作

- 增加具体细节（除非原文有明确依据）
- 增加第一人称（除非原文已有）
- 增加观点或感受
- 统一语域（把口语改成书面语或反之）
- 删除承担情绪或节奏作用的句子
- 重排段落

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
- `references/patterns/strong-contextual.md`（诊断发现时，正常执行）
- `references/patterns/advisory-only.md`（output=diff 或 audit 时）
- `references/protected-spans.md`（始终加载）
- `references/false-positive-protection.md`（始终加载）

---

## 默认策略

- 正常执行 strong-contextual 检测
- 不放宽聚集阈值
- 不降低假互动敏感度
