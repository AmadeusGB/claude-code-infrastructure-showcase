# Agents 迁移分析报告

## 一、现有 Agents 分析（10个）

### 核心开发类
- `code-architecture-reviewer` - 架构审查
- `code-refactor-master` - 重构执行
- `refactor-planner` - 重构规划
- `plan-reviewer` - 计划审查
- `documentation-architect` - 文档生成

### 错误处理类
- `frontend-error-fixer` - 前端错误修复
- `auto-error-resolver` - 自动错误解决

### 认证测试类
- `auth-route-tester` - 认证路由测试
- `auth-route-debugger` - 认证路由调试

### 研究类
- `web-research-specialist` - 网络研究

---

## 二、源项目 Agents 分析（29个）

### 架构类（Architecture）
- `zen-architect` - 架构设计和规划（核心，与 plan-reviewer 互补）
- `database-architect` - 数据库架构设计
- `design-system-architect` - 设计系统架构
- `layout-architect` - 布局架构
- `api-contract-designer` - API 合约设计
- `contract-spec-author` - 合约规范作者
- `module-intent-architect` - 模块意图架构
- `subagent-architect` - 子代理架构（元代理，用于创建新代理）

### 实现类（Implementation）
- `modular-builder` - 模块构建（核心实现代理）
- `component-designer` - 组件设计
- `integration-specialist` - 集成专家

### 质量保证类（Quality）
- `bug-hunter` - 错误狩猎（比 frontend-error-fixer 更通用）
- `security-guardian` - 安全守护（重要）
- `test-coverage` - 测试覆盖分析
- `performance-optimizer` - 性能优化（重要）
- `post-task-cleanup` - 任务后清理（代码库卫生）

### 设计类（Design）
- `art-director` - 艺术指导
- `animation-choreographer` - 动画编排
- `responsive-strategist` - 响应式策略
- `visualization-architect` - 可视化架构

### 研究分析类（Research & Analysis）
- `analysis-engine` - 分析引擎
- `concept-extractor` - 概念提取
- `content-researcher` - 内容研究
- `knowledge-archaeologist` - 知识考古
- `insight-synthesizer` - 洞察合成
- `pattern-emergence` - 模式涌现（高级分析）

### 工具类（Tools）
- `graph-builder` - 图构建
- `ambiguity-guardian` - 歧义守护
- `voice-strategist` - 语音策略

### 项目特定（不迁移）
- `amplifier-cli-architect` - Amplifier CLI 架构（项目特定，不迁移）

---

## 三、功能对比与重复分析

### 重复/相似功能对比

| 现有 Agent | 源项目 Agent | 关系 | 建议 |
|-----------|-------------|------|------|
| `code-architecture-reviewer` | `zen-architect` (REVIEW模式) | 部分重叠 | 保留现有，zen-architect 更全面 |
| `plan-reviewer` | `zen-architect` (ANALYZE模式) | 部分重叠 | 保留现有，zen-architect 更全面 |
| `frontend-error-fixer` | `bug-hunter` | bug-hunter 更通用 | 保留现有，迁移 bug-hunter 作为补充 |
| `auto-error-resolver` | `bug-hunter` | bug-hunter 更系统化 | 保留现有，迁移 bug-hunter 作为补充 |
| `refactor-planner` | `zen-architect` (ARCHITECT模式) | 部分重叠 | 保留现有，zen-architect 更全面 |
| `code-refactor-master` | `modular-builder` | 不同职责：重构 vs 新建 | 保留两者，互补使用 |

### 新增价值 Agents（建议迁移）

#### 高价值（核心）
1. **zen-architect** - 架构设计和规划的核心代理
2. **modular-builder** - 模块实现的核心代理
3. **bug-hunter** - 系统化调试
4. **security-guardian** - 安全审查（重要）
5. **test-coverage** - 测试覆盖分析
6. **performance-optimizer** - 性能优化

#### 中等价值（有用）
7. **database-architect** - 数据库设计
8. **design-system-architect** - 设计系统（如果项目有前端）
9. **post-task-cleanup** - 代码库卫生
10. **api-contract-designer** - API 设计
11. **component-designer** - 组件设计（前端项目）

#### 低价值（可选）
12. **analysis-engine** - 分析引擎
13. **concept-extractor** - 概念提取
14. **knowledge-archaeologist** - 知识考古
15. **pattern-emergence** - 模式涌现（高级）
16. **subagent-architect** - 元代理（用于创建新代理）

---

## 四、分类方案

```
.claude/agents/
├── core/                    # 现有核心 agents（不移动，保持向后兼容）
│   ├── code-architecture-reviewer.md
│   ├── code-refactor-master.md
│   ├── plan-reviewer.md
│   ├── refactor-planner.md
│   ├── documentation-architect.md
│   ├── frontend-error-fixer.md
│   ├── auto-error-resolver.md
│   ├── auth-route-tester.md
│   ├── auth-route-debugger.md
│   └── web-research-specialist.md
│
├── architecture/            # 架构设计类
│   ├── zen-architect.md
│   ├── database-architect.md
│   ├── api-contract-designer.md
│   ├── module-intent-architect.md
│   └── subagent-architect.md
│
├── implementation/          # 实现类
│   ├── modular-builder.md
│   ├── component-designer.md
│   └── integration-specialist.md
│
├── quality/                # 质量保证类
│   ├── bug-hunter.md
│   ├── security-guardian.md
│   ├── test-coverage.md
│   ├── performance-optimizer.md
│   └── post-task-cleanup.md
│
├── design/                  # 设计类（可选）
│   ├── design-system-architect.md
│   ├── layout-architect.md
│   ├── animation-choreographer.md
│   └── responsive-strategist.md
│
└── research/                # 研究分析类（可选）
    ├── analysis-engine.md
    ├── concept-extractor.md
    ├── knowledge-archaeologist.md
    └── pattern-emergence.md
```

---

## 五、迁移优先级

### 第一批（核心价值）
1. zen-architect
2. modular-builder
3. bug-hunter
4. security-guardian
5. test-coverage
6. performance-optimizer

### 第二批（高价值）
7. database-architect
8. post-task-cleanup
9. api-contract-designer
10. component-designer（如果项目有前端）

### 第三批（可选）
11. design-system-architect（如果项目有前端）
12. analysis-engine
13. subagent-architect
14. 其他研究分析类

---

## 六、注意事项

1. **路径检查**：迁移前检查所有硬编码路径
2. **项目特定引用**：移除或更新对 amplifier 项目的引用
3. **依赖关系**：检查 agents 之间的依赖（如 zen-architect → modular-builder）
4. **工具访问**：确认 agents 需要的工具在当前项目中可用
5. **向后兼容**：保持现有 agents 在 core/ 目录，不影响现有使用

---

## 七、迁移计划

1. ✅ 创建分类目录结构
2. ✅ 迁移第一批核心 agents
3. ✅ 检查路径和引用
4. ✅ 更新 README.md
5. ✅ 测试关键 agents
6. ⏳ 根据需求迁移第二批和第三批
