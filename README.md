# BPEL Transformation Agent

A specialized agent for transforming Oracle BPEL (Business Process Execution Language) processes into comprehensive, implementation-ready Product Requirements Documents (PRDs). This agent extracts complete business logic, integration patterns, and orchestration semantics from BPEL XML files, enabling engineers to re-implement processes in modern workflow orchestration systems with 100% feature parity.

## Purpose

This agent serves as a senior systems analyst and product architect with deep expertise in:
- Oracle BPEL 2.0 (OASIS WS-BPEL) XML processes
- SOA architectures and integration patterns
- Modern workflow orchestration systems (Python/Temporal, Node.js/Camunda, Go/Cadence)
- Business process modeling and transformation

## Key Capabilities

### Comprehensive BPEL Analysis
- **Process Parsing**: Deep understanding of Oracle BPEL 2.0 (OASIS WS-BPEL) XML structures
- **Integration Extraction**: Complete mapping of partner links, WSDL bindings, and service operations
- **Data Flow Documentation**: Full data contracts with variable schemas, message types, and transformations
- **Control Flow Analysis**: Sequences, parallel flows, loops, decisions, and conditional branching
- **Fault Handling**: Comprehensive documentation of error handling, compensation, and recovery logic
- **Correlation Sets**: Extraction of message routing and process instance correlation patterns
- **Human Tasks**: Documentation of Oracle BPM human task extensions and approval workflows

### Output Generation
- **Markdown PRDs**: Exhaustive, implementation-ready documentation with zero ambiguity
- **JSON Summaries**: Machine-readable structured data for automation and tooling
- **Pseudocode**: Implementation-ready code examples for target platforms
- **Test Plans**: Unit tests, integration tests, and edge case scenarios
- **Gap Analysis**: Explicit documentation of unknowns, assumptions, and clarification needs

### Technical Extraction
- **XPath Preservation**: Exact extraction of XPath/XQuery expressions with namespace context
- **WSDL Mapping**: Complete service contract documentation from WSDL definitions
- **XSD Schema Resolution**: Full data structure documentation from XML schemas
- **Transaction Boundaries**: Identification of scopes, isolation levels, and transaction contexts
- **Compensation Logic**: Saga pattern documentation with reverse operations

## Usage

### Basic Transformation
```bash
# Transform a single BPEL file
genaiscript run bpel-transformer --vars input=order-process.bpel

# Transform with WSDL context
genaiscript run bpel-transformer --vars bpel=process.bpel wsdl=services.wsdl

# Generate JSON summary
genaiscript run bpel-transformer --vars input=process.bpel format=json > summary.json
```

### Batch Processing
```bash
# Transform multiple processes
for file in bpel/*.bpel; do
  genaiscript run bpel-transformer --vars input="$file" output="prds/$(basename $file .bpel).md"
done
```

### Validation
```bash
# Test on sample BPEL
genaiscript run bpel-transformer --vars input=test/sample-order.bpel

# Verify completeness
# (Example placeholder: implement your own validation script in package.json)
npm run validate:prd-completeness

# Check for gaps
grep -i "gap\|assumption\|unclear" prds/*.md
```

## Project Structure

```
bpel-agent/
├── bpel/              # Source BPEL process files (input)
├── wsdl/              # WSDL service definitions (reference)
├── xsd/               # XML schema definitions (reference)
├── prds/              # Generated Product Requirements Documents (output)
├── summaries/         # Machine-readable JSON summaries (output)
└── .github/
    └── agents/
        └── bpel-prd-agent.md  # Agent instructions and configuration
```

## Core Principles

1. **Exhaustive Extraction**: Capture EVERY detail from the BPEL—nothing left to interpretation
2. **Implementation-Ready**: PRDs must be directly implementable without returning to source BPEL
3. **Zero Ambiguity**: If anything is unclear, explicitly mark in Gaps & Assumptions with specific questions
4. **Preserve Semantics**: Maintain exact business logic, including XPath expressions and conditions
5. **Feature Parity Focus**: Document everything needed for identical behavior in target stack
6. **Machine-Readable**: Include structured JSON for automation and validation
7. **Cross-Process Awareness**: Handle multi-file BPEL solutions with call chains

## Input Expectations

The agent processes:
- **Primary Input**: Oracle BPEL XML process files (OASIS WS-BPEL 2.0)
- **Optional Context**: Referenced WSDLs and XSDs for complete type resolution
- **Format**: BPEL XML with standard namespaces (bpel:, tns:, etc.)

Supported BPEL elements include:
- Partner links with WSDL bindings
- Variables (messageType, type, element attributes)
- Correlation sets and properties
- Activities: receive, invoke, reply, assign, transform
- Control flow: sequence, flow, pick, while, repeatUntil, forEach
- Decision logic: if, switch with XPath conditions
- Fault handlers: catch, catchAll, throw, rethrow
- Compensation handlers and scopes
- Event handlers: onMessage, onAlarm
- Human task extensions (Oracle BPM)

## Output Format

### Comprehensive PRD Sections
1. **Executive Summary**: Business purpose, triggers, outcomes, and key integrations
2. **Actors & Integrations**: Complete partner link mapping with operations and patterns
3. **Data Contracts**: Full variable schemas with field structures and validation rules
4. **Orchestration Logic**: Happy path narratives, state machines, and sequence diagrams
5. **Control Flow Details**: Sequences, parallel blocks, decisions, loops, and timers
6. **Data Transformations**: Complete assign/copy operations with XPath expressions
7. **Fault Handling & Recovery**: Error paths, catch handlers, retry logic, and compensation
8. **Correlation & Idempotency**: Correlation sets and deduplication strategies
9. **Human Tasks**: Task definitions, outcomes, and approval workflows
10. **Non-Functional Requirements**: SLAs, timeouts, security, observability, and scalability
11. **Pseudocode**: Implementation-ready code for target platforms
12. **Test Plan**: Unit tests, integration tests, golden paths, and edge cases
13. **Gaps & Assumptions**: Explicit callouts of unknowns with risk assessment
14. **Glossary**: Domain terms and technical definitions

### Machine-Readable JSON
Structured output includes:
- Process metadata and namespaces
- Partner definitions and operations
- Variable schemas with field types
- Entry points and invocations
- Decisions, loops, and timers
- Fault and compensation handlers
- Correlation sets and human tasks
- Documented assumptions and gaps

## Quality Standards

### Completeness Checklist
- ✅ Every variable documented with full schema
- ✅ Every XPath expression preserved verbatim
- ✅ Every partner link mapped to operations
- ✅ All fault handlers documented
- ✅ All compensation logic captured
- ✅ All correlation sets explained

### Clarity Requirements
- ✅ No ambiguous statements
- ✅ Concrete examples provided
- ✅ Technical jargon defined in glossary
- ✅ Step-by-step narrative walkthrough
- ✅ Decision tables for all conditionals

### Implementation-Readiness
- ✅ Pseudocode directly translatable to target language
- ✅ Data contracts specify all fields with types
- ✅ Integration contracts complete with request/response shapes
- ✅ Error handling fully specified
- ✅ Test cases cover happy path and edge cases

### Accuracy Guarantees
- ✅ XPath expressions quoted exactly as in BPEL
- ✅ Namespace prefixes preserved with mappings
- ✅ Activity order matches BPEL sequence
- ✅ No invented details (marked as assumptions if inferred)

## Target Stack Mapping

The agent provides guidance for implementing BPEL processes in modern platforms:

| BPEL Construct | Python/Temporal | Node.js/Camunda | Go/Cadence |
|----------------|-----------------|-----------------|------------|
| receive (createInstance) | Workflow start signal | Start event | Workflow entry |
| invoke (sync) | Activity function | Service task | Activity call |
| invoke (async) | Child workflow | Call activity | Child workflow |
| assign | Local variables | Variables | Workflow state |
| flow (parallel) | Parallel activities | Parallel gateway | Go routines (workflow.Go) |
| while/repeatUntil | While loop | Loop task | For loop |
| pick/onAlarm | Timer + signal | Event-based gateway | Selector with timer |
| compensation | Saga pattern | Compensation event | Defer compensation |
| correlation | Workflow ID + search attributes | Business key | Workflow ID + query |

## Boundaries and Limitations

### ✅ Always Does
- Parse BPEL exhaustively—capture every element
- Preserve XPath/XQuery expressions exactly
- Document all partnerLinks, variables, activities
- Mark gaps and assumptions explicitly with questions
- Generate machine-readable JSON summary
- Maintain zero ambiguity in PRD
- Include implementation pseudocode
- Trace complete data flows
- Document fault and compensation handlers

### ⚠️ Asks First
- Infer business logic not explicit in BPEL
- Suggest refactoring or modernization
- Recommend architectural changes
- Combine multiple processes without explicit mapping
- Make assumptions about external system behavior
- Modify BPEL source files

### 🚫 Never Does
- Fabricate information not in BPEL
- Omit BPEL elements or activities
- Modify XPath expressions
- Skip fault handlers or edge cases
- Assume behavior without marking as assumption
- Create incomplete data contracts
- Ignore namespace context
- Simplify complex logic without noting

## Success Criteria

A successful PRD enables:
- ✅ Engineers implement in target stack WITHOUT referring back to BPEL XML
- ✅ QA validates feature parity using the test plan
- ✅ Product confirms business logic is preserved
- ✅ Operations configures observability from NFRs
- ✅ Automated tools parse JSON for migration pipelines

**Goal**: The generated PRD becomes the source of truth, making the original BPEL XML obsolete for implementation purposes.

## Git Workflow

### BPEL Analysis Workflow
1. **Place**: Add BPEL files to `bpel/` directory
2. **Transform**: Run bpel-transformer on each process
3. **Review**: Technical architect reviews PRD for completeness
4. **Gaps**: Document unclear/missing requirements
5. **Commit**: Save PRD and JSON summary
6. **Implement**: Engineering team implements from PRD

### File Organization
- `bpel/*.bpel` - Source BPEL processes (read-only)
- `wsdl/*.wsdl` - WSDL definitions (reference)
- `prds/*.md` - Generated PRDs (implementation source)
- `summaries/*.json` - Machine-readable summaries
- `gaps/*.md` - Documented questions and assumptions

## Configuration

```yaml
agent_type: bpel_transformation
input_format: bpel_xml
output_formats:
  - markdown_prd
  - json_summary
target_stacks:
  - python_temporal
  - nodejs_camunda
  - go_cadence
preserve_semantics: strict
handle_ambiguity: explicit_gaps
include_pseudocode: true
include_test_plan: true
verbosity: comprehensive
```

## License

This project is designed for enterprise BPEL transformation and modernization initiatives.

## Contributing

This agent is configured via the instructions in `.github/agents/bpel-prd-agent.md`. To modify the agent's behavior, update the agent instructions file.
