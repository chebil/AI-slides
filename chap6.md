---
layout: intro
transition: slide-left
---

<div style="background: linear-gradient(135deg, #e0eafc 0%, #cfdef3 100%); padding: 2rem; border-radius: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.07);">

# Chapter 6: First-Order Logic

</div>

---
transition: slide-left
---

## Introduction

>- **First-Order Logic (FOL)** expands propositional logic for richer AI reasoning.
>- Addresses statements true for **entire domains** of objects, not just specific cases.
>- **Example**:  
    - **General statement**: “All mammals give birth to live babies.”  
    - **Specific fact**: “A cat is a mammal.”  
    - **Inference using FOL**: “A cat gives birth to live babies.”  

 [Why Propositional Logic is Limited]{style="color:red"}

- **Propositional Logic**: Each statement only applies to specific cases; must list every possibility explicitly.
- **Limitation Example**:
    - "John is coughing" and "John has a temperature" must be repeated for every patient.
- **FOL Solution**: Write rules for all objects, then instantiate for any individual in the domain.

**Example in expert systems**:
> IF coughing AND temperature THEN infection  
> This applies to any patient, not just 'John'.

---

## Predicates Explained 

- **Predicate**: Function returning True/False, describing relationships or properties.
    - **Arity**: Number of arguments
- **Example (Awards)**:
    - F(x, y, z): “x won award z for movie y”
        - F(Steven Spielberg, Saving Private Ryan, Best Director Award) = True
        - F(John Williams, The Terminal, BMI Music Award) = True
- **Example (Medical)**:
    - S(x): “x has a symptom”
    - P(x): “x is a patient”
    - Use same predicate for any patient and any symptom—no need for endless propositional rules.

---

## Advantages of First-Order Logic

- **Generalization**: One rule covers many cases.
- **Domain of discourse**: Set of all considered objects (people, animals, movies, etc.)
- **Efficiency**: Less redundancy.
- **Relation Example**:
    - B(x): “x gives birth to live babies”
        - Use once for all mammals, not for every individual
- **Counting Example**:
    - To find how many movies won an award, add rules for counting in FOL—not practical in propositional logic.

---

## FOL Relationships 

**Expressing relations:**
- $F(x, y, z) → O(x)$
  - "Anyone who wins an award (F) is invited to Oscars (O)"
- Quickly deduce O(Steven Spielberg) if F holds for his case

**Natural language conversion:**
- "If it rains tomorrow, Tommy will eat his carrots."
- $r  ⇒ E(Tommy, Carrots)$

---

## Quantifiers (Universal & Existential) 

- **Universal quantifier (∀)**: “For all x, statement S(x) is true.”
    - $∀x: E(x, Beef) → N(x)$
        - If anyone eats beef, they're non-vegetarian.
- **Existential quantifier (∃)**: "There exists at least one x such that S(x) is true."
    - $∃x: E(x, Beef)$
        - There is at least one person who eats beef.

**Clarification with order:**
- $∀x, ∃y: E(x, y)$
  - Each person eats at least one food (may differ for each)
- $∃y, ∀x: E(x, y)$
  - There is one food everybody eats (much stronger claim)

---

## Quantifier Scope, Order 

- **Parentheses and variable naming clarify scope**
    - $∀x [E(x, Beef) → N(x)]$ — All who eat beef are non-vegetarian. Where $N(x)$ indicates non-vegetarian status of person $x$.
    - Standardize variables for clarity: $∀x, E(x, Beef) → ∃y N(y)$
- **Example (Meat Eater Filtering)**:
    - $∀x, ∃y [E(x, y) ∧ M(y) → N(x)]$. 
        - For each person, if they eat some meat, then they're non-vegetarian
        - Predicate $M(y)$ indicates that the food $y$ is a meat.
---

##  Operator Precedence in FOL

- **Highest**: Quantifiers (∀, ∃)
- **Then**: Negation $(¬)$, And $(∧)$, Or $(∨)$, Implication $(→)$, Equivalence $(↔)$
- **Parentheses**: Always clarify scope if in doubt.

**Precedence Example:**
- $∀x (¬N(x))$
  - Each person is vegetarian.
- $¬∀x N(x)$
  - Not everyone is non-vegetarian (i.e., at least one vegetarian).

---

## Functions in First-Order Logic

- **Function**: Maps object(s) to object(s)
    - $Fav(x)$: favorite food of person x
    - $∀x: Fav(x) = Beef$
- **Example**:
    - If $Fav(John) = Beef$, “John’s favorite food is beef.”
- **Function-based reasoning**:
    - If $M(Fav(x))$ is true (favorite food is meat), infer $N(x)$ (non-vegetarian)

---

## Populating a Knowledge Base

- **Axioms**: Base facts (e.g., parent-child)
    - $P(x, y)$: “x is parent of y”
- **Recursive definition** for ancestor:
    - $∀x, y: P(x, y) → A(x, y)$
    - $∀x, y, z: P(x, z) ∧ A(z, y) → A(x, y)$
    - $∀x: ∃z: P(z, x)$ (everyone has a parent)
- **Example set**:
    - Jim parent of Sue: $P(Jim, Sue)$
    - Sue parent of Ann: $P(Sue, Ann)$
    - Infer Jim ancestor of Ann: via recursive ancestor rules.

---

## Example – Medical Expert System 

- **General rules** (apply to all patients x):
    - $C(x) ∧ T(x) → F(x)$ — Cough and temperature imply infection
    - $P(x) ∧ F(x) → B(x)$ — Phlegm + infection imply bacterial infection
    - $B(x) → A(x)$ — Bacterial infection → Antibiotics needed
- **Facts for John**:
    - $C(John)$ (John coughs)
    - $T(John)$ (John has temperature)
    - $P(John)$ (John has colored phlegm)
- **Inference**:
    - Derive $A(John)$ (John needs antibiotics)

---

## Systematic Inference: Forward & Backward Chaining 

**Forward chaining:** Apply rules to current facts, generate new facts until goal is reached.

**Example:**
- Given: $A(John)$ (absent for exam)
- Rule: $∀x: A(x) → B(x)$ (absent → failing grade)
- $∀x: B(x) → ¬C(x)$ (failing grade → no scholarship)
- Infer: John will not get a scholarship ($¬C(John)$)

**Backward chaining:** Start at goal, look for rules/facts to support it.
- "Did John get a scholarship?" — work backwards via rules above.

---

## Substitution, Unification & Skolemization

- **Substitution**: Replace variables with actual constants for inference.
    - Rule: $∀x: E(x, Beef) → N(x)$
    - Fact: $E(John, Beef)$
    - Substitute: $N(John)$

- **Unification**:
    - Make two formulas look identical for inference.
    - $E(y, Beef)$ and $E(John, Beef)$ unify when $y = John$

- **Skolemization**:
    - Replace existentially quantified variables with Skolem constants or functions.
    - $∃y: E(x, y)$ becomes $E(x, f(x))$, where $f(x)$ is a "Skolem function" of $x$.

---

## Negation & Quantifiers (De Morgan Laws)

- **Negation affects quantifiers**:
    - $∀x: ¬N(x)$: “Nobody is a non-vegetarian.”
    - $¬∀x N(x)$: “Not everyone is non-vegetarian” (at least one is vegetarian).
    - By De Morgan's Laws: Flipping negation moves between $∀$ and $∃$.

- **Example (Domain with a, b, c)**:
    - $∀x N(x) → N(a) ∧ N(b) ∧ N(c)$
    - $¬∀x N(x) → ∃x: ¬N(x)$ (at least one is not non-vegetarian)

---

## Reasoning with Parent/Ancestor Relations

- **Recursive ancestor relationships**:
    - $∀x, y: P(x, y) → A(x, y)$
    - $∀x, y, z: P(x, z) ∧ A(z, y) → A(x, y)$
- **Extended example**:
    - Jim is parent of Sue ($P(Jim, Sue)$)
    - Sue is parent of Ann ($P(Sue, Ann)$)
    - Infer: Jim is ancestor of Ann ($A(Jim, Ann)$) via chaining

- **Avoiding cycles**: $∀x, y: A(x, y) → ¬A(y, x)$

---

## FOL vs Propositional Logic

| Aspect                  | Propositional Logic                  | First-Order Logic                       |
|-------------------------|--------------------------------------|-----------------------------------------|
| Applies to              | Specific statements                  | Objects, variable relations, functions  |
| Compactness             | Redundant for large/similar domains  | Compact rules over domains              |
| Expressiveness          | Only declarative statements          | Relational, compositional, generic      |
| Natural Language Links  | Weak                                 | Strong (NL is relational)               |
| Example                 | “John is coughing”                   | “For all patients x, C(x)”              |

---

## Summary

- **First-Order Logic**:
    - Enables reasoning over domains, not just single cases.
    - Employs predicates, quantifiers, and functions for compact knowledge representation.
    - Strengths: Compactness, generalization, direct mapping to natural language semantics.
- **Used for**: Expert systems, knowledge graphs, semantic web, medical diagnosis.

---

## Practice & Exercises

- **Translate**:
    - “Everyone who studies AI and botany is cool.”
        - $∀x: A(x) ∧ B(x) → C(x)$
    - “There's someone who studies botany but isn't cool.”
        - $∃x: B(x) ∧ ¬C(x)$
    - “Therefore, there is at least one person who doesn't study AI.”
        - Deduce using FOL chain

- **Animal domain**:
    - “Wherever there are deer, there are also lions. There is at least one deer in Serengeti. Therefore, there must also be a lion in Serengeti.”
        - FOL mapping and inference


