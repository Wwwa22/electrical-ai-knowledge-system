# Architecture and engineering decisions

This page describes the private application's design at a high level. It contains no operational data or source code.

## Workflow

| Stage | Responsibility | Engineering reason |
| --- | --- | --- |
| Intake | Accept authorized documents through attachment ingestion or manual upload | Bring scattered references into a consistent workflow |
| Content identity | Compute a SHA-256 hash and check for duplicates | Avoid repeated analysis of identical bytes |
| Evidence extraction | Produce structured knowledge with facts, inferences, unknowns, and source references | Preserve the distinction between an observation and an explanation |
| Organization | Navigate knowledge by equipment and cases | Keep technical context attached to the lesson |
| Retrieval and practice | Retrieve relevant knowledge for Q&A, interviews, and learning | Make stored material usable without losing its evidence trail |

## Retrieval

The implementation combines semantic matches with lexical ranking and has a lexical fallback. Answers return source references and are instructed to stay within the supplied material.

This is a design for grounded responses, not a guarantee of factual accuracy. Extraction errors can propagate into retrieval, a relevant document can be missed, and a model can still overstate an inference.

## Access boundaries

The private application uses authentication, owner checks, private storage, and restricted server operations. Public portfolio documentation is kept separate from both the source repository and the evidence corpus.

Source-level controls must also be verified in the deployed environment. No security certification or full production audit is claimed.

## Workload controls

Duplicate detection, bounded ingestion, scheduled processing limits, and cooldown behavior reduce unnecessary repeated processing. They do not establish a measured total-cost guarantee.

## Validation still needed

- A synthetic evaluation set with answerable and unanswerable questions.
- Citation-support checks and retrieval coverage measurements.
- Negative authorization tests against an isolated deployment.
- Recovery tests for provider failures, duplicate files, and partial processing.
- A public demonstration using newly written synthetic material only.

These are evaluation priorities, not claimed completed results.

[Back to the showcase](../README.md)
