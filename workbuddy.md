# WorkBuddy 对话上下文（workbuddy.md）

本项目为麦当劳程序员节创意开发大赛参赛作品，参与 **WorkBuddy 专项奖励**。本文件说明项目与腾讯 WorkBuddy 智能体的真实联动情况。

## 1. 开发方式

本项目在 **腾讯 WorkBuddy** 智能体中完成开发：

- **需求分析与选题**：由 WorkBuddy 对话完成——检索官方赛事规则（M-China/mcd-developer-innovation-challenge 仓库）与实时排行榜，识别「省钱助手」「活动雷达」等已有同质作品，确定「全场景情报中枢」差异化定位。
- **官方文档研读**：WorkBuddy 通过对话拉取 M-China/mcd-mcp-server 官方 README，整理出 30+ 个 MCP 工具的完整清单与用途说明，沉淀为 `references/tools.md`。
- **SKILL 编写**：`SKILL.md`（技能主体）、`MCP_INTEGRATION.md`（接入说明）、`README.md`、`CONTEST_DECLARATION.md` 等全部参赛文件均由 WorkBuddy 在对话中生成与迭代。
- **MCP 接入**：按 WorkBuddy 自定义连接器方式配置 `mcd-mcp`（Streamable HTTP + Bearer Token），并在 WorkBuddy 会话中进行真实 MCP 联调。

## 2. 运行形态

本 Skill 面向 WorkBuddy 运行时：

- 用户在 WorkBuddy 对话中说「今天麦当劳有什么值得关注的」「我的券快过期了吗」等，
  WorkBuddy 加载 `SKILL.md`，按其工作流调用已连接的 `mcd-mcp` 工具，输出每日情报简报。
- 技能不绑定特定 Agent 框架：`SKILL.md` 与 `references/tools.md` 全程使用官方工具名
  （`campaign-calendar`、`query-my-coupons` 等），同样可接入 Claude Code / Cursor 等支持 MCP 的客户端。

## 3. 对话证据

WorkBuddy 对话中完成的关键动作（对话上下文可在 WorkBuddy 客户端中回溯）：

1. 解析大赛公众号文章 → 提取参赛流程与奖励结构
2. 抓取官方赛事仓库规则 → 确认必交文件与 Issue 报名格式
3. 抓取官方 MCP 文档 → 沉淀 30+ 工具速查表
4. 分析排行榜已有作品 → 差异化选题「麦麦情报站」
5. 编写全部参赛文件 → 形成 mcd-info-station 仓库
6. （Token 到位后）真实 MCP 联调 → 验证活动/券/积分链路

## 4. 声明

本项目为 WorkBuddy 智能体真实辅助开发的原创作品，符合 WorkBuddy 专项奖励的申报条件。
