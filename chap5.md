---
layout: intro
transition: slide-left
---

<div style="background: linear-gradient(135deg, #e0eafc 0%, #cfdef3 100%); padding: 2rem; border-radius: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.07);">

# Chapter 5: Propositional Logic

</div>

---
transition: slide-left
---

## Introduction

Propositional logic is fundamental for artificial intelligence knowledge representation, providing a precise way to encode and reason about facts. Unlike natural language, formal sentences in propositional logic support provable inference. 

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

**💡 Example:**

"If it thunders, there is lightning. There is no lightning today. Therefore, there is no thunder today." 

Logic encodes this so a computer can infer the conclusion:
- Let $T$ = "It thunders", $L$ = "There is lightning"
- Knowledge: $T ⇒ L$ and $¬L$
- Conclusion: $¬T$ (by modus tollens)

</div>

---

## Propositional Logic: The Basics

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #2196f3; margin: 1rem 0;">

**📘 Definition: Logical Operators**

Sentences are assertions built from Boolean variables (True/False). The main operators:
- **Negation (¬):** reverses value
- **Conjunction (∧):** only True if both operands are True
- **Disjunction (∨):** True if at least one operand is True
- **Implication (⇒):** "If a, then b." False only if a is True and b is False
- **Equivalence (⇔):** True if both operands match

</div>

---

## Propositional Logic: The Basics

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

**💡 Example:** If $a$ is "raining" and $b$ is "John is at work"
- "Either it is not raining or John is not at work" is written as $¬a ∨ ¬b$
- Given: "It is raining" ($a$ is True)
- Inference: "John is not at work" ($¬b$)

**Solution:** From $¬a ∨ ¬b$ and $a$, we get $¬b$ (by disjunctive syllogism)

</div>

---

## Truth Tables

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #2196f3; margin: 1rem 0;">

**📘 Definition: Truth Tables**

Truth tables list all possible values for logical expressions.
For two variables $a$ and $b$:

| a    | b    | a ∧ b | a ∨ b | ¬a |  a ⇒ b |
|------|------|-------|-------|----|--------|
| True | True |  True |  True |False|  True |
| True |False | False |  True |False| False |
|False | True | False |  True |True |  True |
|False |False | False | False |True |  True |

</div>
---

## Truth Tables

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #9c27b0; margin: 1rem 0;">

Truth table for the XOR operator ($a ⊕ b$).

**XOR is True when operands differ (one True, one False)**

| a    | b    | a ⊕ b |
|------|------|-------|
| True | True | False |
| True |False | True  |
|False | True | True  |
|False |False | False |

</div>

---

## Laws of Propositional Logic

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #2196f3; margin: 1rem 0;">

**📘 Key Laws:**

- **Idempotence:** $a ∨ a = a$, $a ∧ a = a$
- **Double Negation:** $¬(¬a) = a$
- **Commutativity/Associativity:** Order and grouping don't affect outcome
- **Distributivity:** $a ∧ (b ∨ c) = (a ∧ b) ∨ (a ∧ c)$
- **De Morgan's Laws:** $¬(a ∨ b) = (¬a) ∧ (¬b)$, $¬(a ∧ b) = (¬a) ∨ (¬b)$
- **Implication reduction:** $a ⇒ b = ¬a ∨ b$

</div>

---

## Laws of Propositional Logic

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

**💡 Example:** Show that $¬(a ∨ b)$ is equivalent to $(¬a) ∧ (¬b)$

**Proof:** De Morgan's Law :

 **Both columns match! ✓**

| a | b | a ∨ b | ¬(a ∨ b) | ¬a | ¬b | (¬a) ∧ (¬b) |
|---|---|-------|----------|----|----|-------------|
| T | T |   T   |    F     | F  | F  |      F      |
| T | F |   T   |    F     | F  | T  |      F      |
| F | T |   T   |    F     | T  | F  |      F      |
| F | F |   F   |    T     | T  | T  |      T      |

</div>

---

## Tautologies and Satisfiability

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #2196f3; margin: 1rem 0;">

- **Tautology:** Always True (e.g., $a ∨ ¬a$)
- **Satisfiable:** At least one assignment makes it True (e.g., $a ∧ b$)
- **Unsatisfiable:** No assignment makes it True (e.g., $a ∧ ¬a$)
</div>

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

**💡 Example:** Prove $a ∨ ¬a$ is a tautology

Always True regardless of $a$'s value! ✓

| a    | ¬a   | a ∨ ¬a |
|------|------|--------|
| True | False| True   |
| False| True | True   |

</div>

---

## Tautologies and Satisfiability

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #9c27b0; margin: 1rem 0;">

**✏️ Exercise:** Is $a ∧ b$ satisfiable?

**Solution:** Yes! When $a = True$ and $b = True$, the expression is True. Therefore, it's satisfiable (at least one assignment makes it True).

</div>

## Clauses and Canonical Forms

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #2196f3; margin: 1rem 0;">

- **Clause:** Disjunction of literals (e.g., $a ∨ ¬b ∨ c$)
- **Conjunctive Normal Form (CNF):** Conjunction of clauses: $(a ∨ b) ∧ (c ∨ ¬d)$
- **Disjunctive Normal Form (DNF):** Disjunction of conjunctions: $(a ∧ b) ∨ (¬c ∧ d)$

</div>

---

## Clauses and Canonical Forms

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

**💡 Example:** Convert $¬(a ∨ b)$ to CNF

**Solution:** 
- Apply De Morgan's Law: $¬(a ∨ b)$ → $(¬a) ∧ (¬b)$
- This is already in CNF! (conjunction of literals)

</div>

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #9c27b0; margin: 1rem 0;">

**✏️ Exercise:** Express $(a ∨ b) ∧ (¬c ∨ d)$ in CNF and DNF

**Solution:**
- **CNF:** $(a ∨ b) ∧ (¬c ∨ d)$ - Already in CNF! ✓
- **DNF:** Using distributivity: $(a ∧ ¬c) ∨ (a ∧ d) ∨ (b ∧ ¬c) ∨ (b ∧ d)$

</div>

---

## Knowledge Bases & Expert Systems

Propositional logic is the basis for knowledge-based expert systems that encode domain expertise as logical rules.  **💡 Example: Medical Diagnosis System** 
<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">
Patient John's symptoms:

- $c$: coughing, $t$: fever, $f$: infection, $p$: colored phlegm, $b$: bacterial infection, $a$: administer antibiotic  
**Knowledge Base:**
- $c ∧ t ⇒ f$ : (cough + fever → infection)
- $p ∧ f ⇒ b$ : (colored phlegm + infection → bacterial)
- $b ⇒ a$ : (bacterial infection → antibiotic)

**Solution:** If John has $c = True$, $t = True$, $p = True$:
1. From $c ∧ t ⇒ f$: Infer $f = True$
2. From $p ∧ f ⇒ b$: Infer $b = True$
3. From $b ⇒ a$: Infer $a = True$ (Recommend antibiotic!)
</div>

---

## Equivalence of Expressions

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

**💡 Example:** Show $(a ∨ c) ∧ (a ∨ d) ∧ (b ∨ c) ∧ (b ∨ d)$ ≡ $(a ∧ b) ∨ (c ∧ d)$

- Start: $(a ∨ c) ∧ (a ∨ d) ∧ (b ∨ c) ∧ (b ∨ d)$
- Group: $[(a ∨ c) ∧ (a ∨ d)] ∧ [(b ∨ c) ∧ (b ∨ d)]$
- Distributive: $[a ∨ (c ∧ d)] ∧ [b ∨ (c ∧ d)]$
- Distributive again: $(a ∧ b) ∨ (c ∧ d)$ ✓
</div>

**✏️ Exercise:** Prove $a ⇒ b$ and $¬b ⇒ ¬a$ are equivalent (contraposition)
<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #9c27b0; margin: 1rem 0;">

- $a ⇒ b$ ≡ $¬a ∨ b$ (implication reduction)
- $¬b ⇒ ¬a$ ≡ $¬(¬b) ∨ ¬a$ ≡ $b ∨ ¬a$ (implication + double negation)
- $¬a ∨ b$ ≡ $b ∨ ¬a$ (commutativity) ✓
</div>

---

## Automated Theorem Proving Techniques

**📘 Key Inference Rules:**

- **Modus Ponens:** From $a ⇒ b$ and $a$, infer $b$
- **And-Elimination:** From $a ∧ b$, infer both $a$ and $b$
- **Or-Elimination:** From $a ∨ b$ and $¬a$, infer $b$

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

- "If Alice likes daisies, she also likes roses" ($a ⇒ b$)
- "Alice likes daisies" ($a$)  
**Solution By Modus Ponens:**
- From $a ⇒ b$ and $a$, we infer $b$
- Therefore: Alice likes roses! ✓  
**Note:** If we had $¬a$ instead, we couldn't infer anything about $b$ (that would be the fallacy of denying the antecedent)
</div>

---

## Proof by Contradiction & Resolution

- **Proof by Contradiction:** Assume the negation of what you want to prove and show it leads to a contradiction
- **Resolution:** Pair clauses that differ by the negation of a literal, combine to eliminate it, repeat until contradiction or end

💡 Example: Prove $b$ from $a ⇒ b$ and $a$

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

 1. Convert to CNF: $a ⇒ b$ becomes $¬a ∨ b$
2. Knowledge Base: $\{¬a ∨ b, a\}$
3. To prove $b$, assume $¬b$ (proof by contradiction)
4. New KB: $\{¬a ∨ b, a, ¬b\}$
5. Resolution:
   - From $¬a ∨ b$ and $¬b$: get $¬a$
   - From $¬a$ and $a$: get contradiction! ⊥
6. Therefore $b$ must be True! ✓

</div> 


---

## Clauses: Definite and Horn

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #2196f3; margin: 1rem 0;">

**📘 Definitions:**

- **Definite Clause:** Disjunction with exactly one positive literal (e.g., $¬a ∨ ¬b ∨ c$)
- **Horn Clause:** At most one positive literal. Useful for efficient resolution proofs

</div>

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

**💡 Example:** Convert $a ∧ b ⇒ c$ to Horn clause

**Solution:**
- Apply implication reduction: $a ∧ b ⇒ c$ ≡ $¬(a ∧ b) ∨ c$
- Apply De Morgan's: $¬(a ∧ b) ∨ c$ ≡ $(¬a ∨ ¬b) ∨ c$
- Simplify: $¬a ∨ ¬b ∨ c$ (Horn clause with 2 negative, 1 positive literal)

</div>

---

## Forward and Backward Chaining

<div style="background: linear-gradient(135deg, #e3f2fd 0%, #bbdefb 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #2196f3; margin: 1rem 0;">

- **Forward Chaining:** Start with known facts and use rules to infer new facts stepwise (data-driven)
- **Backward Chaining:** Start with goal, work backward to check if it can be proved (goal-driven)

</div>

<div style="background: linear-gradient(135deg, #fff5e6 0%, #ffe6cc 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #ff9800; margin: 1rem 0;">

**💡 Example: Forward Chaining**

**Rules:** $c ∧ t ⇒ f$, $p ∧ f ⇒ b$, $b ⇒ a$

**Facts:** John has $c = True$, $t = True$, $p = True$

**Solution (Forward):**
1. Apply $c ∧ t ⇒ f$: Since $c$ and $t$ are True → infer $f = True$
2. Apply $p ∧ f ⇒ b$: Since $p$ and $f$ are True → infer $b = True$
3. Apply $b ⇒ a$: Since $b$ is True → infer $a = True$ ✓

</div>

---

## Forward and Backward Chaining

<div style="background: linear-gradient(135deg, #e8f5e9 0%, #c8e6c9 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #4caf50; margin: 1rem 0;">

**💡 Example: Backward Chaining**


**Rules:** $c ∧ t ⇒ f$, $p ∧ f ⇒ b$, $b ⇒ a$

**Facts:** John has $c = True$, $t = True$, $p = True$

**Goal:** Prove $a = True$

1. To prove $a$, need $b$ (from $b ⇒ a$)
2. To prove $b$, need $p ∧ f$ (from $p ∧ f ⇒ b$)
3. Check $p = True$ ✓
4. To prove $f$, need $c ∧ t$ (from $c ∧ t ⇒ f$)
5. Check $c = True$ ✓ and $t = True$ ✓
6. Therefore $f$, $b$, and $a$ are all True! ✓

</div>

---

## Comparing Chaining Methods

- **Forward chaining:** May deduce many facts (some irrelevant) - Good for data-rich scenarios
- **Backward chaining:** Only deduces facts relevant to goal - More efficient in sparse KBs

**✏️ Exercise:** Simulate backward chaining

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #9c27b0; margin: 1rem 0;">

**Rules:** $a ∧ c ⇒ q$, $d ⇒ a$, $e ⇒ c$  
**Facts:** $d = True$, $e = True$  
**Goal:** Prove $q$  
1. To prove $q$, need $a ∧ c$ (from $a ∧ c ⇒ q$)
2. To prove $a$, need $d$ (from $d ⇒ a$) → Check: $d = True$ ✓
3. Therefore $a = True$ ✓
4. To prove $c$, need $e$ (from $e ⇒ c$) → Check: $e = True$ ✓
5. Therefore $c = True$ ✓
6. Since both $a$ and $c$ are True → $q = True$ ✓
</div>

---

## Exercises 

<div style="background: linear-gradient(135deg, #f3e5f5 0%, #e1bee7 100%); padding: 1.5rem; border-radius: 8px; border-left: 4px solid #9c27b0; margin: 1rem 0;">

**✏️ Exercise 1:** Show that $a ⇒ b$ and $¬b ⇒ ¬a$ are equivalent using truth tables

<!-- **Solution:**

| a | b | a ⇒ b | ¬b | ¬a | ¬b ⇒ ¬a |
|---|---|-------|----|----|---------|
| T | T |   T   | F  | F  |    T    |
| T | F |   F   | T  | F  |    F    |
| F | T |   T   | F  | T  |    T    |
| F | F |   T   | T  | T  |    T    |

Columns match! They're equivalent (contraposition) ✓ -->

**✏️ Exercise 2:** Construct truth tables for XOR, NAND, NOR

<!-- **Solution:**

| a | b | XOR (a ⊕ b) | NAND (¬(a ∧ b)) | NOR (¬(a ∨ b)) |
|---|---|-------------|-----------------|----------------|
| T | T |      F      |        F        |       F        |
| T | F |      T      |        T        |       F        |
| F | T |      T      |        T        |       F        |
| F | F |      F      |        T        |       T        | -->

**✏️ Exercise 3:** Forward chaining on medical KB

**KB:** $c ∧ t ⇒ f$, $p ∧ f ⇒ b$, $b ⇒ a$  
**Facts:** $c = True$, $t = True$, $p = True$

<!-- **Solution (Forward):**
1. Apply $c ∧ t ⇒ f$: Since $c$ and $t$ are True → infer $f = True$
2. Apply $p ∧ f ⇒ b$: Since $p$ and $f$ are True → infer $b = True$
3. Apply $b ⇒ a$: Since $b$ is True → infer $a = True$ ✓ -->

**✏️ Exercise 4:** Convert $¬(a ∨ b ∨ c)$ into CNF

<!-- **Solution:**
- Apply De Morgan's: $¬(a ∨ b ∨ c)$ → $¬a ∧ ¬b ∧ ¬c$
- This is already in CNF! (conjunction of literals) -->


**✏️ Exercise 5:** Proof by contradiction: Given $a ⇒ b$ and $a$, prove $b$

<!-- 1. Assume $¬b$ (for contradiction).
2. From $a ⇒ b$, if $a$ is True then $b$ must be True.
3. But we assumed $¬b$ is True → Contradiction!
4. Therefore, $b$ must be True. -->

</div>

