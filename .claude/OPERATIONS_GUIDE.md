# 运维工作工具指南

## 运维工作涉及的主要工具

根据项目现有工具分析，运维工作主要会涉及到以下工具：

---

## 🤖 Agents（代理）- 核心运维工具

### 1. **performance-optimizer** ⭐
**用途**：性能分析和优化

**运维场景**：
- ✅ 分析 API 性能瓶颈
- ✅ 数据库查询优化
- ✅ 内存使用分析
- ✅ 系统性能调优
- ✅ 响应时间优化

**使用方式**：
```
你：分析这个 API 的性能瓶颈并优化
→ 使用 performance-optimizer agent
→ Agent 会：
  1. 分析性能指标
  2. 识别瓶颈
  3. 实施优化
  4. 返回优化报告
```

---

### 2. **bug-hunter** ⭐
**用途**：系统化调试和故障排查

**运维场景**：
- ✅ 生产环境错误排查
- ✅ 系统故障诊断
- ✅ 日志分析
- ✅ 错误根因分析
- ✅ 故障恢复

**使用方式**：
```
你：这个生产错误很奇怪，帮我找出根本原因
→ 使用 bug-hunter agent
→ Agent 会：
  1. 收集错误信息
  2. 分析日志
  3. 提出假设
  4. 系统化测试
  5. 找出根本原因并修复
```

---

### 3. **security-guardian** ⭐
**用途**：安全审查和漏洞检测

**运维场景**：
- ✅ 生产部署前安全检查
- ✅ 安全漏洞扫描
- ✅ 配置安全检查
- ✅ 认证授权审查
- ✅ 数据保护检查

**使用方式**：
```
你：检查这个部署是否有安全漏洞
→ 使用 security-guardian agent
→ Agent 会：
  1. 检查 OWASP Top 10
  2. 检测硬编码密钥
  3. 验证输入输出安全
  4. 返回安全审查报告
```

---

### 4. **web-research-specialist**
**用途**：技术研究和问题解决

**运维场景**：
- ✅ 查找运维问题解决方案
- ✅ 研究最佳实践
- ✅ 比较技术方案
- ✅ 查找工具和配置

**使用方式**：
```
你：研究如何优化 Kubernetes 部署配置
→ 使用 web-research-specialist agent
→ Agent 会：
  1. 研究相关技术
  2. 查找最佳实践
  3. 比较解决方案
  4. 返回研究报告
```

---

### 5. **code-architecture-reviewer**
**用途**：架构审查（运维视角）

**运维场景**：
- ✅ 部署架构审查
- ✅ 可扩展性评估
- ✅ 高可用性检查
- ✅ 资源使用评估

**使用方式**：
```
你：审查这个服务的部署架构是否合理
→ 使用 code-architecture-reviewer agent
→ Agent 会：
  1. 审查架构设计
  2. 评估可扩展性
  3. 检查高可用性
  4. 返回审查报告
```

---

## 📚 Skills（技能）- 运维知识库

### 1. **error-tracking** ⭐
**用途**：错误监控和追踪（Sentry）

**运维场景**：
- ✅ 生产环境错误监控
- ✅ 错误日志分析
- ✅ 性能监控
- ✅ 告警配置
- ✅ 错误趋势分析

**使用方式**：
- 自动激活：编辑包含错误处理的代码时
- 手动激活：使用 `error-tracking` skill

**特点**：
- 提供 Sentry 集成模式
- 错误捕获最佳实践
- 性能监控配置

---

### 2. **backend-dev-guidelines**
**用途**：后端开发指南（包含运维相关）

**运维场景**：
- ✅ 部署配置管理
- ✅ 环境变量管理
- ✅ 日志配置
- ✅ 监控集成

**使用方式**：
- 自动激活：编辑后端代码时
- 提供配置管理最佳实践

---

## 💬 Commands（命令）- 运维任务规划

### 1. **/dev-docs** ⭐
**用途**：运维任务规划文档

**运维场景**：
- ✅ 部署任务规划
- ✅ 运维任务清单
- ✅ 故障处理流程
- ✅ 系统升级计划

**使用方式**：
```
你：/dev-docs 生产环境部署计划
→ Command 生成：
  - dev/active/production-deployment/plan.md
  - dev/active/production-deployment/context.md
  - dev/active/production-deployment/tasks.md
→ 文档持久化，可以跨会话使用
```

---

### 2. **/dev-docs-update**
**用途**：更新运维任务文档

**运维场景**：
- ✅ 记录运维操作
- ✅ 更新任务状态
- ✅ 记录关键决策
- ✅ 记录故障处理过程

**使用方式**：
```
你：/dev-docs-update
→ 更新所有活跃任务的上下文文档
→ 记录运维操作和决策
```

---

## 🪝 Hooks（钩子）- 运维自动化

### 1. **post-tool-use-tracker**
**用途**：跟踪文件修改（运维文档）

**运维场景**：
- ✅ 跟踪配置文件修改
- ✅ 记录部署脚本变更
- ✅ 维护配置变更历史

---

## 运维工作流示例

### 场景 1：生产环境故障排查

**阶段 1：规划（使用 Commands）**
```
你：/dev-docs 生产环境故障排查
→ 生成排查计划文档
→ 记录故障现象和初步分析
```

**阶段 2：排查（使用 Agents）**
```
你：分析生产环境错误日志
→ 使用 bug-hunter agent
→ Agent 系统化分析错误
→ 返回排查报告和修复方案
```

**阶段 3：监控（使用 Skills）**
```
你：检查错误监控配置
→ error-tracking skill 自动激活
→ 提供 Sentry 监控最佳实践
```

**阶段 4：更新文档（使用 Commands）**
```
你：/dev-docs-update
→ 更新故障排查文档
→ 记录排查过程和解决方案
```

---

### 场景 2：性能优化

**阶段 1：分析（使用 Agents）**
```
你：分析 API 性能瓶颈
→ 使用 performance-optimizer agent
→ Agent 分析性能指标
→ 识别瓶颈并优化
```

**阶段 2：监控（使用 Skills）**
```
你：配置性能监控
→ error-tracking skill 提供 Sentry 性能监控配置
→ 设置性能指标监控
```

**阶段 3：验证（使用 Agents）**
```
你：验证优化效果
→ 使用 performance-optimizer agent
→ Agent 对比优化前后性能
→ 返回验证报告
```

---

### 场景 3：安全审查

**阶段 1：审查（使用 Agents）**
```
你：生产部署前安全检查
→ 使用 security-guardian agent
→ Agent 检查安全漏洞
→ 返回安全审查报告
```

**阶段 2：修复（使用 Agents）**
```
你：修复发现的安全问题
→ 使用 bug-hunter agent（如果需要）
→ 或使用 security-guardian agent 指导修复
```

**阶段 3：验证（使用 Agents）**
```
你：验证安全问题已修复
→ 使用 security-guardian agent
→ Agent 再次检查
→ 确认安全问题已解决
```

---

## 运维工具优先级

### ⭐ 高优先级（核心运维工具）

1. **performance-optimizer** - 性能分析
2. **bug-hunter** - 故障排查
3. **security-guardian** - 安全审查
4. **error-tracking** - 错误监控

### ✅ 标准优先级

5. **web-research-specialist** - 技术研究
6. **code-architecture-reviewer** - 架构审查
7. **/dev-docs** - 任务规划

---

## 运维场景 vs 工具映射

| 运维场景 | 主要工具 | 辅助工具 |
|---------|---------|---------|
| **性能分析** | performance-optimizer | error-tracking |
| **故障排查** | bug-hunter | web-research-specialist |
| **安全审查** | security-guardian | code-architecture-reviewer |
| **错误监控** | error-tracking | bug-hunter |
| **部署规划** | /dev-docs | plan-reviewer |
| **技术研究** | web-research-specialist | documentation-architect |
| **架构审查** | code-architecture-reviewer | zen-architect |
| **日志分析** | bug-hunter | error-tracking |
| **配置管理** | backend-dev-guidelines | /dev-docs |

---

## 当前工具的局限性

### 缺失的运维功能

1. **部署相关**：
   - ❌ 部署自动化脚本生成
   - ❌ CI/CD 配置审查
   - ❌ 容器化配置（Docker/Kubernetes）

2. **监控相关**：
   - ❌ 监控告警配置
   - ❌ 监控指标设计
   - ❌ 日志聚合配置

3. **基础设施相关**：
   - ❌ 基础设施即代码（Terraform/CloudFormation）
   - ❌ 云资源配置审查
   - ❌ 网络配置审查

4. **数据库运维**：
   - ❌ 数据库性能优化
   - ❌ 数据库备份策略
   - ❌ 数据库迁移规划

---

## 建议：扩展运维工具

### 可以创建的运维 Agents

1. **deployment-specialist**
   - 用途：部署脚本生成和审查
   - 场景：CI/CD 配置、部署流程审查

2. **monitoring-architect**
   - 用途：监控系统设计
   - 场景：监控指标设计、告警配置

3. **infrastructure-reviewer**
   - 用途：基础设施审查
   - 场景：云资源配置、网络配置审查

4. **database-optimizer**
   - 用途：数据库性能优化
   - 场景：查询优化、索引设计、备份策略

### 可以创建的运维 Skills

1. **deployment-guidelines**
   - 用途：部署最佳实践
   - 场景：部署流程、环境配置

2. **monitoring-patterns**
   - 用途：监控模式和实践
   - 场景：监控指标、告警规则

---

## 总结

### 运维工作主要工具

1. **Agents（代理）**：
   - `performance-optimizer` - 性能分析 ⭐
   - `bug-hunter` - 故障排查 ⭐
   - `security-guardian` - 安全审查 ⭐
   - `web-research-specialist` - 技术研究

2. **Skills（技能）**：
   - `error-tracking` - 错误监控 ⭐

3. **Commands（命令）**：
   - `/dev-docs` - 任务规划 ⭐
   - `/dev-docs-update` - 文档更新

### 核心运维工作流

```
规划（Commands） → 执行（Agents） → 监控（Skills） → 更新（Commands）
```

### 最常用的运维工具组合

- **性能分析**：`performance-optimizer` + `error-tracking`
- **故障排查**：`bug-hunter` + `error-tracking` + `/dev-docs`
- **安全审查**：`security-guardian` + `code-architecture-reviewer`
- **技术研究**：`web-research-specialist` + `/dev-docs`


