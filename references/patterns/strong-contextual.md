# references/patterns/strong-contextual.md
# zh-human-writing v1 — strong-contextual 模式包
# 单次出现未必有问题，聚集出现时才标记。需要结合 profile 和上下文判断。

---

## SC-001: 无信息开场

- **ID**: SC-001
- **问题**: 开场句不承载信息，只是填充
- **触发线索**: "让我们来看看"、"在当今…的时代"、"随着…的发展"
- **聚集阈值**: 同段 ≥2 次
- **适用 profile**: essay（正常）、technical（×1.5）、social（正常）
- **处理权限**: conditional — 聚集时标记，结合 profile 判断
- **language_origin**: language_general
- **false positives**: 教学文本中的开场引导语可能合理
- **protected cases**: 技术文档中的引导语；社媒中的开场互动
- **来源说明**: 重新实现，通用模式

---

## SC-002: 无信息导航

- **ID**: SC-002
- **问题**: 导航句不承载信息，只是填充
- **触发线索**: "接下来我们将讨论"、"首先…其次…最后"、"下面我们来看"
- **聚集阈值**: 同段 ≥2 次
- **适用 profile**: essay（正常）、technical（×1.5）、social（正常）
- **处理权限**: conditional
- **language_origin**: language_general
- **false positives**: 技术文档中的步骤说明是合理的
- **protected cases**: 技术文档中的步骤导航
- **来源说明**: 重新实现，通用模式

---

## SC-003: 无信息总结

- **ID**: SC-003
- **问题**: 总结句不承载新信息，只是重复
- **触发线索**: "总而言之"、"综上所述"、"总结来说"、"通过以上分析可以看出"
- **聚集阈值**: 同段 ≥2 次
- **适用 profile**: essay（正常）、technical（×1.5）、social（正常）
- **处理权限**: conditional
- **language_origin**: language_general
- **false positives**: 学术/技术文档中的总结可能是合理的
- **protected cases**: 技术文档中的结论总结
- **来源说明**: 重新实现，通用模式

---

## SC-004: 无来源权威铺垫

- **ID**: SC-004
- **问题**: 使用"研究表明"等权威铺垫但无具体来源
- **触发线索**: "研究表明"、"数据显示"、"据统计"（无具体来源引用）
- **聚集阈值**: 同段 ≥2 次
- **适用 profile**: essay（正常）、technical（正常）、social（正常）
- **处理权限**: conditional
- **language_origin**: language_general
- **false positives**: 有具体来源引用的权威铺垫是合理的
- **protected cases**: 有具体来源（如"Smith et al. (2023) 研究表明"）
- **来源说明**: 重新实现，通用模式

---

## SC-005: 连续同构结构

- **ID**: SC-005
- **问题**: 连续 ≥3 个相同句式
- **触发线索**: 连续排比、连续"不是…而是…"、连续三段式
- **聚集阈值**: 连续 ≥3 次
- **适用 profile**: essay（正常）、technical（正常）、social（正常）
- **处理权限**: conditional
- **language_origin**: language_general
- **false positives**: 修辞手段中的排比是合法的
- **protected cases**: 诗歌、演讲稿中的修辞排比
- **来源说明**: 重新实现，通用模式

---

## SC-006: 明显假互动

- **ID**: SC-006
- **问题**: 假互动表达（非社媒场景）
- **触发线索**: "你可能会问"、"你想想看"、"你有没有想过"（非社媒场景）
- **聚集阈值**: 同段 ≥2 次
- **适用 profile**: essay（正常）、technical（正常）、social（×2.0，假互动在社媒中是常态）
- **处理权限**: conditional
- **language_origin**: language_general
- **false positives**: 社媒中的互动是常态；教学文本中的引导性提问可能合理
- **protected cases**: 社媒短文；教学文本中的苏格拉底式提问
- **来源说明**: 重新实现，通用模式

---

## 动作权限汇总

| 级别 | preserve | balance | rebuild |
|------|---------|---------|---------|
| strong-contextual（聚集） | conditional 标记+profile 判断 | conditional 删除/改写 | conditional 删除/改写 |
| strong-contextual（单次） | deny | deny | conditional 标记 |

strong-contextual 只能输出 review 候选，除非上下文明确证明没有信息损失。
