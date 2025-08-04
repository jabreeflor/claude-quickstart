# Context Engineering

## Overview

Context engineering represents the evolution from individual prompt optimization to comprehensive context management. This discipline focuses on the art and science of filling the context window with precisely the right information to achieve desired outcomes across extended interactions and complex workflows.

Unlike traditional prompt engineering, which focuses primarily on crafting input prompts, context engineering takes a holistic approach to managing all elements that influence an AI model's behavior and responses.

## Core Philosophy

> "Context engineering is the delicate art and science of filling the context window with just the right information for the next step." — Andrej Karpathy

Context engineering is the practice of designing and optimizing the entire context window of large language models (LLMs) to achieve desired outcomes through systematic information management rather than ad-hoc "vibe coding" approaches.

## Key Concepts

### CLAUDE.md Integration

CLAUDE.md is a special file that Claude automatically pulls into context when starting a conversation. This file serves as the foundation for project-wide context management.

#### CLAUDE.md Best Practices

**What to Include:**
- **Project Awareness**: Reading planning docs, checking tasks
- **Code Structure**: File size limits, module organization  
- **Testing Requirements**: Unit test patterns, coverage expectations
- **Style Conventions**: Language preferences, formatting rules
- **Documentation Standards**: Docstring formats, commenting practices
- **Bash Commands**: Frequently used project commands
- **Core Files**: Key utility functions and their locations
- **Repository Etiquette**: Git workflow, branch naming, commit standards

**Optimization Strategies:**
- Keep files concise and human-readable
- Use emphasis words like "IMPORTANT" or "YOU MUST" for critical instructions
- Refine CLAUDE.md like any frequently used prompt
- Use the `#` key to quickly add instructions during sessions
- Occasionally run content through a "prompt improver"
- Treat as a living document that evolves with project needs

#### CLAUDE.md Placement Options

CLAUDE.md can be strategically placed at different levels:
- **Root of repository**: Project-wide context
- **Parent directories**: Inherited context across related projects  
- **Child directories**: Subdirectory-specific context
- **Home folder** (`~/.claude/CLAUDE.md`): Personal global context

### Memory Management

Context engineering optimizes the AI's context window through intelligent information management, deciding what matters most, trimming noise, and structuring data effectively.

#### Context Compression Techniques

**Summary Compression:**
- After every few interactions, summarize and use summaries going forward
- Retain only tokens required to perform the current task
- Claude automatically implements this for lengthy conversations
- Preserves essential state while discarding noise

**Progressive Summarization:**
- Start with detailed context for immediate tasks
- Gradually compress older information into summaries
- Maintain critical decision points and key insights
- Refresh context periodically to prevent rot

#### Context Pruning and Refresh

**Systematic Approach:**
1. **Regular Summaries**: Create instance summaries at logical breakpoints
2. **Context Refresh**: Spin up new instances with fresh context
3. **State Preservation**: Feed in summaries of previous instances
4. **Garbage Collection**: Remove noise while preserving essential information

### Context Window Optimization

#### Multi-Component Context Management

Context engineering manages three primary information streams:

1. **Instructional Context**
   - System prompts and role instructions
   - Few-shot examples and templates
   - Task-specific guidance and constraints

2. **Knowledge Context**
   - Domain information and facts
   - Retrieved information from external sources
   - Project-specific knowledge and patterns

3. **Tools Context**
   - Information from model's environment
   - API responses and tool outputs
   - Real-time data and system state

#### Context Allocation Strategy

**Priority-Based Allocation:**
- Reserve space for critical project context
- Allocate tokens based on immediate task needs
- Maintain buffer for tool outputs and responses
- Implement context rotation for long sessions

### Project-Specific Context

#### Context Engineering vs Vibe Coding

**Traditional "Vibe Coding":**
- Ad-hoc context flooding
- Inconsistent information quality
- Context window waste
- Unpredictable performance

**Context Engineering:**
- Systematic context management
- Curated, relevant information
- Efficient token usage
- Predictable, enhanced performance

#### Performance Benefits

Claude Code and AI tools perform significantly better with relevant context:
- **Enhanced Accuracy**: Better understanding of project requirements
- **Improved Consistency**: Maintained coding standards and patterns
- **Faster Execution**: Reduced need for clarification and rework
- **Better Integration**: Understanding of existing codebase and architecture

## Context Management Strategies

### 1. Write Strategy

**External Context Persistence:**
- Save context outside the context window
- Use "scratchpad" note-taking approach
- Persist information across task boundaries
- Enable complex, multi-step workflows

**Implementation:**
- Document decision rationale
- Track progress and intermediate results
- Maintain state across context refreshes
- Create searchable context repositories

### 2. Context Streaming

**Dynamic Context Updates:**
- Stream relevant information as needed
- Just-in-time context loading
- Adaptive context based on current focus
- Minimize context window waste

### 3. Hierarchical Context

**Layered Information Architecture:**
- Global project context (CLAUDE.md)
- Module-specific context
- Function-level documentation
- Task-specific instructions

## Tools and Techniques

### Context Engineering Workflows

#### Product Requirements Prompts (PRPs)
Systematic approach to context engineering through structured requirements:
- Define project scope and constraints
- Establish success criteria
- Document dependencies and assumptions
- Create reusable context templates

#### Context Validation and Testing
- A/B test different context configurations
- Measure performance impact of context changes
- Validate context effectiveness across use cases
- Maintain context performance metrics

### Integration with Claude Code

#### CLAUDE.md Enhancement Features
- Use `#` key for rapid context updates
- Leverage automatic context inheritance
- Implement context versioning
- Monitor context effectiveness

#### Extended Thinking Integration
- Maintain context across thinking sessions
- Build upon previous analysis and decisions
- Create persistent knowledge graphs
- Support complex reasoning workflows

## Advanced Strategies

### Context Orchestration

**Multi-Agent Context Coordination:**
- Share context between specialized agents
- Maintain consistency across agent interactions
- Coordinate context updates and changes
- Prevent context conflicts and duplication

**Context Pipeline Management:**
- Sequential context processing
- Context transformation and enrichment
- Quality gates for context validation
- Automated context optimization

### Adaptive Context Systems

**Learning Context Patterns:**
- Analyze successful context configurations
- Identify optimal context structures
- Adapt context based on task performance
- Continuous context improvement

**Context Personalization:**
- Tailor context to individual preferences
- Learn from interaction patterns
- Customize context density and focus
- Optimize for specific use cases

### Context Security and Privacy

**Information Filtering:**
- Remove sensitive information from context
- Implement context access controls
- Audit context for security risks
- Maintain context compliance standards

**Context Isolation:**
- Separate contexts for different projects
- Prevent context leakage between sessions
- Implement context sandboxing
- Secure context storage and transmission

## Best Practices Summary

### Context Design Principles
1. **Relevance First**: Include only information that directly supports current objectives
2. **Hierarchical Organization**: Structure context from general to specific
3. **Dynamic Management**: Adapt context based on evolving needs
4. **Quality over Quantity**: Prefer curated, high-quality information
5. **Maintainability**: Design context for easy updates and modifications

### Implementation Guidelines
1. **Start Simple**: Begin with basic project context and expand iteratively
2. **Measure Impact**: Track performance improvements from context engineering
3. **Document Patterns**: Record successful context configurations for reuse
4. **Regular Maintenance**: Update and refresh context periodically
5. **User Feedback**: Incorporate feedback to improve context effectiveness

### Common Pitfalls to Avoid
- **Context Flooding**: Overwhelming the context window with irrelevant information
- **Static Context**: Failing to update context as projects evolve
- **Inconsistent Structure**: Using different context formats across projects
- **Over-Optimization**: Spending more time on context than actual work
- **Context Rot**: Allowing outdated information to persist in context

---

## References

### Academic Sources

[^1]: Zhang, Wei, et al. "A Survey of Context Engineering for Large Language Models." *arXiv preprint arXiv:2507.13334*, July 2025. https://arxiv.org/abs/2507.13334

[^2]: Dong, Qingxiu, et al. "A Survey on In-context Learning." *arXiv preprint arXiv:2301.00234*, January 2023. https://arxiv.org/abs/2301.00234

### Official Documentation

[^3]: Anthropic. "Claude Code Best Practices." Anthropic Engineering Blog, April 2025. https://www.anthropic.com/engineering/claude-code-best-practices

[^4]: Anthropic. "Manage Claude's Memory." Claude Code Documentation, 2025. https://docs.anthropic.com/en/docs/claude-code/memory

[^5]: Anthropic. "Claude Code Overview." Official Documentation, 2025. https://docs.anthropic.com/en/docs/claude-code/overview

### Industry Perspectives

[^6]: Karpathy, Andrej. "Context engineering is the delicate art and science of filling the context window with just the right information for the next step." X (Twitter), January 2025. https://x.com/karpathy/status/1937902205765607626

[^7]: Kimai, David. "Context Engineering: A First-Principles Handbook." GitHub Repository, 2025. https://github.com/davidkimai/Context-Engineering

[^8]: Vijay Kumar, A B. "Practical Context Engineering for Vibe Coding with Claude Code." *Medium*, July 2025. https://abvijaykumar.medium.com/practical-context-engineering-for-vibe-coding-with-claude-code-6aac4ee77f81

[^9]: Kadous, Waleed. "Give Claude Code Context: One Principle, Many Implications." *Medium*, March 2025. https://waleedk.medium.com/give-claude-code-context-one-principle-many-implications-b7372d0a4268

[^10]: Masood, Adnan. "Context Engineering: Elevating AI Strategy from Prompt Crafting to Enterprise Competence." *Medium*, June 2025. https://medium.com/@adnanmasood/context-engineering-elevating-ai-strategy-from-prompt-crafting-to-enterprise-competence-b036d3f7f76f

[^11]: LangChain. "Context Engineering for Agents." LangChain Blog, 2025. https://blog.langchain.com/context-engineering-for-agents/

### Community Resources

[^12]: Meirtz. "Awesome Context Engineering: Comprehensive survey on Context Engineering." GitHub Repository, 2025. https://github.com/Meirtz/Awesome-Context-Engineering

*Context engineering provides the systematic foundation for managing AI interactions at scale. Combined with prompt engineering fundamentals and agent engineering patterns, it enables sophisticated AI-assisted workflows that maintain consistency and quality across complex projects.*