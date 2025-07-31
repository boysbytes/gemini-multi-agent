# Content Strategy Multi-Agent Framework

A collaborative AI framework for creating high-quality educational content using specialized agent personas.

> I cannot provide the pedagogical framework and content structure because they are not mine to share.

## Quick Start

1. **Set up context files** (required):
   - `content_agents.md` - Agent personas and responsibilities
   - `pedagogical_framework.md` - Educational principles and standards
   - `lesson_template.md` - Content structure template
   - `GEMINI.md` - Framework documentation

2. **Start a content run** with one of these triggers:
   ```
   CONTENT GOAL: Create a learning module on [topic]
   CONTENT REVIEW: Evaluate and improve existing [content]
   CONTENT SUPPORT: Develop supporting materials for [content]
   ```

3. **Agents collaborate** through 6 workflow stages:
   - Strategy & Learning Design
   - Research & Content Foundation  
   - Content Planning
   - Content Creation
   - Quality Assurance
   - Final Review & Delivery

## Output Structure

Each content run creates a timestamped directory with:

- **Transcript files** (append-only logs of agent interactions)
- **Planning documents** (learning objectives, research, task breakdown)
- **Final deliverables** (educational content and supporting materials)
- **Quality reports** (QA documentation and recommendations)

## Key Features

- **Specialized agents** for strategy, research, writing, and QA
- **Pedagogical framework** ensures educational effectiveness
- **Quality safeguards** prevent infinite revision loops
- **Flexible workflows** for creation, review, and support materials
- **Complete audit trail** through append-only transcripts

## Agent Roles

- **ContentDirector** - Strategic vision and final approval
- **LearningExperienceDesigner** - Learning architecture and progression
- **PedagogyExpert** - Educational framework compliance
- **SeniorResearcher** - Research strategy and synthesis
- **JuniorResearcher** - Data collection and source documentation
- **SeniorTechnicalWriter** - Content creation and development
- **JuniorTechnicalWriter** - Content editing and formatting
- **QualityAssuranceSpecialist** - Quality evaluation and approval
- **ContentProjectManager** - Task coordination and timeline management

## Loop Prevention

- Maximum 2 revision cycles per content item
- Deadlock detection after 3 consecutive agent interactions
- Automatic escalation and scope reduction protocols
- Session timeout after 10 interactions without progress