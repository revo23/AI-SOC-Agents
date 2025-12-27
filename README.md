# AI SOC Agents

<img width="524" height="524" alt="image" src="https://github.com/user-attachments/assets/de5b7986-9114-4d3a-af30-3c308f8ae7a1" />

**Overview**  
Tackling one of the most critical challenges in cybersecurity operations: context gathering (correlation between various data sources) and alert fatigue. Context gathering is a fundamental part of detection and response; most of the time it is also tedious and repetitive, making it well-suited for handling by AI agents.

**Versus current automation (SOAR)**

| Capability | SOAR Playbook | AI Agent |  
| -------- | ------- | ---------|
| Planning  | Fixed script | Dynamic planning    |  
| Scenarios | Anticipates specific cases     | Adapts to novel situations    | 
| Edge cases| Breaks when off-script    |  Re-plans when unexpected    | 
| Context  | No understanding    | Reasons about business/threat context    |  
| Integration | Rigid API calls     | Flexible tool use    | 
| Maintenance| Rewrite scripts    |  Update goals/tools/knowledge    | 

**Versus Agentic SOC**  
AI SOC Agents: AI tools or models deployed within a SOC (Security Operations Center) that assist analysts. They are generally task-specific and reactive, performing functions like alert triage, log correlation, or threat enrichment.  

Agentic SOC: A SOC framework where AI operates more autonomously as “agents” with goals, decision-making ability, and the capacity to orchestrate actions across multiple systems. Think AI-driven SOC operations rather than AI-assisted SOC operations.  
