# Content Strategy Multi-Agent Framework

This is a multi-agent system for creating, reviewing, and improving educational content.

Inspired by [Brain: A Multi-Agent Framework by Ali Afshar](https://github.com/aliafshar/brain).

## Quick Start

To use the framework, provide a prompt with one of these triggers:

```bash
# Create new educational content
@gemini-multi-agent "CONTENT GOAL: Create a new class on JavaScript variables for beginner web developers"

# Review and analyze existing content  
@gemini-multi-agent "CONTENT REVIEW: Evaluate my existing lesson on CSS Grid for pedagogy alignment and engagement"

# Generate supporting materials
@gemini-multi-agent "CONTENT SUPPORT: Create mentor facilitation guide for Project A with discussion prompts"
```

## Required Files

Ensure these context files are present in `gemini-multi-agent` at the root of your project directory.

```
├── GEMINI.md                    # This framework (current file)
├── content_agents.md            # Agent personas and responsibilities  
├── pedagogical_framework.md     # Pedagogical framework and educational standards
├── lesson_template.md           # Mandatory lesson structure template
└── content_runs/                # Generated content directory
```

## Use Cases

### 1. Content Creation (`CONTENT GOAL:`)
Creates new educational content following pedagogical framework and lesson template.

**Workflow:** Strategy → Research → Planning → Writing → QA → Approval  
**Output:** Complete lesson with proper pedagogy mapping and learning objectives.

### 2. Content Review (`CONTENT REVIEW:`)
Analyzes existing content without modifying original files.

**Workflow:** Analysis → Audit → Assessment → Recommendations  
**Output:** Quality reports, improvement roadmaps, benchmarking analysis

### 3. Supporting Materials (`CONTENT SUPPORT:`)
Generates lesson plans, instructor guides, assessments, and learner resources.

**Workflow:** Requirements → Research → Design → Creation → Integration Testing  
**Output:** Complete instructional packages ready for classroom use

## Agent Team

### Leadership
- **ContentDirector**: Strategic vision and audience alignment
- **LearningExperienceDesigner**: Educational workflow and learning architecture
- **PedagogyExpert**: Pedagogical framework implementation and learning objective design

### Content Creation
- **SeniorTechnicalWriter**: Primary content creation using lesson template
- **JuniorTechnicalWriter**: Content editing, formatting, and template compliance
- **InstructionalDesigner**: Lesson plans and supporting material creation

### Quality & Research
- **SeniorResearcher**: Strategic research and source validation
- **JuniorResearcher**: Content research and example gathering
- **QualityAssuranceSpecialist**: Framework compliance and learning effectiveness
- **ContentEvaluationSpecialist**: Existing content analysis and improvement recommendations

## Output Structure

Each content run creates a timestamped directory:

```text
content_runs/YYYYMMDD_hhmmss_<short_goal>/
├── learning_brief.md
├── research_synthesis.md  
├── content_plan.md
├── content_deliverables/
└── quality_report.md
```

## Getting Started

1. Ensure all required context files are in place
2. Choose your content goal type (create, review, or support)
3. Provide specific, detailed prompts with appropriate triggers
4. Review generated content and provide feedback for improvements
