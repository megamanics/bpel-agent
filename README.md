# BPEL Transformation Agents

A suite of specialized agents for transforming Oracle BPEL (Business Process Execution Language) processes into modern implementations. This repository provides two complementary agents that work together to enable complete BPEL modernization:

1. **BPEL PRD Agent** - Analyzes BPEL processes and generates comprehensive Product Requirements Documents
2. **BPEL to Spring Boot Agent** - Implements PRD specifications in Java Spring Boot with full test coverage

Together, these agents enable engineers to re-implement BPEL processes in modern technology stacks with 100% feature parity.

---

## Table of Contents

- [Overview](#overview)
- [Common Capabilities](#common-capabilities)
- [BPEL PRD Agent](#bpel-prd-agent)
- [BPEL to Spring Boot Agent](#bpel-to-spring-boot-agent)
- [Workflow Integration](#workflow-integration)
- [Project Structure](#project-structure)
- [Core Principles](#core-principles)
- [Quality Standards](#quality-standards)
- [License](#license)
- [Contributing](#contributing)

---

## Overview

### Transformation Pipeline

```
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│   Oracle BPEL   │────▶│  BPEL PRD Agent │────▶│   PRD Document  │
│   XML Process   │     │   (Analysis)    │     │   (Markdown)    │
└─────────────────┘     └─────────────────┘     └────────┬────────┘
                                                         │
                                                         ▼
┌─────────────────┐     ┌─────────────────┐     ┌─────────────────┐
│  Spring Boot    │◀────│  BPEL to Spring │◀────│   PRD Document  │
│  Application    │     │   Boot Agent    │     │   (Markdown)    │
└─────────────────┘     └─────────────────┘     └─────────────────┘
```

---

## Common Capabilities

Both agents share foundational capabilities for BPEL transformation:

### Shared Expertise
- **Oracle BPEL 2.0 Understanding**: Deep knowledge of OASIS WS-BPEL XML structures
- **SOA Architecture Patterns**: Understanding of service-oriented integration patterns
- **Business Process Semantics**: Preservation of exact business logic during transformation
- **Data Contract Handling**: Complete variable schemas, message types, and validations

### Shared Principles
- **Exhaustive Processing**: Capture every detail—nothing left to interpretation
- **Zero Ambiguity**: Explicit documentation of all gaps and assumptions
- **Feature Parity Focus**: Enable identical behavior in target implementation
- **Semantic Preservation**: Maintain exact business logic, conditions, and expressions

---

## BPEL PRD Agent

A specialized agent for analyzing Oracle BPEL processes and producing comprehensive, implementable Product Requirements Documents (PRDs).

### Purpose

This agent serves as a senior systems analyst and product architect with deep expertise in:
- Oracle BPEL 2.0 (OASIS WS-BPEL) XML processes
- SOA architectures and integration patterns
- Modern workflow orchestration systems (Python/Temporal, Node.js/Camunda, Java Spring Boot)
- Business process modeling and transformation

### Key Capabilities

#### Comprehensive BPEL Analysis
- **Process Parsing**: Deep understanding of Oracle BPEL 2.0 (OASIS WS-BPEL) XML structures
- **Integration Extraction**: Complete mapping of partner links, WSDL bindings, and service operations
- **Data Flow Documentation**: Full data contracts with variable schemas, message types, and transformations
- **Control Flow Analysis**: Sequences, parallel flows, loops, decisions, and conditional branching
- **Fault Handling**: Comprehensive documentation of error handling, compensation, and recovery logic
- **Correlation Sets**: Extraction of message routing and process instance correlation patterns
- **Human Tasks**: Documentation of Oracle BPM human task extensions and approval workflows

#### Output Generation
- **Markdown PRDs**: Exhaustive, implementation-ready documentation with zero ambiguity (default output)
- **JSON Summaries**: Machine-readable structured data for automation and tooling (use `format=json` parameter)
- **Pseudocode**: Implementation-ready code examples for target platforms
- **Test Plans**: Unit tests, integration tests, and edge case scenarios
- **Gap Analysis**: Explicit documentation of unknowns, assumptions, and clarification needs

#### Technical Extraction
- **XPath Preservation**: Exact extraction of XPath/XQuery expressions with namespace context
- **WSDL Mapping**: Complete service contract documentation from WSDL definitions
- **XSD Schema Resolution**: Full data structure documentation from XML schemas
- **Transaction Boundaries**: Identification of scopes, isolation levels, and transaction contexts
- **Compensation Logic**: Saga pattern documentation with reverse operations

### Usage

#### Basic Transformation
The agent analyzes BPEL process files and generates comprehensive PRDs. Simply provide:
- **Primary Input**: One or more Oracle BPEL XML process files (OASIS WS-BPEL 2.0)
- **Optional Context**: Referenced WSDLs and XSDs for complete type resolution
- **Format**: BPEL XML pasted or referenced in the input

#### Batch Processing
The agent can process multiple BPEL files in sequence to generate:
- Individual PRD documents for each process
- Machine-readable JSON summaries
- Cross-process integration documentation

#### Validation
After generating PRDs, validate completeness by:
```bash
# Check for gaps in generated PRDs
grep -i "gap\|assumption\|unclear" prds/*.md

# Review JSON summaries for completeness
cat summaries/*.json | jq '.gaps[], .assumptions[]'
```

### Input Expectations

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

### Output Format

#### Comprehensive PRD Sections
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

#### Machine-Readable JSON
Structured output includes:
- Process metadata and namespaces
- Partner definitions and operations
- Variable schemas with field types
- Entry points and invocations
- Decisions, loops, and timers
- Fault and compensation handlers
- Correlation sets and human tasks
- Documented assumptions and gaps

### Target Stack Mapping

The agent provides guidance for implementing BPEL processes in modern platforms:

| BPEL Construct | Python/Temporal | Node.js/Camunda | Java Spring Boot |
|----------------|-----------------|-----------------|------------------|
| receive (createInstance) | Workflow start signal | Start event | @RestController endpoint |
| invoke (sync) | Activity function | Service task | RestTemplate/WebClient call |
| invoke (async) | Child workflow | Call activity | @Async method / CompletableFuture |
| assign | Local variables | Variables | Local variables / DTOs |
| flow (parallel) | Parallel activities | Parallel gateway | CompletableFuture.allOf() |
| while/repeatUntil | While loop | Loop task | While/do-while loop |
| pick/onAlarm | Timer + signal | Event-based gateway | @Scheduled / Timer task |
| compensation | Saga pattern | Compensation event | @Transactional with rollback |
| correlation | Workflow ID + search attributes | Business key | Correlation ID header |

### Boundaries and Limitations

#### ✅ Always Does
- Parse BPEL exhaustively—capture every element
- Preserve XPath/XQuery expressions exactly
- Document all partnerLinks, variables, activities
- Mark gaps and assumptions explicitly with questions
- Generate machine-readable JSON summary
- Maintain zero ambiguity in PRD
- Include implementation pseudocode
- Trace complete data flows
- Document fault and compensation handlers

#### ⚠️ Asks First
- Infer business logic not explicit in BPEL
- Suggest refactoring or modernization
- Recommend architectural changes
- Combine multiple processes without explicit mapping
- Make assumptions about external system behavior
- Modify BPEL source files

#### 🚫 Never Does
- Fabricate information not in BPEL
- Omit BPEL elements or activities
- Modify XPath expressions
- Skip fault handlers or edge cases
- Assume behavior without marking as assumption
- Create incomplete data contracts
- Ignore namespace context
- Simplify complex logic without noting

---

## BPEL to Spring Boot Agent

A specialized agent that reads BPEL PRD documentation and implements the functionality using Java Spring Boot with comprehensive test coverage.

### Purpose

This agent serves as a senior Java/Spring Boot engineer that transforms PRD specifications into production-ready implementations:
- Reads and interprets PRD documents generated by the BPEL PRD Agent
- Implements business logic in idiomatic Java Spring Boot
- Creates comprehensive test suites for feature parity validation
- Follows enterprise Java best practices and patterns

### Key Capabilities

#### Spring Boot Implementation
- **Service Layer**: Translates orchestration logic into Spring services
- **REST Controllers**: Exposes endpoints matching PRD-defined entry points
- **Data Models**: Generates POJOs/DTOs from PRD data contracts
- **Integration Clients**: Implements service clients for partner integrations
- **Error Handling**: Maps fault handlers to Spring exception handling patterns

#### Test Coverage
- **Unit Tests**: JUnit tests for individual components
- **Integration Tests**: Spring Boot test slices for service integration
- **Mocking**: Mockito-based mocking for external dependencies
- **Test Data**: Generates test fixtures matching PRD data contracts
- **Coverage**: Targets comprehensive coverage of happy path and edge cases

#### Code Quality
- **Spring Best Practices**: Follows established Spring patterns and conventions
- **Dependency Injection**: Proper use of Spring's IoC container
- **Configuration**: Externalized configuration using Spring properties/YAML
- **Logging**: Structured logging for observability
- **Documentation**: JavaDoc and inline comments for complex logic

### Usage

#### Basic Implementation
The agent reads PRD documents and generates Spring Boot implementations:
- **Primary Input**: PRD markdown document (from BPEL PRD Agent)
- **Output**: Complete Spring Boot application with tests
- **Format**: Standard Maven/Gradle project structure

#### Example Workflow
```bash
# 1. Generate PRD from BPEL (using BPEL PRD Agent)
# Input: bpel/OrderProcess.bpel → Output: prds/OrderProcess.md

# 2. Implement in Spring Boot (using BPEL to Spring Boot Agent)
# Input: prds/OrderProcess.md → Output: Spring Boot project

# 3. Build and test the implementation
cd generated-project
./mvnw clean verify
```

### Output Structure

The agent generates a standard Spring Boot project:

```
generated-project/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/example/
│   │   │       ├── controller/     # REST endpoints
│   │   │       ├── service/        # Business logic
│   │   │       ├── model/          # Data models/DTOs
│   │   │       ├── client/         # Integration clients
│   │   │       ├── exception/      # Custom exceptions
│   │   │       └── config/         # Spring configuration
│   │   └── resources/
│   │       └── application.yml     # Configuration
│   └── test/
│       └── java/
│           └── com/example/
│               ├── controller/     # Controller tests
│               ├── service/        # Service unit tests
│               └── integration/    # Integration tests
├── pom.xml                         # Maven build file
└── README.md                       # Project documentation
```

### Spring Boot Mapping

The agent maps PRD constructs to Spring Boot patterns:

| PRD Construct | Spring Boot Implementation |
|---------------|---------------------------|
| Entry Point | @RestController endpoint |
| Service Invocation | @Service with RestTemplate/WebClient |
| Data Contract | @Entity / DTO class |
| Orchestration | @Service orchestration layer |
| Parallel Flow | CompletableFuture / @Async |
| Decision Logic | Service method conditionals |
| Fault Handler | @ExceptionHandler / @ControllerAdvice |
| Compensation | Saga pattern with transaction management |
| Timeout | @Timeout / Circuit breaker patterns |
| Correlation | Request/correlation ID headers |

### Boundaries and Limitations

#### ✅ Always Does
- Implement all PRD-specified functionality
- Generate comprehensive unit and integration tests
- Follow Spring Boot best practices
- Create proper exception handling
- Include configuration externalization
- Generate build files (Maven/Gradle)
- Document generated code

#### ⚠️ Asks First
- Deviate from PRD specifications
- Add functionality not in PRD
- Use non-standard frameworks or libraries
- Implement complex infrastructure patterns
- Make architectural decisions not in PRD

#### 🚫 Never Does
- Skip PRD requirements
- Generate untested code
- Hard-code configuration values
- Ignore error handling paths
- Create security vulnerabilities
- Produce non-compilable code

---

## Workflow Integration

### Complete Transformation Pipeline

The two agents work together in a seamless pipeline:

```
┌─────────────────────────────────────────────────────────────────────────┐
│                        BPEL Transformation Workflow                     │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  Phase 1: Analysis (BPEL PRD Agent)                                     │
│  ┌──────────────┐    ┌─────────────┐    ┌────────────────┐              │
│  │ BPEL Process │───▶│ PRD Agent   │───▶│ PRD Document   │              │
│  │ (.bpel)      │    │             │    │ (.md + .json)  │              │
│  └──────────────┘    └─────────────┘    └───────┬────────┘              │
│                                                  │                      │
│  Phase 2: Review                                 │                      │
│  ┌──────────────┐                                │                      │
│  │ Architect    │◀───────────────────────────────┤                      │
│  │ Review       │                                │                      │
│  └──────────────┘                                │                      │
│                                                  │                      │
│  Phase 3: Implementation (BPEL to Spring Boot Agent)                    │
│  ┌──────────────┐    ┌─────────────┐    ┌────────────────┐              │
│  │ PRD Document │───▶│ Spring Boot │───▶│ Spring Boot    │              │
│  │ (.md)        │    │ Agent       │    │ Application    │              │
│  └──────────────┘    └─────────────┘    └────────────────┘              │
│                                                                         │
└─────────────────────────────────────────────────────────────────────────┘
```

### Step-by-Step Process

1. **Place**: Add BPEL files to `bpel/` directory
2. **Analyze**: Run BPEL PRD Agent on each process
3. **Review**: Technical architect reviews PRD for completeness
4. **Resolve**: Document and resolve gaps/assumptions
5. **Implement**: Run BPEL to Spring Boot Agent on PRD
6. **Test**: Verify implementation with generated tests
7. **Deploy**: Deploy Spring Boot application

### Success Criteria

A successful transformation enables:
- ✅ Engineers implement WITHOUT referring back to BPEL XML
- ✅ QA validates feature parity using generated tests
- ✅ Product confirms business logic is preserved
- ✅ Operations configures observability from NFRs
- ✅ Automated tools parse JSON for migration pipelines

**Goal**: The generated PRD and Spring Boot implementation make the original BPEL XML obsolete.

---

## Project Structure

```
bpel-agent/
├── bpel/              # Source BPEL process files (input)
├── wsdl/              # WSDL service definitions (reference)
├── xsd/               # XML schema definitions (reference)
├── prds/              # Generated Product Requirements Documents (output)
├── summaries/         # Machine-readable JSON summaries (output)
├── implementations/   # Generated Spring Boot projects (output)
├── gaps/              # Documented questions and assumptions
└── .github/
    └── agents/
        ├── bpel-prd-agent.md           # PRD Agent configuration
        └── bpel2springboot-agent.md    # Spring Boot Agent configuration
```

### File Organization
- `bpel/*.bpel` - Source BPEL processes (read-only)
- `wsdl/*.wsdl` - WSDL definitions (reference)
- `xsd/*.xsd` - XML schema definitions (reference)
- `prds/*.md` - Generated PRDs (implementation source)
- `summaries/*.json` - Machine-readable summaries
- `implementations/` - Generated Spring Boot projects
- `gaps/*.md` - Documented questions and assumptions

---

## Core Principles

Both agents adhere to these core principles:

1. **Exhaustive Processing**: Capture EVERY detail—nothing left to interpretation
2. **Implementation-Ready Output**: Documents and code must be directly usable
3. **Zero Ambiguity**: Explicitly mark gaps and assumptions with specific questions
4. **Preserve Semantics**: Maintain exact business logic and conditions
5. **Feature Parity Focus**: Enable identical behavior in target implementation
6. **Machine-Readable**: Include structured formats for automation
7. **Cross-Process Awareness**: Handle multi-file solutions with dependencies
8. **Comprehensive Testing**: Include test plans and generated tests

---

## Quality Standards

### PRD Completeness (BPEL PRD Agent)
- ✅ Every variable documented with full schema
- ✅ Every XPath expression preserved verbatim
- ✅ Every partner link mapped to operations
- ✅ All fault handlers documented
- ✅ All compensation logic captured
- ✅ All correlation sets explained

### Implementation Completeness (BPEL to Spring Boot Agent)
- ✅ All PRD requirements implemented
- ✅ Comprehensive unit test coverage
- ✅ Integration tests for service interactions
- ✅ Proper exception handling throughout
- ✅ Externalized configuration
- ✅ Build-ready project structure

### Clarity Requirements
- ✅ No ambiguous statements or code
- ✅ Concrete examples provided
- ✅ Technical jargon defined
- ✅ Step-by-step documentation
- ✅ Decision tables for conditionals

### Accuracy Guarantees
- ✅ XPath expressions quoted exactly as in BPEL
- ✅ Namespace prefixes preserved with mappings
- ✅ Activity order matches BPEL sequence
- ✅ No invented details (marked as assumptions if inferred)

---

## Configuration

### BPEL PRD Agent Configuration

```yaml
agent_type: bpel_prd_transformation
input_format: bpel_xml
output_formats:
  - markdown_prd
  - json_summary
target_stacks:
  - python_temporal
  - nodejs_camunda
  - java_springboot
preserve_semantics: strict
handle_ambiguity: explicit_gaps
include_pseudocode: true
include_test_plan: true
verbosity: comprehensive
```

### BPEL to Spring Boot Agent Configuration

```yaml
agent_type: bpel_springboot_implementation
input_format: prd_markdown
output_format: springboot_project
java_version: 17
spring_boot_version: 3.x
build_tool: maven
test_framework: junit5
include_integration_tests: true
code_style: google_java_format
```

---

## License

This project is designed for enterprise BPEL transformation and modernization initiatives.

---

## Contributing

This repository contains two agents configured via instruction files:

- **BPEL PRD Agent**: Configured in `.github/agents/bpel-prd-agent.md`
- **BPEL to Spring Boot Agent**: Configured in `.github/agents/bpel2springboot-agent.md`

To modify agent behavior, update the respective agent instruction files.
