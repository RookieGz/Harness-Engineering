# 前端 Harness Engineering Starter Kit

这是一个面向前端开发场景的 Harness Engineering 起步仓库，用来给 agent 提供一套更稳定的页面开发工作方式。

## 目标

把前端常见流程：

产品文档 + UI 设计稿 + 接口文档 → 页面开发 → 还原 UI → 接入 API → 提交完成

改造成一条可验证的执行链路：

输入规范 → 任务拆解 → 分阶段开发 → 自动校验 → 产出证据 → 完成

## 仓库内容

### 1. `FRONTEND_RULES.md`
前端开发的基础规则，约束 agent 在实现页面时的顺序、范围和完成标准。

### 2. `.agents/skills/plan-frontend-page/`
用于规划阶段的 skill。

作用：
- 读取产品文档、设计稿、接口文档
- 生成页面任务文档
- 明确路由、接口、视口、页面状态、验收标准

当前包含：
- `SKILL.md`
- `references/page-task-template.md`

### 3. `.agents/skills/implement-frontend-page/`
用于实施阶段的 skill。

作用：
- 按页面任务文档开始开发
- 先完成静态 UI
- 再补交互和状态
- 最后接入 API 并做校验

当前包含：
- `SKILL.md`
- `scripts/verify-visual.sh`
- `scripts/verify-states.sh`
- `scripts/verify-api-mock.sh`
- `scripts/verify-integration.sh`

### 4. `CONTENTS.md`
当前分支已经写入的文件清单。

## 推荐工作流

### 第一步：规划页面任务
先使用 `plan-frontend-page`，把输入材料整理成可执行任务。

输入建议包括：
- 产品文档
- Figma 设计稿链接或页面说明
- 接口文档或 OpenAPI 文档
- 页面路由
- 需要覆盖的屏幕尺寸
- 必须实现的状态，例如 loading、empty、error、success

输出建议为一个页面任务文档，例如：
- `tasks/page-01.md`

### 第二步：开始页面实现
再使用 `implement-frontend-page`，按固定顺序实施：

1. 读取任务文档
2. 明确页面边界和组件边界
3. 用 mock data 先完成静态页面
4. 做视觉校验
5. 补交互和状态切换
6. 做状态校验
7. 通过 service 或 hook 接入 API
8. 做 mock API 校验
9. 做联调或集成校验
10. 收集截图和测试结果

## 这套方式适合解决什么问题

它主要解决的是前端 agent 开发里最常见的几个问题：

- 一上来直接接真实 API，导致 UI、状态、数据问题混在一起
- 页面做完了但没有截图、没有校验证据
- “1:1 还原设计稿”只有口头要求，没有可执行标准
- loading / empty / error 等关键状态容易漏掉
- 任务边界不清，agent 容易顺手改到无关模块

## 建议你后续继续补充的内容

这个 starter kit 目前还是最小可用版本，后续可以继续补这些内容：

- 补一个真正的 `AGENTS.md`
- 增加 `verify-api-smoke.sh`
- 增加 `tasks/` 目录示例
- 增加 Playwright 示例用例
- 增加 Figma 到前端任务文档的映射规则
- 增加接口契约校验规则

## 使用建议

这套仓库更适合作为模板或规则仓库使用，再按你自己的项目去替换：

- 实际路由
- 接口地址
- 测试命令
- 页面状态定义
- 断点规则
- 截图规则
- 目录结构

## 当前状态

当前内容写在 `v1` 分支。

如果后续要继续完善，比较自然的顺序是：

1. 先补 `AGENTS.md`
2. 再补一个页面任务示例
3. 再补 Playwright 测试样例
4. 最后把这些规则迁移进真实业务仓库
