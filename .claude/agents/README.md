# Agents

Specialized agents for complex, multi-step tasks.

---

## What Are Agents?

Agents are autonomous Claude instances that handle specific complex tasks. Unlike skills (which provide inline guidance), agents:
- Run as separate sub-tasks
- Work autonomously with minimal supervision
- Have specialized tool access
- Return comprehensive reports when complete

**Key advantage:** Agents are **standalone** - just copy the `.md` file and use immediately!

---

## Directory Structure

Agents are organized by category for better discoverability:

```
.claude/agents/
├── core/                    # Core development agents (10)
├── architecture/            # Architecture design agents (3)
├── implementation/          # Implementation agents (2)
├── quality/                 # Quality assurance agents (5)
├── design/                  # Design agents (optional)
└── research/                # Research & analysis agents (optional)
```

---

## Available Agents

### Core Agents (10)

Located in `core/` directory - essential agents for daily development:

#### code-architecture-reviewer
**Purpose:** Review code for architectural consistency and best practices

**When to use:**
- After implementing a new feature
- Before merging significant changes
- When refactoring code
- To validate architectural decisions

**Integration:** ✅ Copy as-is

---

#### code-refactor-master
**Purpose:** Plan and execute comprehensive refactoring

**When to use:**
- Reorganizing file structures
- Breaking down large components
- Updating import paths after moves
- Improving code maintainability

**Integration:** ✅ Copy as-is

---

#### documentation-architect
**Purpose:** Create comprehensive documentation

**When to use:**
- Documenting new features
- Creating API documentation
- Writing developer guides
- Generating architectural overviews

**Integration:** ✅ Copy as-is

---

#### frontend-error-fixer
**Purpose:** Debug and fix frontend errors

**When to use:**
- Browser console errors
- TypeScript compilation errors in frontend
- React errors
- Build failures

**Integration:** ⚠️ May reference screenshot paths - update if needed

---

#### plan-reviewer
**Purpose:** Review development plans before implementation

**When to use:**
- Before starting complex features
- Validating architectural plans
- Identifying potential issues early
- Getting second opinion on approach

**Integration:** ✅ Copy as-is

---

#### refactor-planner
**Purpose:** Create comprehensive refactoring strategies

**When to use:**
- Planning code reorganization
- Modernizing legacy code
- Breaking down large files
- Improving code structure

**Integration:** ✅ Copy as-is

---

#### web-research-specialist
**Purpose:** Research technical issues online

**When to use:**
- Debugging obscure errors
- Finding solutions to problems
- Researching best practices
- Comparing implementation approaches

**Integration:** ✅ Copy as-is

---

#### auth-route-tester
**Purpose:** Test authenticated API endpoints

**When to use:**
- Testing routes with JWT cookie auth
- Validating endpoint functionality
- Debugging authentication issues

**Integration:** ⚠️ Requires JWT cookie-based auth

---

#### auth-route-debugger
**Purpose:** Debug authentication issues

**When to use:**
- Auth failures
- Token issues
- Cookie problems
- Permission errors

**Integration:** ⚠️ Requires JWT cookie-based auth

---

#### auto-error-resolver
**Purpose:** Automatically fix TypeScript compilation errors

**When to use:**
- Build failures with TypeScript errors
- After refactoring that breaks types
- Systematic error resolution needed

**Integration:** ⚠️ May need path updates

---

### Architecture Agents (3)

Located in `architecture/` directory - for system design and architecture:

#### zen-architect ⭐
**Purpose:** Code planning, architecture design, and review tasks

**When to use:**
- Planning new features (ANALYZE mode)
- System design needs (ARCHITECT mode)
- Code review (REVIEW mode)
- Creating specifications for implementation

**Features:**
- Three operating modes: ANALYZE, ARCHITECT, REVIEW
- Embodies ruthless simplicity and analysis-first development
- Creates specifications that modular-builder implements

**Integration:** ✅ Copy as-is (project-specific references are optional)

**Note:** This agent works with `modular-builder` - zen-architect creates specs, modular-builder implements them.

---

#### database-architect
**Purpose:** Design database schemas and data models

**When to use:**
- Designing new database schemas
- Planning data models
- Database optimization
- Migration planning

**Integration:** ✅ Copy as-is

---

#### api-contract-designer
**Purpose:** Design API contracts and specifications

**When to use:**
- Designing new APIs
- Defining API contracts
- Creating API specifications
- Versioning APIs

**Integration:** ✅ Copy as-is

---

### Implementation Agents (2)

Located in `implementation/` directory - for code implementation:

#### modular-builder ⭐
**Purpose:** Primary implementation agent that builds code from specifications

**When to use:**
- Implementing modules from zen-architect specifications
- Building new features
- Creating self-contained modules following "bricks and studs" philosophy

**Features:**
- Works with zen-architect specifications
- Follows modular design philosophy
- Creates regeneratable modules with clear contracts

**Integration:** ✅ Copy as-is

**Note:** This agent implements specifications created by `zen-architect`.

---

#### component-designer
**Purpose:** Design and implement UI components

**When to use:**
- Creating new UI components
- Designing component interfaces
- Component composition
- Frontend component patterns

**Integration:** ✅ Copy as-is (useful for frontend projects)

---

### Quality Assurance Agents (5)

Located in `quality/` directory - for testing, security, and code quality:

#### bug-hunter ⭐
**Purpose:** Systematic debugging expert

**When to use:**
- When encountering errors or bugs
- Test failures
- Unexpected behavior
- Systematic debugging needed

**Features:**
- Hypothesis-driven debugging approach
- Minimal fix philosophy
- Root cause analysis

**Integration:** ✅ Copy as-is

**Note:** More general than `frontend-error-fixer` - works for all code types.

---

#### security-guardian ⭐
**Purpose:** Security review and vulnerability assessment

**When to use:**
- Before production deployments
- After adding features that handle user data
- When integrating third-party services
- After refactoring auth code
- When handling payment data
- Periodic security reviews

**Features:**
- OWASP Top 10 checks
- Secret detection
- Input/output security validation
- Authentication/authorization review

**Integration:** ✅ Copy as-is

**Note:** Critical for production deployments!

---

#### test-coverage
**Purpose:** Analyze test coverage and identify gaps

**When to use:**
- After writing new features
- After bug fixes
- During test reviews
- When planning test strategy

**Features:**
- Testing pyramid (60% unit, 30% integration, 10% e2e)
- Coverage gap identification
- Strategic test case suggestions

**Integration:** ✅ Copy as-is

---

#### performance-optimizer ⭐
**Purpose:** Analyze and improve performance

**When to use:**
- Slow API endpoints
- Performance bottlenecks
- Memory usage issues
- Database query optimization

**Features:**
- Measure-first approach
- 80/20 optimization principle
- Data-driven optimization decisions

**Integration:** ✅ Copy as-is

---

#### post-task-cleanup
**Purpose:** Ensure codebase hygiene after task completion

**When to use:**
- After completing todo lists
- After major feature implementation
- After bug fixes
- Before committing code

**Features:**
- Reviews git status
- Removes temporary artifacts
- Eliminates unnecessary complexity
- Ensures adherence to project philosophy

**Integration:** ✅ Copy as-is

---

## Agent Quick Reference

### By Category

| Category | Agents | Count |
|----------|--------|-------|
| **Core** | code-architecture-reviewer, code-refactor-master, documentation-architect, frontend-error-fixer, plan-reviewer, refactor-planner, web-research-specialist, auth-route-tester, auth-route-debugger, auto-error-resolver | 10 |
| **Architecture** | zen-architect, database-architect, api-contract-designer | 3 |
| **Implementation** | modular-builder, component-designer | 2 |
| **Quality** | bug-hunter, security-guardian, test-coverage, performance-optimizer, post-task-cleanup | 5 |
| **Total** | | **20** |

### By Priority

#### ⭐ High Priority (Core Workflow)
- `zen-architect` + `modular-builder` - Architecture and implementation workflow
- `bug-hunter` - Systematic debugging
- `security-guardian` - Security reviews
- `performance-optimizer` - Performance analysis

#### ✅ Standard Priority
- `code-refactor-master` - Refactoring
- `test-coverage` - Test analysis
- `post-task-cleanup` - Code hygiene

#### 🔧 Specialized Use
- `frontend-error-fixer` - Frontend-specific
- `auth-route-tester` / `auth-route-debugger` - Auth-specific
- `component-designer` - Frontend components

---

## How to Use Agents

### Using an Agent

Agents are invoked via the Task tool in Claude Code. Simply ask Claude to use an agent:

```bash
# Examples:
"Use the zen-architect agent to design a caching layer"
"Use the bug-hunter agent to debug this error"
"Use the security-guardian agent to review this code before deployment"
```

### Agent Workflows

#### Architecture → Implementation Workflow
1. **zen-architect** (ANALYZE mode) - Analyzes requirements and creates specifications
2. **modular-builder** - Implements modules from specifications

#### Debugging Workflow
1. **bug-hunter** - Systematically finds and fixes bugs
2. **post-task-cleanup** - Ensures code hygiene after fixes

#### Pre-Deployment Workflow
1. **security-guardian** - Security review
2. **test-coverage** - Test coverage analysis
3. **performance-optimizer** - Performance check
4. **post-task-cleanup** - Final cleanup

---

## When to Use Agents vs Skills

| Use Agents When... | Use Skills When... |
|-------------------|-------------------|
| Task requires multiple steps | Need inline guidance |
| Complex analysis needed | Checking best practices |
| Autonomous work preferred | Want to maintain control |
| Task has clear end goal | Ongoing development work |
| Example: "Review all controllers" | Example: "Creating a new route" |

**Both can work together:**
- Skill provides patterns during development
- Agent reviews the result when complete

---

## Integration Notes

### Project-Specific References

Some agents reference project-specific context files (like `@ai_context/IMPLEMENTATION_PHILOSOPHY.md`). These references are marked as optional:
- If your project has these files, agents will use them
- If not, agents will work without them
- Consider creating these files for better agent context

### Path Updates

Most agents work as-is, but check for:
- Hardcoded paths (use `$CLAUDE_PROJECT_DIR` or relative paths)
- Project-specific URLs (update for your project)
- Screenshot paths (for frontend-error-fixer)

---

## Creating Your Own Agents

Agents are markdown files with optional YAML frontmatter:

```markdown
---
name: my-agent
description: What this agent does
model: inherit
---

# Agent Name

## Purpose
What this agent does

## Instructions
Step-by-step instructions for autonomous execution

## Tools Available
List of tools this agent can use

## Expected Output
What format to return results in
```

**Tips:**
- Be very specific in instructions
- Break complex tasks into numbered steps
- Specify exactly what to return
- Include examples of good output
- List available tools explicitly

---

## Troubleshooting

### Agent not found

**Check:**
```bash
# Is agent file present?
ls -la .claude/agents/[category]/[agent-name].md
```

### Agent fails with path errors

**Check for hardcoded paths:**
```bash
grep "~/\|/root/\|/Users/" .claude/agents/[category]/[agent-name].md
```

**Fix:**
Update paths to use `$CLAUDE_PROJECT_DIR` or relative paths.

---

## Next Steps

1. **Browse agents above** - Find ones useful for your work
2. **Try the core workflow** - Start with zen-architect → modular-builder
3. **Use quality agents** - bug-hunter, security-guardian, test-coverage
4. **Create your own** - Follow the pattern for your specific needs

**Questions?** See [CLAUDE_INTEGRATION_GUIDE.md](../../CLAUDE_INTEGRATION_GUIDE.md)

---

## Migration Notes

This agents directory includes agents migrated from the amplifier project. See `MIGRATION_ANALYSIS.md` for details on the migration process and agent categorization.

**Key Migrated Agents:**
- `zen-architect` - Core architecture agent
- `modular-builder` - Core implementation agent
- `bug-hunter` - Systematic debugging
- `security-guardian` - Security reviews
- `performance-optimizer` - Performance analysis

These agents have been cleaned of project-specific references and are ready to use.