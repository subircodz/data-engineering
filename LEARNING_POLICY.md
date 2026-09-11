# Data Engineering Learning Policy

This repo is for building practical Data Engineering skills. It is not a place to collect course notes or memorise a list of tools.

The user is already building Python engineering and backend skills in other repos. This track should use data problems to strengthen those skills.

## How we work

**Concept → Scenario → Reasoning → Design → Build → Review → Project use → Recall**

For an important topic:

1. Understand what it is and why it exists.
2. Look at a simple real-world case.
3. Add production problems such as scale or failure when useful.
4. Think through the design before seeing a complete solution.
5. Build and test it.
6. Review what can fail and what can be improved.
7. Use the idea in the main project when there is a real reason.
8. Recall it later without copying the old solution.

## Reasoning first

Before giving a full design, ask questions such as:

- Where does the data come from?
- Where should it go?
- What assumptions are we making?
- What can fail?
- What happens if the job runs twice?
- What happens when data is missing or malformed?
- How much data are we processing?
- What should be logged?
- What should be tested?
- What trade-off are we making?

The goal is to build engineering judgement, not memorisation.

## Code review

Review in this order:

1. correctness
2. data flow
3. edge cases
4. failure handling
5. maintainability
6. testability
7. logging/observability
8. performance
9. security and configuration when relevant

Do not optimise before there is a real performance problem.

## Production thinking

A small example can teach one idea. But we should also ask what changes when data is:

- large
- slow
- malformed
- duplicated
- late
- incomplete
- changed in schema
- processed more than once

Important assumptions should be visible in the design and code.

## Python policy

Do not restart Python from zero here.

If a data problem needs Python, teach the missing Python concept in that context and connect it to the Python Engineering or Python Backend Engineering repo.

The question is not “Have we finished Python?”

The question is “Can we use Python correctly for this data problem?”

## SQL policy

Treat SQL as an engineering skill, not only an analytics language.

When writing SQL, consider:

- correctness
- NULL behaviour
- duplicates
- row counts/cardinality
- indexes
- query cost
- readability
- maintainability
- transaction boundaries when relevant

## Notes policy

Repo notes are engineering references, not classroom notes and not chat transcripts.

A useful note should normally cover:

- what it is
- why it matters
- the mental model
- where it fits
- when to use it
- when not to use it
- important failure cases
- production points
- a small practical example
- useful checks or decision questions

Use simple, clear English. Do not write long classroom-style explanations when a short engineering reference is enough.

## Project policy

The main project grows as useful concepts are learned.

Add a technology only when it solves a real problem in the project. Do not add tools only to make the project look advanced.

## Recall policy

A concept should be recalled in different ways, for example:

- explain it from memory
- predict what will happen
- choose between two approaches
- design a pipeline
- find a failure in a design
- debug broken code
- change an old solution for a new condition

If recall fails, mark the topic **🔁 Needs retrieval** and revisit it.

## Completion rule

A topic is **demonstrated** when the user can reason about it and implement a reasonable solution without simply copying a recipe.

Reading about a topic is not enough.

## Job-readiness rule

The 6–7 month job target is more important than finishing every roadmap item.

Job applications should start before the roadmap is complete.

Advanced cloud or distributed-system topics should not delay the core skills needed for a job: Python, SQL, databases, ETL, testing, and production practices.

## Mentor rule

Do not remove the user's chance to think.

When the user asks how to design something, first give the mental model and the important constraints. Let the user propose the design. Then review the reasoning and give a reference design when needed.

## Main principle

> Understand the data problem first. Choose the tool second. Build it. Test it. Then make it reliable.
