# Task23 v151 单变量对照

- 基线：v145 seed105 完整视频。该条在当前远端 scorer 下完成
  `Open Microwave` 与 `Place Cream Microwave`，但未完成 `Place Popcorn Microwave`。
- 观察：v150 从 v149 继承了完整长 VLA prompt 模板，seed104 从第一阶段就未开门；它不能用来
  判断 `place popcorn` target 是否导致最后一阶段过早停住。
- 单一行为修改：完整复刻 v145 seed105 的 VLM、VLA、短 primitive prompt、norm repo、scorer、
  hold/release、passage 与 anchor；只从 Task23 target JSON 删除 `place popcorn`，并从
  consecutive-hold JSON 删除它。
- 不变项：所有 `ORACLE_*` 为 0；没有 object anchor；VLM 仍负责输出每个 prompt；评分 commit
  为 `62214036103ee8d5fef9b475dd8b344b6e2cfc03`。
- 预期证据：开门和 cream 放置至少复刻 v145，之后 VLA 在 `place popcorn` 不会因 EEF 到浅层
  target 被 hold。若开门不能复刻，先判为 v145 基线复现失败，不把它归因于 popcorn target。
