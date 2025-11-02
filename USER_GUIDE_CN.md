# Claude Code 基础设施使用指南（用户版）

**作为最终用户，如何将这个参考库集成到你的项目中并使用**

---

## 📋 前置条件

在开始之前，确保：
- ✅ 你已经安装了 Claude Code（Cursor 中的 Claude Code 功能）
- ✅ 你有一个使用 Claude Code 的项目（项目根目录有 `.claude` 目录）
- ✅ 你了解你的项目结构（是 monorepo 还是单服务项目？）

---

## 🚀 快速开始（3个步骤，15分钟）

### 步骤 1：复制核心钩子（必须）

核心钩子实现技能自动激活功能：

```bash
# 进入这个参考库目录
cd /Users/binguo/workspaces/claude-code-infrastructure-showcase

# 假设你的项目路径是 ~/my-project
# 创建钩子目录（如果不存在）
mkdir -p ~/my-project/.claude/hooks

# 复制核心钩子文件
cp .claude/hooks/skill-activation-prompt.sh ~/my-project/.claude/hooks/
cp .claude/hooks/skill-activation-prompt.ts ~/my-project/.claude/hooks/
cp .claude/hooks/post-tool-use-tracker.sh ~/my-project/.claude/hooks/

# 复制 package.json（如果有）
cp .claude/hooks/package.json ~/my-project/.claude/hooks/ 2>/dev/null || true

# 设置为可执行
chmod +x ~/my-project/.claude/hooks/*.sh

# 安装依赖（如果需要）
cd ~/my-project/.claude/hooks && npm install 2>/dev/null || echo "无需安装依赖"
```

### 步骤 2：配置 settings.json

在你的项目中创建或编辑 `.claude/settings.json`：

```json
{
  "hooks": {
    "UserPromptSubmit": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "$CLAUDE_PROJECT_DIR/.claude/hooks/skill-activation-prompt.sh"
          }
        ]
      }
    ],
    "PostToolUse": [
      {
        "matcher": "Edit|MultiEdit|Write",
        "hooks": [
          {
            "type": "command",
            "command": "$CLAUDE_PROJECT_DIR/.claude/hooks/post-tool-use-tracker.sh"
          }
        ]
      }
    ]
  }
}
```

**注意：**
- 如果你的项目已有 `settings.json`，只需要添加 `hooks` 部分
- 不要删除你现有的配置

### 步骤 3：添加一个技能并测试

```bash
# 创建技能目录
mkdir -p ~/my-project/.claude/skills

# 假设你使用 Node.js/Express，复制后端技能
cp -r .claude/skills/backend-dev-guidelines ~/my-project/.claude/skills/

# 或者如果你使用 React，复制前端技能
# cp -r .claude/skills/frontend-dev-guidelines ~/my-project/.claude/skills/

# 复制技能规则配置文件
cp .claude/skills/skill-rules.json ~/my-project/.claude/skills/
```

**然后编辑 `~/my-project/.claude/skills/skill-rules.json`，根据你的项目调整路径模式：**

```json
{
  "skills": {
    "backend-dev-guidelines": {
      "fileTriggers": {
        "pathPatterns": [
          "src/**/*.ts",           // ← 根据你的项目结构调整
          "api/**/*.ts",
          "server/**/*.ts"
        ]
      }
    }
  }
}
```

---

## ✅ 测试是否工作

1. **打开你的项目**，在 Cursor 中使用 Claude Code
2. **编辑一个后端文件**（如果你添加了 backend-dev-guidelines）
3. **或者在对话中问**："帮我创建一个 Express 路由"
4. **你应该看到** Claude 自动建议使用 `backend-dev-guidelines` 技能

如果技能自动激活了，恭喜！✅ 设置成功。

---

## 📚 添加更多技能

根据需要复制更多技能：

### 后端开发技能
```bash
# 适用于：Node.js/Express/Prisma 项目
cp -r .claude/skills/backend-dev-guidelines ~/my-project/.claude/skills/
```

### 前端开发技能
```bash
# 适用于：React + MUI v7 项目
cp -r .claude/skills/frontend-dev-guidelines ~/my-project/.claude/skills/
```

### 路由测试技能
```bash
# 适用于：需要测试认证 API 的项目
cp -r .claude/skills/route-tester ~/my-project/.claude/skills/
```

### 错误追踪技能
```bash
# 适用于：使用 Sentry 的项目
cp -r .claude/skills/error-tracking ~/my-project/.claude/skills/
```

### 技能开发技能（元技能）
```bash
# 适用于：想要创建自己的技能
cp -r .claude/skills/skill-developer ~/my-project/.claude/skills/
```

**每次添加技能后，记得更新 `skill-rules.json` 添加对应的配置。**

---

## 🤖 使用专业代理

代理是独立的工具，直接复制就能用：

```bash
# 创建代理目录
mkdir -p ~/my-project/.claude/agents

# 复制你需要的代理（例如：代码架构审查）
cp .claude/agents/code-architecture-reviewer.md ~/my-project/.claude/agents/

# 其他常用代理：
# cp .claude/agents/refactor-planner.md ~/my-project/.claude/agents/
# cp .claude/agents/frontend-error-fixer.md ~/my-project/.claude/agents/
```

**如何使用代理：**
在 Claude Code 对话中，使用 Task 工具，指定：
- `subagent_type`: "code-architecture-reviewer"（或你复制的代理名称）
- `prompt`: 描述你想要完成的任务

---

## 💬 使用斜杠命令

```bash
mkdir -p ~/my-project/.claude/commands

# 开发文档命令（非常有用！）
cp .claude/commands/dev-docs.md ~/my-project/.claude/commands/
cp .claude/commands/dev-docs-update.md ~/my-project/.claude/commands/
```

**使用方式：**
在 Claude Code 对话中输入：
```
/dev-docs 实现用户认证系统
```

这会创建三个文档文件，帮助你管理复杂的开发任务。

---

## 🔧 自定义配置

### 调整技能激活规则

编辑 `~/.claude/skills/skill-rules.json`，可以：
- 修改触发关键词
- 调整文件路径模式
- 改变优先级

**示例：**如果你的后端代码在 `packages/api/` 而不是 `src/`：

```json
{
  "backend-dev-guidelines": {
    "fileTriggers": {
      "pathPatterns": [
        "packages/api/**/*.ts",
        "packages/server/**/*.ts"
      ]
    }
  }
}
```

### 添加自定义关键词

在 `skill-rules.json` 中添加你项目特定的关键词：

```json
{
  "backend-dev-guidelines": {
    "promptTriggers": {
      "keywords": [
        "backend",
        "API",
        "你的业务术语",    // ← 添加自定义关键词
        "你的服务名称"
      ]
    }
  }
}
```

---

## 📖 日常使用场景

### 场景 1：开发新功能

1. **使用 `/dev-docs`** 创建开发计划
   ```
   /dev-docs 实现支付集成功能
   ```

2. **开始编码时**，技能会自动激活：
   - 编辑 `src/routes/payment.ts` → 自动建议 `backend-dev-guidelines`
   - 编辑 `src/components/PaymentForm.tsx` → 自动建议 `frontend-dev-guidelines`

3. **遇到问题时**，使用专业代理：
   ```
   使用 code-architecture-reviewer 审查我的支付模块架构
   ```

### 场景 2：调试错误

1. **使用错误追踪技能**：
   - 提到 "错误处理" → 自动建议 `error-tracking` 技能
   - 提到 "Sentry" → 自动激活

2. **使用前端错误修复代理**：
   ```
   使用 frontend-error-fixer 修复这个 React 组件错误
   ```

### 场景 3：代码审查

1. **使用架构审查代理**：
   ```
   使用 code-architecture-reviewer 审查我的控制器层代码
   ```

2. **使用重构计划代理**：
   ```
   使用 refactor-planner 为我的用户服务制定重构计划
   ```

---

## ⚠️ 常见问题

### Q: 技能没有自动激活？

**检查：**
1. `settings.json` 中的钩子配置是否正确
2. 钩子文件是否有执行权限：`chmod +x .claude/hooks/*.sh`
3. `skill-rules.json` 中的路径模式是否匹配你的项目结构
4. 尝试在对话中明确提到关键词（如 "backend", "API", "controller"）

### Q: 路径模式怎么配置？

**判断你的项目类型：**
- **单服务项目**：`["src/**/*.ts", "backend/**/*.ts"]`
- **Monorepo**：`["packages/*/src/**/*.ts", "apps/*/src/**/*.ts"]`
- **微服务**：`["services/*/src/**/*.ts"]`

### Q: 可以只使用部分功能吗？

**完全可以！**
- 只想要技能自动激活 → 只需要步骤 1 和 2
- 只想要某个特定技能 → 只复制那个技能目录
- 只想要代理 → 只复制代理文件，无需配置

### Q: 技术栈不匹配怎么办？

**例如：**项目使用 Vue 而不是 React

**选项 1：**跳过不匹配的技能，使用其他通用技能
**选项 2：**使用 `skill-developer` 技能创建适配你技术栈的技能
**选项 3：**基于现有技能作为模板，修改代码示例和模式

---

## 🎯 推荐的使用路径

### 路径 A：最小化集成（5分钟）
1. 复制两个核心钩子
2. 配置 settings.json
3. 测试技能自动激活

**适合：**想先试试看，不确定是否要全面集成

### 路径 B：标准集成（15分钟）
1. 复制核心钩子
2. 配置 settings.json
3. 添加 1-2 个相关技能（后端或前端）
4. 配置 skill-rules.json

**适合：**知道自己的技术栈，想要核心功能

### 路径 C：完整集成（30分钟）
1. 复制所有核心钩子
2. 配置 settings.json
3. 添加所有相关技能
4. 添加常用代理
5. 添加斜杠命令
6. 全面自定义 skill-rules.json

**适合：**想要完整的开发体验，项目结构清晰

---

## 📝 下一步

1. ✅ **完成快速开始**（步骤 1-3）
2. ✅ **测试技能自动激活**
3. ✅ **根据需要添加更多技能**
4. ✅ **尝试使用代理和命令**
5. ✅ **根据项目需求自定义配置**

**遇到问题？**参考 `CLAUDE_INTEGRATION_GUIDE.md` 获取详细的技术说明。

**需要帮助？**在对话中告诉 Claude Code："我的技能没有激活，帮我检查配置"。

---

**祝使用愉快！** 🎉

