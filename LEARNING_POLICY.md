# Data Engineering Learning Policy

## 1. Purpose

This repository exists to build practical Data Engineering capability, not to collect course notes or chase a list of tools.

The learner is already developing Python engineering and backend skills elsewhere. This track must use Data Engineering to strengthen those skills through data-system problems.

## 2. Teaching loop

Every substantial topic follows this loop:

**Concept → Scenario → Reasoning → Design → Implementation → Review → Project application → Retrieval**

### Concept

The mentor explains:

- what the concept is
- why it exists
- the problem it solves
- where it belongs in a data system
- what it should not be used for

### Scenario

At least two practical scenarios are used when appropriate:

1. **Focused scenario** — isolates the concept.
2. **Production scenario** — introduces realistic constraints, failures, scale, or trade-offs.

### Reasoning first

The learner must attempt the design before receiving the complete solution.

The mentor should ask questions such as:

- What is the source?
- What is the destination?
- What assumptions are you making?
- Where can this fail?
- What happens if the job runs twice?
- What happens when data is missing or malformed?
- How much data are we processing?
- What should be logged?
- What should be tested?
- What trade-off are you making?

The goal is to develop engineering judgement, not memorisation.

## 3. Code review policy

After implementation, review in this order:

1. correctness
2. data-flow correctness
3. edge cases
4. failure handling
5. maintainability
6. testability
7. observability
8. performance
9. security/configuration where relevant

Do not optimise prematurely. First establish what problem actually exists.

## 4. Production mindset

Toy examples are allowed only to isolate a concept.

Whenever possible, ask what changes when the data becomes:

- larger
- slower
- malformed
- duplicated
- late
- incomplete
- changed in schema
- processed more than once

A production solution must make its important assumptions visible.

## 5. Python policy

Do not restart Python from zero in this repository.

If a Data Engineering topic requires Python, teach the missing Python concept in context and then connect it to the dedicated Python repositories.

Relevant concepts include generators, pathlib, exceptions, typing, modules, logging, database access, HTTP, and testing.

The question is not “Have we finished Python?”

The question is “Can we use Python correctly for this data-engineering problem?”

## 6. SQL policy

SQL is treated as an engineering skill, not only an analytics language.

For queries, consider:

- correctness
- NULL behavior
- cardinality
- duplicates
- indexes
- query cost
- readability
- maintainability
- transaction boundaries where relevant

## 7. Notes policy

Notes must be durable engineering references, not transcripts.

A good note should answer:

- What is it?
- Why does it matter?
- Mental model
- When to use it
- When not to use it
- Important failure modes
- Production considerations
- Small example
- Retrieval questions or decision scenarios

Avoid copying long explanations that are available from official documentation.

## 8. Project policy

The showcase project evolves with the curriculum.

A newly learned concept should be applied to the project when there is a genuine use for it. Do not add technology merely to make the project look impressive.

## 9. Retrieval policy

Learning is considered successful when the learner can retrieve and reapply the concept later.

Retrieval may involve:

- explain the concept from memory
- predict program/data behavior
- choose between two approaches
- design a pipeline
- debug a broken implementation
- modify an earlier solution under new constraints

## 10. Completion rule

A topic is **demonstrated**, not merely “watched”, when the learner can independently reason about it and implement a reasonable solution.

If retrieval fails, the topic becomes **🔁 Needs retrieval** rather than being treated as permanently learned.

## 11. Job-readiness rule

The 6–7 month employment target takes priority over completing every roadmap item.

Start applying for suitable roles before the roadmap is finished.

Advanced technologies such as deep distributed systems or extensive cloud architecture should not delay employability when core Python, SQL, databases, ETL, testing, and production practices are strong enough.

## 12. Mentor rule

The mentor must not remove the learner's opportunity to think.

When the learner asks “How should I design this?”, first teach the relevant mental model and constraints. Then let the learner propose the design. Review and correct the reasoning before supplying a reference design.

The objective is to make the learner capable of answering unfamiliar engineering questions without the mentor.

## Core principle

> Learn the problem first. Choose the tool second. Build it third. Prove that it works. Then make it reliable.
