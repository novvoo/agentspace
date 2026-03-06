# agentspace

这个仓库包含两部分：

- `.agents/`：一套可复用的 Skills/Agent Prompts 索引与内容库
- `skill_router/`：一个最小实现的“Claude Code 风格 Skill 路由器”（按需加载 `SKILL.md`）

## skill_router 快速开始

列出可用 skills（不需要配置模型参数）：

```bash
python -m skill_router --list
```

选择并执行（需要 OpenAI 兼容接口参数）：

```bash
python -m skill_router "帮我写一个Python脚本解析JSON" --api-key "xxxx" --base-url "https://api.siliconflow.cn/v1" --model "Qwen/Qwen3-8B"
```

只做路由选择：

```bash
python -m skill_router --choose "我需要设计一个 REST API 的分页与错误格式" --api-key "xxxx" --base-url "https://api.siliconflow.cn/v1" --model "Qwen/Qwen3-8B"
```

JSON 输出（包含 used_skills）：

```bash
python -m skill_router "帮我写一个Python脚本解析JSON" --json --api-key "xxxx" --base-url "https://api.siliconflow.cn/v1" --model "Qwen/Qwen3-8B"
```

非 `--json` 输出会在第一行展示使用的 skill（或 none），后面直接输出最终回复内容。

## 环境变量（可选）

如果不想每次传 CLI 参数，也可以使用环境变量：

- `OPENAI_API_KEY`
- `OPENAI_BASE_URL`
- `OPENAI_MODEL`

技能扫描根目录（可选，使用 `;` 分隔多个目录）：

- `SKILL_ROOTS_ENTERPRISE`
- `SKILL_ROOTS_USER`
- `SKILL_ROOTS_PROJECT`
- `SKILL_ROOTS_PLUGIN`

## 目录说明

- Skills/Agents 内容库说明见 [.agents/README.md](.agents/README.md)
- 路由器实现说明见 [skill_router/README.md](skill_router/README.md)
