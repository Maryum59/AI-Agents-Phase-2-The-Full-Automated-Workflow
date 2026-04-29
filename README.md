# AI-Agents-Phase-2-The-Full-Automated-Workflow

Phase 2 takes all the individual agents built in Phase 1 and connects them together into one automated pipeline. The result: give the system a single sentence goal, and it produces a complete software project plan — with user stories, product features, and engineering tasks — all on its own.

---

## What Is This Project About?

Imagine a company wants to build a new software product called the **Email Router** — a tool that automatically sorts and forwards emails to the right people.

Normally, planning this product would require three different roles:

- A **Product Manager** who figures out what users need (writes user stories)
- A **Program Manager** who groups those needs into features
- A **Development Engineer** who breaks the features into technical tasks for developers

In Phase 2, all three roles are played by AI agents — working together automatically, in the right order, and checking each other's work.

---

## The Files in This Folder

| File | What It Is |
|---|---|
| `agentic_workflow.py` | The main file — sets up all agents and runs the full workflow |
| `workflow_output.txt` | The actual output produced when the workflow was run |
| `Screen shots required for phase.docx` | Course screenshots |

> **Note:** This file also reads a product specification document called `Product-Spec-Email-Router.txt` which describes what the Email Router product should do. That file needs to be in the same folder when running the code.

---

## How the Workflow Works — Step by Step

The whole workflow is triggered by this single sentence:

> *"Create a complete project plan for the Email Router product including user stories, product features, and development tasks."*

From that one sentence, here is what happens automatically:

---

### Step 1 — Break the Goal into Steps

The **Action Planning Agent** reads the sentence above and breaks it into a clear list of steps:

1. Define user stories
2. Define product features
3. Define development tasks

Think of it like a manager reading a goal statement and turning it into an action plan.

---

### Step 2 — Route Each Step to the Right Specialist

The **Routing Agent** looks at each step and decides which specialist AI should handle it:

| Step | Goes To |
|---|---|
| "Define user stories" | Product Manager Agent |
| "Define product features" | Program Manager Agent |
| "Define development tasks" | Development Engineer Agent |

It picks the right specialist automatically, using the meaning of the step — not a hardcoded rule.

---

### Step 3 — Each Specialist Does Their Job (With a Quality Check)

Each specialist has two parts working together:

1. A **Worker** who produces the answer
2. A **Judge** who checks if the answer meets the required format

If the answer fails the check, a **Fixer** tells the worker what to correct, and the worker tries again — up to 3 times.

---

#### Specialist 1: Product Manager Agent — Writes User Stories

User stories describe what a user needs from the product. They always follow this pattern:

> *"As a [type of user], I want [something] so that [benefit]."*

**Real output from this project:**
- *"As a user, I want to set up email forwarding rules to automatically route incoming emails to specific folders."*
- *"As a user, I want to create custom email filters to categorize and prioritize incoming emails."*
- *"As a user, I want to track the status of sent emails, including delivery and read receipts."*

The judge checks: does every story follow the "As a... I want... so that..." format? If not, the worker is told to fix it.

---

#### Specialist 2: Program Manager Agent — Groups Stories into Features

The Program Manager takes the user stories and groups related ones together into named product features.

**Real output from this project:**

**Feature: Email Forwarding Rules**
- What it does: Lets users create rules to send emails to specific folders automatically
- Key ability: Automated routing based on user-defined rules
- User benefit: Saves time by keeping the inbox organized

**Feature: Custom Email Filters**
- What it does: Lets users filter and prioritize incoming emails
- Key ability: Personalized email categorization
- User benefit: Reduces clutter, helps users focus on what matters

The judge checks: does every feature have a Name, Description, Key Functionality, and User Benefit? If not, the worker fixes it.

---

#### Specialist 3: Development Engineer Agent — Writes the Technical Tasks

The Development Engineer takes each feature and breaks it into concrete tasks for software developers to build.

Each task follows this structure:
- **Task ID** — a tracking number
- **Task Title** — what needs to be built
- **Related User Story** — which user need this covers
- **Description** — what the developer actually has to do
- **Acceptance Criteria** — how to know when it's done
- **Estimated Effort** — how long it might take
- **Dependencies** — what other tasks must be done first

The judge checks: does every task include all 7 required fields? If not, the worker fixes it.

---

## The Full Picture — How All the Agents Connect

```
  One sentence goal
        ↓
  Action Planning Agent
  (breaks it into steps)
        ↓
  ┌─────────────────────────────────────────┐
  │           Routing Agent                 │
  │  (sends each step to the right person)  │
  └────────────┬──────────────┬─────────────┘
               │              │              │
               ↓              ↓              ↓
      Product Manager   Program Manager   Dev Engineer
       (user stories)    (features)        (tasks)
               │              │              │
               ↓              ↓              ↓
           Evaluator      Evaluator      Evaluator
         (checks work)  (checks work)  (checks work)
               │              │              │
               └──────────────┴──────────────┘
                              ↓
                    Final Project Plan
```

---

## What the Final Output Looks Like

When the workflow finishes, you have a complete software project plan:

1. A list of **user stories** — what users need the product to do
2. A list of **product features** — the capabilities the product will have
3. A list of **engineering tasks** — the specific work developers need to do to build it

All of this is generated from one sentence, checked for quality, corrected if needed, and delivered automatically.

---

## The Difference Between Phase 1 and Phase 2

| | Phase 1 | Phase 2 |
|---|---|---|
| **What it does** | Builds each agent separately and tests them one by one | Connects all agents into a single automated pipeline |
| **How you use it** | Run each file individually | Run one file — the whole workflow runs automatically |
| **The result** | Individual AI responses | A complete software project plan |

---

## How to Run This Project

**What you need:**
- Python installed
- An OpenAI API key
- The `Product-Spec-Email-Router.txt` file in the same folder
- The agents from Phase 1 available as a module called `workflow_agents`

**Install dependencies:**
```
pip install openai python-dotenv numpy pandas
```

**Create a `.env` file in this folder:**
```
OPENAI_API_KEY=your_key_here
```

**Run the workflow:**
```
python agentic_workflow.py
```

The terminal will show each step being executed, what agent handled it, how many attempts it took, and the final result.

---

## Course

This project is part of the **AI Agents with LLMs** course on Udacity.
