# Agent Engineering Summary

## Evolution of AI Interaction

Three distinct eras:
1. **Prompt Engineering** - Crafting perfect individual prompts
2. **Context Engineering** - Optimizing context and CLAUDE.md files  
3. **Agent Engineering** - Designing specialized, reusable AI agents

## Agent Types Comparison

| Aspect | Custom Agents | Split Role Sub-agents | Task/Agent Tools |
|--------|---------------|----------------------|------------------|
| Token Efficiency | ⭐⭐⭐ | ⭐⭐ | ⭐ |
| Activation | Automatic delegation | Manual delegation | Manual delegation |
| Shared System Prompt | No | Yes | Yes |
| Portability | Highly portable (single .md file) | Impractical | Impractical |
| Configuration | YAML frontmatter + system prompt | Task description only | Task description only |

## Performance & Token Optimization

### Agent Weight Classifications
- **Lightweight agents**: Under 3k tokens - Low initialization cost
- **Medium-weight agents**: 10-15k tokens - Moderate initialization cost  
- **Heavy agents**: 25k+ tokens - High initialization cost

### Model Selection Strategy
**Conventional Pairings:**
- Haiku + Lightweight Agent: Frequent, simple tasks
- Sonnet + Medium Agent: Balanced approach for moderate complexity
- Opus + Heavy Agent: Complex analysis requiring maximum reasoning

**Experimental Opportunities:**
- Opus + Lightweight Agent: Surprising depth in simple tasks
- Haiku + Heavy Agent: New paths through complex workflows

## When to Use Custom Agents

### Specialized Domain Tasks
- Code Review (security, performance, maintainability)
- Research Tasks (API docs, library comparison)
- Quality Assurance (testing strategies, edge cases)
- Documentation (technical writing, SEO, accessibility)
- Design Analysis (UX review, layout assessment)
- Content Quality (legibility, grammar, brand voice)

### Portable Workflows
- Cross-project standards enforcement
- Team workflow standardization
- Personal expertise amplification
- Community knowledge sharing

## Essential Features

### No CLAUDE.md Inheritance
Custom agents don't automatically inherit project CLAUDE.md configuration, preventing context pollution and ensuring consistent behavior across projects.

### Agent Nicknaming
Configure short nicknames for efficiency:
```
UX agent (A1) - Quick UX analysis
Security agent (S1) - Rapid security review
Performance agent (P1) - Performance optimization
```

Usage: `ask agent a1 to review the navigation menu UX`

### Automatic Delegation
Agents are automatically invoked based on:
- Task description in your prompt
- Description field in agent configuration
- Current context and available tools

**Tool SEO**: Include terms like "use PROACTIVELY" or "MUST BE USED" in descriptions for better auto-activation.

## Design Best Practices

### Getting Started Strategy
1. **Token-First Design**: Create focused, single-purpose agents initially
2. Start with lightweight agents for maximum composability
3. Use clear, specific descriptions for reliable auto-activation
4. Grant only necessary tools initially
5. Test agents in isolation before deployment

### Configuration Guidelines
- Choose appropriate models based on complexity
- Include examples in system prompts
- Design for chainability and multi-agent workflows
- Match model to agent weight for optimal cost/performance
- Test frequently and share with others for validation

### Model Selection Framework
1. **Start with conventional pairing**: Establish baseline performance
2. **Cross-experiment**: Test unconventional model/agent combinations
3. **Measure everything**: Token usage, cost, speed, quality, satisfaction
4. **Share discoveries**: Contribute findings to expand collective knowledge
5. **Iterate based on data**: Let empirical results guide optimization

## Key Takeaways

- **Efficiency matters**: Lightweight agents are more composable and frequently used
- **Experimental approach**: Don't let optimization assumptions limit discovery
- **Foundation first**: Master fundamentals before complex chaining
- **Community collaboration**: Share benchmarking results and discoveries
- **Start simple**: Begin with one focused agent that solves a specific recurring problem

## Advanced Workflows

### Multi-Agent Coordination
```
ask A1, P2, C1 to review the changes
```

### Agent Chainability
Heavy agents (25k+ tokens) create bottlenecks, while lightweight agents enable fluid orchestration. Balance specialized high-cost agents with efficient ones using a "big.LITTLE" approach.

## Task/Agent Tools

### The Task Tool - Claude's Most Powerful Tool

The Task tool enables Claude to efficiently delegate tasks to sub-agents for:
- Basic file reads and writes
- Code searches and file analysis
- Bash operations
- Research tasks

### Performance Benefits

**Main Agent Limitations:**
- Interactive nature with human response latency
- Switching between operation types reduces efficiency
- Various overheads slow down task execution

**Sub-Agent Advantages:**
- Parallel execution capabilities
- Specialized focus on specific operations
- Reduced context switching overhead

### Current Usage Patterns

Claude uses sub-agents cautiously, primarily for:
- Reading files
- Fetching web content  
- Searching for specific text patterns
- Operations where write conflicts are unlikely

### Maximizing Sub-Agent Usage

**Multi-Threading Mindset:** Like programming with threads, explicit orchestration of delegated steps yields best results.

**Key Strategies:**
1. **Provide explicit steps** including which will be delegated to sub-agents
2. **Balance token costs** with performance gains
3. **Group related tasks** rather than creating separate agents for every operation
4. **Specify parallel execution** when appropriate

### Parallel Feature Implementation Workflow

**7-Parallel-Task Method:**
1. **Component**: Create main component file
2. **Styles**: Create component styles/CSS
3. **Tests**: Create test files  
4. **Types**: Create type definitions
5. **Hooks**: Create custom hooks/utilities
6. **Integration**: Update routing, imports, exports
7. **Remaining**: Update package.json, documentation, configuration files
8. **Review and Validation**: Coordinate integration, run tests, verify build, check for conflicts

### Context Optimization Rules

- Strip out comments when reading code files for analysis
- Each task handles ONLY specified files or file types
- Task 7 combines small config/doc updates to prevent over-splitting
- Make MINIMAL CHANGES to existing patterns and structures
- Preserve existing naming conventions and file organization

### Implementation Guidelines

**Priority Rules:**
- **IMMEDIATE EXECUTION**: Launch parallel Tasks immediately upon feature requests
- **NO CLARIFICATION**: Skip asking what type of implementation unless absolutely critical
- **PARALLEL BY DEFAULT**: Always use 7-parallel-Task method for efficiency

**Code Quality:**
- Follow project's established architecture and component patterns
- Use existing utility functions and avoid duplicating functionality
- Preserve existing naming conventions and file organization

## Split Role Sub-Agents

### The Role Foundation

Anthropic recommends providing Claude with specific roles to optimize performance:
```
Your role is as a seasoned security expert which specialises in pen testing.
```

### Native Implementation Strategy

**Sub-Agent Coordination Process:**
1. **Setup Phase** - Ensure Claude is in Plan Mode with ultrathink instantiated
2. **Role Suggestion** - Claude automatically suggests relevant roles for the task
3. **Perspective Selection** - Select specific perspectives for task review
4. **Parallel Analysis** - Sub-agents complete specialized reviews simultaneously
5. **Consolidation** - Findings are consolidated and presented by Claude

### Perspective Selection Examples

**Code Review Tasks:**
```
Create sub-agents and analyse the problem from the following perspectives: 
factual, senior engineer, security expert, consistency reviewer, redundancy checker
```

**User Experience Tasks:**
```
Create sub-agents and analyse the problem from a: 
creative, nooby user, designer, marketing, seo perspective
```

**Documentation Tasks:**
```
Create sub-agents to review this documentation from the following perspectives:
technical accuracy, beginner accessibility, SEO optimization, content clarity
```

### Tool Selection by Role

Each perspective naturally gravitates toward different tools based on their domain expertise:
- Security experts focus on vulnerability analysis tools
- UX designers prioritize user interaction patterns
- SEO specialists examine content structure and metadata
- Technical reviewers analyze code quality and architecture

This natural tool selection creates comprehensive analysis as different agents instinctively choose the most relevant tool combinations.

### Performance & Cost Optimization

**Strategic Value:**
- Maximizes Claude 4 Sonnet capabilities through orchestration
- Avoids reaching for 5x more expensive Opus model
- Parallel Task execution enables simultaneous multi-expert analysis
- Prevents context pollution from sequential single-role analysis

**Cost-Effective Formula:**
```
Claude 4 Sonnet + Plan Mode + ultrathink + split role sub-agents = Maximum performance before Opus
```

### Beyond Coding Applications

Split role sub-agents apply to any domain:
- **Content Creation**: noob, SEO, engineer, vibe coder, non-coder perspectives
- **Business Analysis**: technical, marketing, user, financial perspectives  
- **Product Development**: creative, practical, security, accessibility perspectives

### Multi-Perspective Analysis Benefits

**Key Advantages:**
- Surfaces insights no single Claude instance could discover alone
- Each role uses different approaches and tools
- Creates comprehensive analysis improving decision quality
- Scalable to any domain or problem type

### Best Practices

1. **Start with fundamental technical perspectives**
2. **Experiment with creative role combinations**  
3. **Adapt perspective combinations to specific domains**
4. **Always Be Experimenting (A.B.E)** with new role configurations
5. **Use Plan Mode for optimal coordination**

### Experimental Approach

The beauty of split role sub-agents lies in their scalability - you can adapt perspective combinations to any domain or problem type. Discovery comes through experimentation with different role combinations to see what unique insights each reveals.

---

*Source: ClaudeLog - Agent Engineering Guide, Task/Agent Tools & Split Role Sub-Agents*
*Last updated: August 2025*