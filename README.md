# data-engineering-lab

Yes. And I think we should make this a **system**, not a one-off exercise.

The loop will be:

> **Choose → Hypothesize → Build → Test → Observe → Analyze → Decide → Document → Publish → Reuse**

We'll do it together, step by step.

## 1. First, create your "Engineering Evidence" system

Since you already have an `.ai` engineering framework, I would keep this separate from your work-project artifacts and make a small public-learning repository.

Something like:

```text
data-engineering-lab/
│
├── README.md
│
├── experiments/
│   ├── airflow/
│   ├── snowflake/
│   ├── dbt/
│   ├── python/
│   └── ai/
│
├── decisions/
│
├── failures/
│
├── benchmarks/
│
├── patterns/
│
├── anti-patterns/
│
├── architectures/
│
├── projects/
│
└── docs/
```

The important distinction:

**Your `.ai` framework** = your engineering methodology.

**This lab** = evidence generated from your own experiments.

---

# 2. Pick ONE experiment

Don't start with an enormous project.

I'd actually start with something you already know:

## Experiment #1 — Snowflake query optimization

Why?

Because you already rated Snowflake performance **A**, so we're not learning Snowflake from scratch.

We're testing whether we can turn your existing knowledge into **evidence-based knowledge**.

The question could be:

> **How much can Snowflake query performance improve through better filtering, clustering, and query design?**

---

# 3. Write the hypothesis BEFORE testing

Create:

```text
experiments/snowflake/001-query-optimization.md
```

Start with:

```markdown
# Experiment 001 — Snowflake Query Optimization

## Question

How much can query performance be improved through query
optimization and physical design?

## Hypothesis

I expect that reducing unnecessary data scanned and improving
pruning will have a measurable impact on query execution time.

## What I want to learn

- How query design affects execution
- How much data is scanned
- How clustering affects pruning
- How warehouse size affects runtime
- Whether lower runtime always means lower cost

## Status

Planned
```

Notice that we're **not writing the answer yet**.

---

# 4. Design the experiment

We need controlled variables.

For example:

### Dataset

Use a sufficiently large dataset.

Potentially:

```text
10M+ rows
```

### Test A — Baseline

Poor/simple query.

Record:

```text
Execution time
Bytes scanned
Rows scanned
Warehouse
Credits
```

### Test B — Query optimization

Change only the query.

Measure again.

### Test C — Physical optimization

Introduce clustering/appropriate physical design.

Measure again.

### Test D — Warehouse size

Test different warehouse sizes.

Measure again.

Now we have actual evidence.

---

# 5. Record results immediately

Don't rely on memory.

Create:

```text
experiments/snowflake/001-results.csv
```

Something like:

| Test | Query         | Warehouse | Runtime | Data scanned | Credits |
| ---- | ------------- | --------- | ------: | -----------: | ------: |
| A    | Baseline      | Small     |     ... |          ... |     ... |
| B    | Optimized SQL | Small     |     ... |          ... |     ... |
| C    | Clustered     | Small     |     ... |          ... |     ... |
| D    | Clustered     | Medium    |     ... |          ... |     ... |

Now your conclusion is based on **your measurements**, not ChatGPT's explanation.

---

# 6. Investigate unexpected results

This is where the real knowledge starts.

Suppose:

```text
Baseline       8 sec
Optimization   7 sec
Clustering     6.5 sec
```

You might conclude:

> "Clustering dramatically improves performance."

But that's probably an overstatement.

Instead ask:

> Why was the improvement small?

Maybe:

* dataset too small
* cache affected results
* query already had good pruning
* clustering wasn't selective
* warehouse was the bottleneck

This investigation is more valuable than the original test.

---

# 7. Record the decision

After the experiment:

```text
decisions/snowflake/query-optimization.md
```

Example:

```markdown
# Decision — Query Optimization

## Context

...

## Options evaluated

1. Query rewrite
2. Clustering
3. Warehouse scaling

## Evidence

...

## Decision

...

## Why

...

## When I would NOT use this

...

## Confidence

Medium
```

Now you've captured **engineering judgment**.

---

# 8. Convert the experiment into a reusable pattern

Suppose you learn:

> "Before increasing warehouse size, investigate query pruning and unnecessary scans."

That becomes:

```text
patterns/snowflake/query-performance-investigation.md
```

Structure:

```markdown
# Snowflake Query Performance Investigation

## When to use

## Symptoms

## Investigation sequence

1. Query Profile
2. Data scanned
3. Pruning
4. Query structure
5. Clustering
6. Warehouse sizing

## Common mistakes

## Decision criteria
```

Now your experiment became a **reusable engineering asset**.

---

# 9. Publish the experiment—not your notes

This is extremely important.

Don't publish:

> "Today I learned Snowflake clustering."

Publish:

> **I tested whether clustering actually improved query performance—and the result wasn't what I expected.**

Then:

```text
Problem
 ↓
Hypothesis
 ↓
Experiment
 ↓
Results
 ↓
Unexpected observation
 ↓
Investigation
 ↓
Conclusion
```

That makes much better LinkedIn/YouTube content.

---

# 10. GitHub becomes the evidence

Your repository contains:

```text
experiment
results
SQL
charts
analysis
decision
pattern
```

Someone can inspect your work.

That is much stronger than:

> "I have 5 years of Snowflake experience."

---

# 11. Then publish a short version

For LinkedIn, something like:

> **I wanted to test something I thought I already understood: Snowflake query optimization.**
>
> I created a controlled workload and compared:
>
> * baseline query
> * optimized query
> * clustering
> * warehouse scaling
>
> The interesting part wasn't the performance improvement itself. It was discovering where the improvement **didn't** happen.
>
> I documented the experiment, measurements and conclusions here: [GitHub]

That's authentic technical content.

---

# 12. YouTube can use the same experiment

You don't need a separate project.

Video:

> **"I tested Snowflake query optimization instead of just reading about it."**

Structure:

```text
0:00 Problem
0:30 Hypothesis
1:00 Dataset
2:00 Baseline
4:00 Optimization
6:00 Clustering
8:00 Results
10:00 What surprised me
12:00 Conclusion
```

One experiment → **GitHub + LinkedIn + YouTube**.

---

# 13. And then we repeat

Once experiment #1 is finished:

### Experiment #2

**dbt incremental vs full refresh**

Then:

### Experiment #3

**Airflow retry strategies**

Then:

### Experiment #4

**Python synchronous vs concurrent API ingestion**

Then:

### Experiment #5

**RAG chunking strategies**

Then:

### Experiment #6

**Vector search in Milvus**

Then:

### Experiment #7

**LLM structured output reliability**

Then:

### Experiment #8

**RAG evaluation**

Notice what's happening.

We're simultaneously:

**learning → experimenting → building → measuring → documenting → publishing**

And your AI learning naturally gets incorporated.

---

# One important rule

**We should never fabricate results.**

If you haven't run the experiment, we don't write:

> "Clustering reduced runtime by 40%."

We run it first.

If the result is boring:

> "There was almost no improvement."

**That's still valuable.**

In fact, unexpected/negative results can make better engineering content because you can explain *why* your original assumption was wrong.

---

# How I can help you through the process

You don't have to figure out each experiment yourself.

We can work like this:

### You say:

> "Let's do experiment #1."

### I'll help you:

**Step 1:** formulate the question
**Step 2:** formulate hypothesis
**Step 3:** design controlled test
**Step 4:** create repo structure
**Step 5:** write SQL/code
**Step 6:** execute it
**Step 7:** collect measurements
**Step 8:** analyze results
**Step 9:** identify lessons
**Step 10:** create decision record
**Step 11:** create reusable pattern
**Step 12:** write GitHub documentation
**Step 13:** turn it into LinkedIn content
**Step 14:** optionally turn it into a YouTube script

And importantly, **AI helps you throughout the process, but the evidence comes from you actually doing the experiment.**

---

## So let's actually begin

I suggest **Experiment #1 = Snowflake Query Optimization**, because you already have a Snowflake environment and production experience.

We won't jump into coding yet.

**First we'll design the experiment properly**, including the dataset, queries, variables, measurements, and success criteria. Then you'll run it and bring the results back, and we'll proceed to documentation and publication.



STEP 1  → Choose what to investigate
STEP 2  → Define the question
STEP 3  → Write hypothesis
STEP 4  → Design the experiment
STEP 5  → Prepare environment
STEP 6  → Build baseline
STEP 7  → Measure baseline
STEP 8  → Change ONE thing
STEP 9  → Measure again
STEP 10 → Repeat experiments
STEP 11 → Analyze results
STEP 12 → Identify what you learned
STEP 13 → Make engineering decision
STEP 14 → Document experiment
STEP 15 → Create reusable pattern
STEP 16 → Put everything in GitHub
STEP 17 → Publish publicly
STEP 18 → Convert into future knowledge