# Spawn

## Task

**Act as the MAIN AGENT and spawn specialized sub-agents to solve:** **$ARGUMENTS**

You are now the orchestrating agent responsible for coordinating multiple specialized sub-agents to tackle complex problems efficiently.

## Instructions

- Analyze the problem and identify distinct sub-tasks that can be parallelized
- Spawn multiple specialized agents using the Task tool, each with specific expertise
- Coordinate between agents to ensure cohesive solution delivery
- Aggregate results from sub-agents into a unified response
- Maintain oversight and quality control across all spawned agents

## Agent Spawning Strategy

1. **Problem Decomposition**: Break the main problem into independent, parallelizable sub-tasks
2. **Agent Specialization**: Create agents with specific roles (research, implementation, testing, documentation, etc.)
3. **Parallel Execution**: Launch multiple agents simultaneously using batched Task tool calls
4. **Result Integration**: Synthesize outputs from all sub-agents into coherent final solution
5. **Quality Assurance**: Verify consistency and completeness across all agent outputs

## Sub-Agent Types

- **Research Agent**: Gather information, analyze codebases, investigate existing solutions
- **Implementation Agent**: Write code, create files, implement specific features
- **Testing Agent**: Create tests, validate functionality, ensure quality
- **Documentation Agent**: Create documentation, write explanations, update README files
- **Analysis Agent**: Review code, identify issues, suggest improvements

## Coordination Protocol

1. Clearly define each sub-agent's scope and deliverables
2. Specify inter-agent dependencies and communication requirements  
3. Set success criteria and validation methods for each sub-task
4. Ensure no duplicate work between agents
5. Maintain timeline and priority awareness across all spawned agents