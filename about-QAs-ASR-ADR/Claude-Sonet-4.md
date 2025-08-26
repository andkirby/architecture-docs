Quality Attributes, Architecture Decision Records (ADR), and Architecturally Significant Requirements (ASR) are fundamental concepts in software architecture that work together to guide architectural decision-making.

## Quality Attributes

Quality Attributes (also called Non-Functional Requirements) define **how** a system should behave rather than **what** it should do. They're critical for architectural design decisions.

### Common Quality Attributes:

**Performance**
- Response time, throughput, resource utilization
- Example: "System must respond to user requests within 200ms"

**Scalability**
- Ability to handle increased load
- Horizontal vs. vertical scaling capabilities

**Reliability/Availability**
- System uptime, fault tolerance, disaster recovery
- Example: "99.9% uptime requirement"

**Security**
- Authentication, authorization, data protection, compliance
- Example: "Must comply with GDPR and encrypt data at rest"

**Maintainability**
- Code readability, modularity, testability
- Ease of adding new features or fixing bugs

**Usability**
- User experience, accessibility, learnability

**Interoperability**
- Integration capabilities with other systems
- API compatibility, data exchange formats

## Architecturally Significant Requirements (ASR)

ASRs are requirements that have a **major impact** on the system's architecture. They typically include:

- Quality attribute requirements with specific measurable criteria
- Functional requirements that significantly influence architectural decisions
- Business constraints (budget, timeline, compliance)
- Technical constraints (existing systems, technology choices)

### ASR Characteristics:
- **Measurable**: Specific metrics and acceptance criteria
- **Testable**: Can be verified through testing or analysis
- **High Impact**: Significantly influence architectural decisions
- **Prioritized**: Ranked by business importance

## Architecture Decision Records (ADR)

ADRs document important architectural decisions, providing context for future team members and maintaining institutional knowledge.

### ADR Structure:
```markdown
# ADR-001: Database Technology Selection

## Status
Accepted

## Context
We need to choose a database technology for our e-commerce platform
that supports high transaction volumes and complex queries.

## Decision
Use PostgreSQL as our primary database.

## Consequences
**Positive:**
- ACID compliance ensures data consistency
- Strong SQL support for complex queries
- Good performance for read-heavy workloads

**Negative:**
- Higher operational complexity than NoSQL alternatives
- Vertical scaling limitations for extreme loads
```

## How They Work Together

```mermaid
graph LR
    A[Business Requirements] --> B[Identify ASRs]
    B --> C[Define Quality Attributes]
    C --> D[Architectural Design]
    D --> E[Document ADRs]
    E --> F[Validate Against ASRs]
```

### Example Workflow:

1. **Identify ASRs**: "System must handle 10,000 concurrent users with sub-second response times"

2. **Extract Quality Attributes**: 
   - Performance: < 1 second response time
   - Scalability: 10,000 concurrent users

3. **Make Architectural Decisions**: Choose microservices architecture with load balancing

4. **Document ADR**: Record the decision, rationale, and trade-offs

5. **Validate**: Ensure the architecture meets the original ASRs

## Best Practices

### For Quality Attributes:
- Make them **specific and measurable**
- Use quality attribute scenarios (stimulus-response pairs)
- Prioritize based on business value
- Consider trade-offs between conflicting attributes

### For ASRs:
- Involve stakeholders in identification
- Update as requirements evolve
- Link to business objectives
- Maintain traceability to architectural decisions

### For ADRs:
- Keep them concise but complete
- Include context and alternatives considered
- Update status as needed (Proposed → Accepted → Superseded)
- Make them easily discoverable and searchable

## Quality Attribute Scenarios Template
```markdown
**Source**: Who/what generates the stimulus
**Stimulus**: The condition that affects the system
**Environment**: System state when stimulus occurs
**Artifact**: Part of system affected
**Response**: Activity after stimulus arrival
**Response Measure**: Measurable criteria for response
```

**Example**:
- **Source**: User
- **Stimulus**: Requests product search
- **Environment**: Normal operation, peak load
- **Artifact**: Search service
- **Response**: Results returned to user
- **Response Measure**: 95% of searches complete within 500ms

This systematic approach ensures that architectural decisions are well-informed, documented, and aligned with business objectives while maintaining system quality.
