# Personal Tutor Skill

`personal-tutor` 是一个面向交互式学习的 Codex Skill：把“我想学会某个知识或技能”转化为可验证的能力目标，裁剪不必要的内容，制定落地路线，并在计划生成后立即开始训练。

## 一句话调用

```text
使用 $personal-tutor 帮我把学习目标变成可执行计划，并立即开始交互式训练。
```

## 能力概览

`personal-tutor` 适用于学习、入门、复习或训练：

- 把主题改写为可测试的真实结果和最终实战任务。
- 根据时间、截止期、基础和约束裁剪学习范围。
- 默认支持最多 4 小时的高强度学习会话，也支持按天规划的学习路径。
- 通过诊断题、真实场景、错误纠正、迁移练习和最终实战验证能力。
- 根据学习状态动态使用一句话锚点、真实错误模拟、费曼复述和漏洞审计。
- 明确区分已验证掌握、未验证能力、部分达到和仍存在的漏洞。

它不用于仅需一个简短事实答案、纯内容生成，或用户明确只要求代做而不希望学习的任务。

## 安装

使用 Skills CLI 将本仓库安装为 `personal-tutor`：

```bash
npx skills add https://github.com/psiQAQ/personal-tutor
```

安装后的 Skill 目录通常为：

```text
.agents/skills/personal-tutor/
```

也可以直接阅读或引用入口文件：[SKILL.md](.agents/skills/personal-tutor/SKILL.md)。

## 使用示例

### 从零学习一项技能

```text
使用 $personal-tutor 帮我在 4 小时内学会 Docker 基础。
我的目标是能把一个本地 Web 服务容器化、运行、查看日志，并定位一次启动失败。
请先制定学习契约和路线，然后立即开始第一个诊断题。
```

### 按截止期规划

```text
使用 $personal-tutor 帮我在 7 天后能独立完成一个 Python 数据清洗任务。
我每天有 45 分钟，已经会基础语法，但不会处理缺失值和验证结果。
请按每天一个核心任务规划，并从今天的第一个练习开始。
```

## 工作方式

默认主线为：

```text
个人学习路径 → 学习曲线破坏者 → 真实错误模拟器 → 隐藏漏洞检测器
                         ↘ 困惑破碎机 / 强制费曼方法（按状态插入）
```

对应的执行重点是：

1. 先定义真实目标、最终实战和成功标准。
2. 明确现在必须学、暂时忽略和之后再学的内容。
3. 让学习者先行动，再根据错误提供逐级提示和最小解释。
4. 用变体、边界条件和最终实战确认能力是否可以独立迁移。

详细的教学理论、模式说明和选择依据见 [`references/learning-patterns.md`](.agents/skills/personal-tutor/references/learning-patterns.md)。

## 仓库结构

```text
personal-tutor/
├─ README.md
└─ .agents/
   └─ skills/
      └─ personal-tutor/
         ├─ SKILL.md
         ├─ agents/
         │  └─ openai.yaml
         └─ references/
            └─ learning-patterns.md
```

- `.agents/skills/personal-tutor/SKILL.md`：运行时入口，包含触发范围、执行工作流、状态维护、响应格式和交付前检查。
- `.agents/skills/personal-tutor/agents/openai.yaml`：面向 Skill 列表和调用界面的显示名称、简介及默认提示。
- `.agents/skills/personal-tutor/references/learning-patterns.md`：按需读取的学习理论、六种教学模式、边界和动态分支。

## 设计边界

- 以学习者的实际表现作为掌握证据，不把读过解释或复述术语当作掌握。
- 不确定的事实明确标记；涉及易变的技术、标准、法规或 API 时优先核对可靠的一手资料。
- 安全风险或高风险专业决策场景中，必要的警告和答案优先于错误模拟。
- 计划不是终点：生成路线后必须立即进入第一项训练。

## 维护检查

修改 Skill 后，应至少确认：

1. `.agents/skills/personal-tutor/SKILL.md` 的 frontmatter 中 `name` 仍为 `personal-tutor`。
2. `.agents/skills/personal-tutor/references/learning-patterns.md` 的链接和六种模式说明仍可访问。
3. 使用 Skill Creator 提供的 `quick_validate.py` 运行标准结构校验。

## 参考

本 README 的信息架构参考 [Blender MCP Skills Toolkit](https://github.com/psiQAQ/blender_mcp-setup-guide) 的项目定位、调用示例、能力概览、安装和仓库结构组织方式。
