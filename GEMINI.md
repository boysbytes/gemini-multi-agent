# Content Strategy Multi-Agent Framework

The basic concept will be a "CONTENT GOAL" that will be analyzed, researched, designed, written, and quality-assured in a "content run". Each "content run" will have its own working directory in the content_runs subdirectory.

## Required Context Files

This framework depends on several context files that must be present:

*   **`content_agents.md`**: Defines all agent personas and their responsibilities
*   **`pedagogical_framework.md`**: Your specific educational framework, lesson flow requirements, and quality standards
*   **`lesson_template.md`**: Mandatory template structure for all lesson content creation
*   **`GEMINI.md`**: This framework documentation (current file)

All agents will reference the `pedagogical_framework.md` and `lesson_template.md` when making educational design decisions and creating content, ensuring consistency across all content work.

## Core Concepts

*   **Content Goal**: A learning objective or educational content requirement that needs to be researched, designed, written, and delivered.
*   **ContentItem**: A task to be completed by an agent. It has a `description`, assigned `agent`, `dependencies`, and a `result`.
*   **Content Run**: Manages the state for a given `Content Goal`. It tracks all `ContentItem`s, learning objectives, target audience, and other necessary state.
*   **Agent Persona**: A definition of an agent's capabilities, expertise, and personality, stored as a heading in the `content_agents.md` file.

## Content Run Directory & Artifacts

Each content run will have a unique directory inside the `content_runs` directory. The directory name will be prefixed with a timestamp in the format `YYYYMMDD_hhmmss_<short_content_goal>`, where `<short_content_goal>` is a brief, 10-20 character version of the content goal.

### Artifacts by Use Case

#### For Content Creation (`CONTENT GOAL:`)
*   **`content_transcript.md`**: Detailed log of all agent interactions during content development
*   **`learning_brief.md`**: Pedagogical foundation with learning objectives, audience analysis, and framework
*   **`research_synthesis.md`**: Comprehensive research findings and content insights
*   **`content_plan.md`**: Project breakdown with ContentItems, agent assignments, and dependencies
*   **`content_deliverables/`**: Final educational content in various formats
*   **`quality_report.md`**: Quality assurance documentation

#### For Content Review (`CONTENT REVIEW:`)
*   **`review_transcript.md`**: Detailed log of evaluation process and agent analysis
*   **`content_audit.md`**: Comprehensive assessment of existing content against quality criteria
*   **`pedagogical_assessment.md`**: Analysis of instructional design effectiveness and learning alignment
*   **`gap_analysis.md`**: Identification of content gaps, issues, and improvement opportunities
*   **`improvement_roadmap.md`**: Prioritized recommendations and implementation plan
*   **`benchmarking_report.md`**: Comparison against industry standards and best practices

#### For Supporting Materials (`CONTENT SUPPORT:`)
*   **`support_transcript.md`**: Development process documentation
*   **`materials_brief.md`**: Requirements and specifications for all supporting materials
*   **`instructor_package/`**: Complete instructor resources (lesson plans, guides, answer keys)
*   **`student_materials/`**: Learner resources (handouts, exercises, reference materials)
*   **`assessments/`**: All evaluation materials (quizzes, rubrics, project guidelines)
*   **`integration_guide.md`**: Instructions for using all materials together effectively

## Agent Communication & Task Management

### Task Notification Protocol (Streamlined)
All agents are notified of their assignments through a streamlined process:

1. **Batch Task Assignment**: ContentProjectManager logs all task assignments in single transcript entry
2. **Implicit Acknowledgment**: Agents acknowledge by beginning work (no separate confirmation step required)
3. **Dependency Auto-Check**: System verifies prerequisites are met before agents can start
4. **Progress Indicators**: Simple status updates (Not Started → In Progress → Complete) without detailed logging requirements

### Stage Transition Protocol
Clear handoff mechanisms ensure smooth transitions between workflow stages:

1. **Stage Completion Signal**: Completing stage agents log "READY FOR [NEXT STAGE]" with summary of deliverables
2. **Handoff Documentation**: Brief summary of key decisions, changes, and recommendations for next stage
3. **Receiving Stage Acknowledgment**: Next stage agents acknowledge receipt and review all predecessor outputs
4. **Readiness Confirmation**: Agents confirm they have all necessary inputs before beginning work

### ContentItem Execution Framework
Structured approach to task management:

1. **Task Reference**: Agents reference `content_plan.md` for their assigned ContentItems and specifications
2. **Dependency Check**: Verify all prerequisite ContentItems are complete and outputs are available
3. **Work Documentation**: Log all decisions, iterations, and rationale in the content transcript
4. **Quality Checkpoints**: Built-in review points with other agents as specified in dependencies
5. **Completion Notification**: Clear signal when ContentItem is ready for next stage or dependent tasks

## Staged Workflow

1.  **Initiation**:
    *   The user provides a `CONTENT GOAL:` prompt.
    *   All Agent Personas from `content_agents.md` are loaded.
    *   A `Content Run` is initiated, and its unique directory is created.

2.  **Stage 1: Content Strategy & Learning Design (Leadership Agents)**
    *   **Agents**: `ContentDirector`, `LearningExperienceDesigner`, `PedagogyExpert`
    *   **Process**: The leadership team collaborates to analyze the `CONTENT GOAL`, define learning objectives, identify target audience needs, and establish the pedagogical framework. Their detailed discussion is logged.
    *   **Output**: A refined content goal, clear learning objectives, pedagogical framework, and high-level content strategy documented in `learning_brief.md`.
    *   **Handoff**: **Append** to transcript "READY FOR STAGE 2: RESEARCH" with summary of learning objectives, target audience, and content strategy priorities.

3.  **Stage 2: Research & Content Foundation (Research Agents)**
    *   **Agents**: `SeniorResearcher`, `JuniorResearcher`
    *   **Process**: Research team acknowledges Stage 1 outputs and conducts comprehensive research to gather current, authoritative information to support the educational content. All research findings, source evaluation, and synthesis work is logged.
    *   **Output**: Comprehensive research findings documented in `research_synthesis.md` and a curated knowledge base for content creation.
    *   **Handoff**: **Append** to transcript "READY FOR STAGE 3: PROJECT PLANNING" with research summary and key content insights.

4.  **Stage 3: Content Planning (Project Management)**
    *   **Agents**: `ContentProjectManager`
    *   **Process**: The project manager acknowledges Stages 1-2 outputs and breaks down the learning objectives and content requirements into specific, actionable `ContentItem`s with clear dependencies, assigned agents, and deliverable specifications.
    *   **Output**: A comprehensive list of ContentItems with clear specifications and development timeline documented in `content_plan.md`.
    *   **Task Notification Process**:
        - **Append** task assignments to `content_transcript.md`: "TASK ASSIGNED: [Agent Name] - [ContentItem ID]: [Description]"
        - Include dependencies and expected deliverables for each assignment
        - Request agent acknowledgment before proceeding to Stage 4
    *   **Handoff**: **Append** to `content_transcript.md`: "READY FOR STAGE 4: CONTENT CREATION" after all agents acknowledge their assignments.

5.  **Stage 4: Content Creation (Writing Agents)**
    *   **Agents**: `SeniorTechnicalWriter`, `JuniorTechnicalWriter`
    *   **Process**: 
        - Writing agents acknowledge their assigned ContentItems from `content_plan.md`
        - Reference `learning_brief.md` (learning objectives and pedagogical framework) and `research_synthesis.md` (content foundation)
        - Create educational content following specifications from content planning
        - Update ContentItem status and log all content creation decisions and iterations
        - Coordinate with other agents as specified in ContentItem dependencies
    *   **Output**: Draft educational content and supporting materials stored in `content_deliverables/`.
    *   **Handoff**: **Append** to transcript "READY FOR STAGE 5: QUALITY ASSURANCE" with content creation summary and any issues encountered.

6.  **Stage 5: Quality Assurance & Optimization (QA and Analysis Agents)**
    *   **Agents**: `QualityAssuranceSpecialist`, `ContentAnalyst`
    *   **Process**: 
        - QA team acknowledges Stage 4 outputs and assigned review ContentItems
        - Systematically evaluate content against quality criteria, pedagogical effectiveness, and learner experience standards
        - Content analyst provides optimization recommendations
        - Update ContentItem status and document all findings
    *   **Output**: Quality-assured content with documented review results in `quality_report.md` and optimized final deliverables.
    *   **Handoff**: **Append** to transcript "READY FOR STAGE 6: FINAL REVIEW" with QA summary and revision recommendations.

7.  **Stage 6: Final Review & Delivery (Leadership Review)**
    *   **Agents**: `ContentDirector`, `PedagogyExpert`
    *   **Process**: 
        - Leadership team acknowledges all prior stage outputs
        - Conduct final strategic review using the `quality_report.md` to ensure content meets all requirements and learning objectives
        - If issues are identified, specify which ContentItems need revision and return to appropriate stage
        - Update all ContentItem statuses to reflect final decisions
    *   **Output**: 
        - **APPROVED**: Final educational content ready for delivery with all ContentItems marked "Complete"
        - **REVISION REQUIRED**: Content returns to specified stage with detailed feedback and ContentItems marked for rework
    *   **Loop Prevention**: Maximum of 2 revision cycles per ContentItem before escalation to ContentDirector for scope adjustment

## Content-Specific Considerations

### Learning-Centered Approach
- All content development is driven by clearly defined learning objectives
- Pedagogical principles guide every decision in content creation
- Assessment strategies are integrated throughout the development process

### Quality Focus
- Multi-layered quality assurance with specialized QA and content analysis roles
- Systematic evaluation against pedagogical standards and learner experience criteria
- Continuous improvement feedback loops built into the process

### Research-Driven Content
- Comprehensive research phase ensures content accuracy and currency
- Source validation and credibility assessment are integral to the process
- Research synthesis creates a solid foundation for content creation

### Collaborative Expertise
- Cross-functional collaboration between pedagogical experts, researchers, writers, and QA specialists
- Clear handoffs and communication protocols between specialized roles
- Shared accountability for educational content quality and effectiveness

## Multiple Use Cases & Execution Triggers

The framework supports several types of content work through different trigger phrases:

### 1. Content Creation
**Trigger:** `CONTENT GOAL:`
**Purpose:** Create new educational content from scratch

**Example:**
```
CONTENT GOAL: Create a comprehensive learning module on "Introduction to Machine Learning" for software developers with 2-3 years of experience who have basic statistics knowledge but no ML background.
```

### 2. Content Evaluation & Improvement
**Trigger:** `CONTENT REVIEW:`
**Purpose:** Evaluate, analyze, and improve existing educational content

**Example:**
```
CONTENT REVIEW: Analyze the effectiveness of our "Python Fundamentals" course materials, identify learning gaps, assess pedagogical alignment, and recommend improvements for better learner outcomes.
```

### 3. Supporting Materials Development
**Trigger:** `CONTENT SUPPORT:`
**Purpose:** Create lesson plans, instructor guides, assessments, exercises, and other supporting materials

**Example:**
```
CONTENT SUPPORT: Develop a complete instructor package for the "Data Structures" module including lesson plans, lab exercises, assessment rubrics, and student handouts.
```

## Adapted Workflows by Use Case

### Content Review Workflow
1. **Stage 1: Content Analysis Strategy** - Leadership team defines evaluation criteria and methodology
2. **Stage 2: Content Audit & Research** - Research team analyzes existing content and benchmarks against current best practices
3. **Stage 3: Pedagogical Assessment** - Pedagogy Expert evaluates instructional design and learning effectiveness
4. **Stage 4: Quality & Experience Evaluation** - QA team assesses content quality, accessibility, and learner experience
5. **Stage 5: Gap Analysis & Recommendations** - Content Analyst identifies improvement opportunities
6. **Stage 6: Improvement Implementation** - Writing team implements recommended changes

### Supporting Materials Workflow
1. **Stage 1: Support Requirements Analysis** - Leadership team defines what supporting materials are needed and their purpose
2. **Stage 2: Curriculum Integration Research** - Research team ensures materials align with main content and educational standards
3. **Stage 3: Material Design & Planning** - Project management breaks down deliverables (lesson plans, exercises, assessments, etc.)
4. **Stage 4: Material Creation** - Writing team creates all supporting materials following pedagogical guidelines
5. **Stage 5: Integration Testing** - QA team ensures materials work seamlessly with main content
6. **Stage 6: Final Package Assembly** - All materials are compiled into a complete educational package

## Loop Prevention & Efficiency Safeguards

### Revision Cycle Limits
- **Maximum 2 revision cycles** per ContentItem before escalation to ContentDirector for scope adjustment
- **Time-boxing**: Each stage has maximum duration based on content complexity
- **Escalation Protocol**: Persistent issues trigger leadership intervention rather than continued loops

### Agent Coordination Rules
- **Single Point of Truth**: Only one agent updates ContentItem status at a time
- **Dependency Verification**: Automated checks prevent circular dependencies in content_plan.md
- **Acknowledgment Efficiency**: Agents acknowledge in batch rather than individual confirmations

### Quality Gate Optimization
- **Risk-Based Reviews**: High-risk ContentItems get full review; low-risk get spot checks
- **Parallel Processing**: Independent ContentItems can be worked on simultaneously
- **Review Consolidation**: Multiple small reviews combined into single comprehensive review

### Emergency Protocols
- **Deadlock Detection**: If no progress after 3 consecutive agent interactions, ContentDirector intervenes
- **Stall Prevention**: If same ContentItem fails review twice, automatic escalation to simplified requirements
- **Session Timeout**: If workflow stalls for more than 10 interactions without deliverable progress, trigger scope reduction
- **Quality Threshold**: Minimum acceptable quality standard to prevent perfectionism loops

### Transcript Logging Requirements
All agent interactions must be logged in the appropriate transcript file with:
- Timestamp and agent identification
- Clear stage and ContentItem references
- Decision rationale and key insights
- Handoff signals and status updates
- Any issues or blockers encountered

### Status Update Format
ContentItem status updates should follow this format:
```
[TIMESTAMP] [AGENT]: ContentItem [ID] - Status: [STATUS]
Details: [Brief description of work completed or issues]
Next Steps: [What happens next or dependencies waiting]
```

### Handoff Documentation Template
Stage completion handoffs should include:
```
[TIMESTAMP] [AGENT]: READY FOR [NEXT STAGE]
Deliverables: [List of completed outputs]
Key Decisions: [Important choices made that affect next stage]
Recommendations: [Guidance for next stage agents]
Issues/Blockers: [Any concerns or unresolved items]
```