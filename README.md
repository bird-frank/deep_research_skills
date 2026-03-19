# Deep Research Skills

A pair of complementary skills for OpenClaw that enable comprehensive, automated deep research workflows.

## Skills Overview

### 1. deep-research

**Purpose:** Research planning and coordination skill

**Key Features:**

- **Two-phase workflow:** Planning → Execution
- **User collaboration:** Discusses and clarifies research questions with the user
- **Structured planning:** Creates detailed research plan documents
- **Scope definition:** Defines what to include/exclude in the research
- **Report specification:** Sets expectations for output format and depth

**How it works:**

1. **Phase 1 - Planning:** Collaborates with you to define research questions, scope, and report requirements
2. **Phase 2 - Execution:** Launches the `deep-research-executor` sub-agent to carry out the research based on the approved plan

**Use when:** You need comprehensive research on any topic with structured planning and detailed reporting

---

### 2. deep-research-executor

**Purpose:** Research execution specialist that performs comprehensive web searches and synthesizes findings

**Key Features:**

- **Bilingual search:** Searches in both Chinese and English for comprehensive coverage
- **Dynamic search:** Adds targeted searches based on initial findings
- **Source analysis:** Fetches and analyzes content from discovered sources
- **Citation tracking:** Maintains proper source citations throughout the report
- **Progressive reporting:** Builds the report incrementally during research

**How it works:**

1. Reads the research plan created by `deep-research`
2. Executes thorough web searches (minimum 12 diverse sources)
3. Analyzes and synthesizes findings from multiple sources
4. Generates a comprehensive report with proper citations
5. Appends the report entry to an index file

**Use when:** This skill is automatically invoked by `deep-research` during execution phase

## Installation

### Method 1: Install in OpenClaw via ClawHub

The easiest way to install these skills is through ClawHub in OpenClaw:

```bash
# Install deep-research (planning skill)
clawhub install deep-research

# Install deep-research-executor (execution skill)
clawhub install deep-research-executor
```

Or install both at once:

```bash
clawhub install deep-research deep-research-executor
```

### Method 2: Manual Installation

1. Clone or download this repository:

   ```bash
   git clone <repository-url>
   cd deep-research
   ```

2. Copy the skill directories to your OpenClaw skills folder:

   ```bash
   # Default OpenClaw skills location (adjust path as needed)
   cp -r skills/deep-research ~/.config/openclaw/skills/
   cp -r skills/deep-research-executor ~/.config/openclaw/skills/
   ```

3. Verify installation:

   ```bash
   openclaw --list-skills
   ```

   You should see both `deep-research` and `deep-research-executor` in the output.

## Usage

Once installed, simply ask OpenClaw to research a topic:

```
User: "Research the latest developments in quantum computing"
```

The `deep-research` skill will:

1. Discuss the topic with you to clarify research questions
2. Create a research plan based on your input
3. Wait for your approval before proceeding
4. Launch `deep-research-executor` to carry out the research
5. Deliver a comprehensive report with citations

## Workflow Example

```
User: "I want to understand the current state of renewable energy storage"

→ deep-research skill activates
→ Discusses research scope with user
→ Creates research plan (saved to plans/research-plan-{timestamp}.json)
→ User confirms the plan
→ Launches deep-research-executor
→ Executor performs bilingual searches
→ Analyzes 12+ sources
→ Generates report (saved to report/ds_renewable_energy_storage_{timestamp}.md)
→ Appends entry to index.md
→ Presents findings to user
```

## Requirements

- OpenClaw with skill support enabled
- Internet connection for web search capabilities
- Adequate storage for research plans and reports

## Directory Structure

When using these skills, the following directories will be created:

```
your-project/
├── plans/          # Research plan documents (JSON)
├── report/         # Generated research reports (Markdown)
└── index.md        # Index of all research reports
```

## Notes

- Both skills work together as a pair. Install both for full functionality.
- The `deep-research` skill handles planning and user interaction
- The `deep-research-executor` skill performs the actual research and report generation
- Research reports are always generated in English
- All sources are properly cited with reference numbers
