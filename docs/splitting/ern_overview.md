# Entity Resolution with Negative Rules (ER-N)

Traditional Entity Resolution (ER) focuses on finding records that refer to the same entity and merging them ($M$ and $\mu$). However, this process can sometimes create data that violates logical constraints or "inconsistencies".

**ER-N** introduces "Negative Rules" to identify and resolve these inconsistencies, producing a consistent solution.

## Core Concepts
### Example Records

| Index | Name      | SSN         | Gender |
|-------|-----------|-------------|--------|
| r1    | Pat       | 999-04-1234 |        |
| r2    | Patricia  |             | F      |
| r3    | Pat       | 999-04-1234 | M      |


### 1. The Negative Rules
A negative rule is a predicate that determines if a state is invalid.

* **Unary Negative Rules ($N_1$):** Checks a single record for internal inconsistencies.
    * *Example:* A person record containing two different genders (Male AND Female).
    * *Logic:* $N_1(r) =$ `inconsistent`.
* **Binary Negative Rules ($N_2$):** Checks if two *distinct* records cannot coexist in the same solution.
    * *Example:* Two different people records having the same Social Security Number.
    * *Logic:* $N_2(r_2, r_3) =$ `inconsistent`.

### 2. Resolution Strategies
When an inconsistency is flagged by a negative rule, a "Solver" (human expert or heuristic algorithm) must intervene using one of three strategies:

1.  **Discard:** Drop one of the problematic records from the final answer.
2.  **Forced Merge:** Decide the records actually *are* the same entity and merge them (fixing the binary inconsistency).
3.  **Override:** Decide the rule is a false positive and allow the inconsistency.

## Conceptual Flow

The following diagram illustrates how Negative Rules act as a filter after the standard Match/Merge process.

```d2 layout="elk"
direction: right

Raw_Data: {
  shape: cylinder
  label: Raw Records (I)
}

Merge_Closure: {
  shape: package
  label: Merge Closure (Î)
  tooltip: All possible merged records
}

Consistency_Check: {
  shape: diamond
  label: Negative Rules Check
}

Valid_Solution: {
  shape: document
  label: Valid Solution (J)
  style: {
    fill: "#d1fae5"
    stroke: "#047857"
  }
}

Solver: {
  shape: person
  label: Solver / Expert
}

Raw_Data -> Merge_Closure: Match & Merge
Merge_Closure -> Consistency_Check
Consistency_Check -> Valid_Solution: Consistent
Consistency_Check -> Solver: Inconsistent
Solver -> Valid_Solution: Fix (Discard/Merge)
```