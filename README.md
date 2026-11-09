# 合作式开发与研究技能

两项可独立安装的 Codex 技能，用于用户与代理共同推进多阶段项目。用户确认关键路线与取舍，代理按依赖执行，持续维护进展、验收证据与阶段交接。

| 技能 | 适用场景 | 关键记录 |
| --- | --- | --- |
| [合作式开发](skills/collaborative-development/SKILL.md) | 多阶段功能开发、重构或工程交付 | 技术取舍、任务依赖、验收结果、可恢复版本 |
| [合作式研究](skills/collaborative-research/SKILL.md) | 实验、论文复现或分阶段证据综合 | 研究协议、对照与门槛、结果及适用范围、复现入口 |

## 安装与使用

在 Codex 中发送以下指令，按需保留要安装的技能路径。

```text
使用 $skill-installer 从 LeoAndJellyfish/collaborative-dev-research-skills 安装 skills/collaborative-development 和 skills/collaborative-research。
```

在项目会话中调用对应技能，可附上现有的 README、计划或实验记录。

- `使用 $collaborative-development 为这次重构拟定路线图，说明兼容性取舍和各阶段的验收条件。`
- `使用 $collaborative-research 按 README 中已确认的路线继续，汇总本轮结果和触发下一阶段的条件。`

## 路线图示例

示例中的研究路线已确认，两项准备工作可以并行。留出验证开始前先固定样本、评分规则与基线。决策节点显示测量结束后的两种去向。

```mermaid
flowchart TD
    accTitle: 文档日期提取的研究路线图
    accDescr: 已确认研究路线并完成样本与基线准备。下一步是运行留出验证。十份文档中至少八份日期正确时进入扩展复测，否则先归档失败样本并提出修订路线。
    A["已完成 · 确认研究路线<br/>评估文档日期提取规则"]
    B["已完成 · 固定样本和评分<br/>十份留出文档"]
    C["已完成 · 复核基线和配置"]
    D["下一步 · 运行留出验证"]
    E{"十份中至少八份日期正确？"}
    F["待办 · 扩展复测<br/>采用独立文档"]
    G["待办 · 归档失败样本<br/>提交修订路线"]
    A --> B
    A --> C
    B --> D
    C --> D
    D --> E
    E -->|达标| F
    E -->|未达标| G
    classDef done fill:#e8f3e8,stroke:#43834b,color:#173b1c;
    classDef current fill:#fff0cc,stroke:#b78016,color:#604200;
    classDef planned fill:#f3f4f6,stroke:#8b929c,color:#252a31;
    class A,B,C done;
    class D current;
    class E,F,G planned;
```

绿色表示已完成，黄色表示下一步，灰色表示待办与尚待判定的门槛。项目图旁可链接实际的协议、提交、验收或结果。开发项目可采用同一图式，在汇合点执行集成验收，依据结果进入交付或修正分支。

## 阻塞与交接

单条任务线受阻时，先记录影响和恢复条件，再推进其他独立任务。所有可执行分支都受阻时，代理汇报自上次收到用户消息以来的进展、已尝试的处理方式和需要用户提供的具体帮助。阶段结束后，归档可追溯的中间版本，清理可重建且已无引用的临时文件，并记录下一次接续的位置。
