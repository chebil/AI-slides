---
layout: intro
transition: slide-left
---

<div style="background: linear-gradient(135deg, #e0eafc 0%, #cfdef3 100%); padding: 2rem; border-radius: 12px; box-shadow: 0 2px 8px rgba(0,0,0,0.07);">

# Chapter 2: Important Concepts in AI

</div>
---
layout: two-cols-header
---

## The concept of Agents
- An **agent** is anything that can be viewed as perceiving its environment through sensors and acting upon that environment through actuators.
- An agent can be a robot, a chatbot, or any other entity that can perceive and act. **The decisions of an agent are made in the context of its environment.**
- An **environment** is the surrounding or conditions in which an agent operates.
::left::

```mermaid
graph TD
    A[Agent] --> B[Perception]
    A --> C[Action]
    B --> D[Sensors]
    C --> E[Actuators]
```
::right::

```mermaid
graph TD
    A[Environment] --> B[State]
    A --> C[Observations]
    A --> D[Actions]
    B --> E[Initial State]
    B --> F[Goal State]
    C --> G[Sensor Data]
    D --> H[Possible Actions]
    D --> I[Constraints]
```

---

## Types of environments
- **Fully observable**: The agent has access to all relevant information about the environment at all times. 
- **Partially observable**: The agent has limited access to information.
- **Deterministic**: The outcome of an action is predictable and certain. 
- **Stochastic**: The outcome of an action is uncertain and may involve randomness.
- **Static**: The environment does not change while the agent is deliberating. 
- **Dynamic**: The environment can change while the agent is deliberating.
- **Discrete**: The number of possible states and actions is finite. 
- **Continuous**: The number of possible states and actions is infinite.

<div style="display: flex; gap: 2rem; align-items: flex-start;">
<div style="flex: 1;">

```mermaid
graph TD
 A[Chess Game] --> B[Fully Observable]
 A --> C[Deterministic]
    A --> D[Static]
    A --> E[Discrete]
``` 
</div>
<div style="flex: 1;">

```mermaid
graph TD
    B[Self-Driving Car] --> F[Partially Observable]
    B --> G[Stochastic]
    B --> H[Dynamic]
    B --> I[Continuous]
``` 
</div>
</div>
---

## Types of Agents

- **Simple Reflex Agents**: Act based on the current percept, ignoring the rest of the percept history.
- **Model-Based Reflex Agents**: Maintain an internal state to keep track of the world.
- **Goal-Based Agents**: Act to achieve specific goals, considering future actions.
- **Utility-Based Agents**: Act to maximize a utility function, which measures the desirability of different states.

<div align="center">

> **Agent examples**

</div>

| <span style="font-family: 'Segoe UI', 'Arial', sans-serif; font-weight: 700;">Agent</span>            | <span style="font-family: 'Segoe UI', 'Arial', sans-serif; font-weight: 700;">Sensor/Input</span>         | <span style="font-family: 'Segoe UI', 'Arial', sans-serif; font-weight: 700;">Actuator/Output</span>      | <span style="font-family: 'Segoe UI', 'Arial', sans-serif; font-weight: 700;">Objective/Evaluation</span>      | <span style="font-family: 'Segoe UI', 'Arial', sans-serif; font-weight: 700;">State/Environment</span>      |
|------------------|---------------------|----------------------|--------------------------|-----------------------|
| Cleaning Robot   | Camera, Joint sensor | Limbs, Joints        | Cleanliness              | Object positions      |
| Chess Agent      | Board input          | Move output          | Position score           | Chess board           |
| Self-driving Car | Camera, Sound sensor | Car controls         | Safety, Speed, Goals     | Traffic conditions    |
| Chatbot          | Keyboard             | Screen               | Chat quality             | Dialog history        |
---

## Inductive vs Deductive Reasoning

- **Deductive Reasoning**: Starts with a knowledge base of facts and use logic or other systematic methods in order to make inferences. There are several approaches to deductive reasoning, including search and logic-based methods.
- **Inductive Reasoning**: Starts with specific observations or examples and generalizes them to form broader rules or patterns. Inductive reasoning is often used in machine learning, where algorithms learn from data to make predictions or decisions.
<div align="center">
```mermaid
graph TD
    A[Deductive Reasoning] --> B[Knowledge Base]
    A --> C[Logic/Rules]
    B --> D[Specific Facts]
    C --> E[Inferences]
    
    F[Inductive Reasoning] --> G[Observations/Examples]
    F --> H[Generalization]
    G --> I[Specific Cases]
    H --> J[Broader Rules/Patterns]
```
</div>
---
