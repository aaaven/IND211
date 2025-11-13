## Prompting as Desining  
#### Crafting, Steering, and Collaborating with LLMs
##### By *Dr. [Aven Le ZHOU](https://www.aven.cc)*, 2025

---


### Goal

Move from **trial-and-error**<!-- .element: class="fragment grow highlight-current-red" --> to **structured, reflective prompting**<!-- .element: class="fragment grow highlight-current-red" -->

---

### My Working-in-Progress Prompt Builder

The prompt **anatomy**<!-- .element: class="fragment grow highlight-current-blue" -->, **tuning strategies**<!-- .element: class="fragment grow highlight-current-blue" -->, **iteration logs**<!-- .element: class="fragment grow highlight-current-blue" -->, **reflection & ethics**<!-- .element: class="fragment grow highlight-current-blue" -->, **documentation**<!-- .element: class="fragment grow highlight-current-blue" --> 

note:
This lecture reframes prompting as a design practice. Emphasize structure, iteration, and reflection.

---


### Learning Outcomes

- Understand prompt structure and how it matters
- Apply prompting strategies for creative tasks
- Iterate with critique loops for high-quality results

- Document and reflect on AI co-creation ethically

---

### Agenda 

1. From Commanding → Collaborating 
2. Anatomy of a Good Prompt 
3. Prompting Strategies & Demos 
4. Exercises: Build–Test–Reflect 
5. Ethics, Documentation, and Archive 

---

### Basic Ideas
#### *Commanding*<!-- .element: class="fragment grow highlight-current-red" --> vs *Prompting*<!-- .element: class="fragment grow highlight-current-red" -->

- Command = give task or requirement to LLMs 
- Prompt = interface between intention (from you) and inference (from LLMs)  
- Treat prompts like **design briefs**<!-- .element: class="fragment grow highlight-current-red" -->
    - scoped and contextualized
    - iteratable and testable

note:

Quick demo incoming to show effect of framing.


---

### Mini Demo
**From Commanding to Prompting or Collaborating**

---

### Commanding (low-context)  
> “Describe an apple.”

---

### Commanding (low-context)  

- One-way instruction with low context  
- AI acts as a passive executor  
- Output is literal, shallow, and disconnected from (unclear) intent  

---


### High-context, Co-thinking, i.e., Collaborating
“You are a sensory ethnographer documenting everyday objects. Describe an apple as if it were a microcosm of human–nature relations.  
Focus on how its form, texture, and symbolism reveal bodily sensation and cultural values. Conclude with a question that invites further exploration of somaesthetics and culture.”

note: 

you are thining for the other side of the collaborater

---

### Collaborating (high-context, co-thinking)  

- Adds **role**, **context**, and **intentional goal**  
- LLM now creates with human in collaborative context  
- Also opens space for iterative follow-up rather than a single answer  


note:

- How did the added **role**, **goal**, and **context** shift the quality of output?  
- These three elements are the foundation of what we call the **5-Part Prompt Builder** —  
  a way to collaborative design prompts as *design briefs* instead of commands.

---

### Prompt Anatomy

1. **Role / Persona** — who is the model acting as?  
2. **Task / Goal** — what action and outcome?  
3. **Context / Background** — constraints, references, datasets  
4. **Output Format / Style** (optional) — structure, tone, word limits  
5. **Examples** (optional) — few-shot scaffolds to anchor style

note:
**Heuristic:** clarity > length; constraints focus release creativity.

----

#### Try it after class

- **Role:** Speculative designer from 2080 investigating extinct interfaces  
- **Task:** Generate 3 alternative futures for human–AI co-habitation  
- **Context:** Use “companion species,” post-Anthropocene ecology  
- **Output:** 3 bullets, each ≤70 words, end with a design principle  
- **Examples:** Style akin to manifesto fragments, compressed, vivid

---

#### Common Prompt Tuning Strategies

- **Role Prompting** — steer expertise/voice  
- **Chain-of-Thought** — request stepwise reasoning  
- **Perspective Switching** — nonhuman, cross-cultural, temporal shifts  
- **Reflexive Looping** — self-critique, then revise  

----

- **Few-Shot Examples** — style/structure anchoring  
- **Constraint Prompting** — word count, schema, rubric  
- **Meta-Prompting** — “List 3 approaches before answering; pick one.”

---

### 🧩 From Demo 1: Role Prompting  

**Commanding (low-context)**  
> “Describe an apple.”

----

**Collaborating (high-context, co-thinking)**  
> “You are a sensory ethnographer documenting everyday objects.  
> Describe an apple as if it were a microcosm of human–nature relations.  
> Focus on how its form, texture, and symbolism reveal cultural values.  
> Conclude with a question that invites further exploration.”

----

- Adds **role**, **context**, and **goal**  
- Turns the AI into a **co-thinker**  
- Opens space for dialogue and iteration  

---

### 🧠 Demo 2 Guiding Reasoning with Chain-of-Thought (CoT)

----

> “You are a sensory ethnographer documenting everyday objects. Let’s reason step-by-step before describing the apple:  
> 1. Identify sensory qualities that make it unique.  
> 2. Reflect on how these connect to human–nature relations.  
> 3. Synthesize insights into a short ethnographic description.  
> 4. End with one question that invites me to respond.”

----

🧭 *Why it matters:*  
- Makes reasoning **explicit, executable and traceable**  
- Creates better hooks for critique or follow-up  
- Encourages **process transparency**  


---

### 🌍 Demo 3 Perspective Switching


----


> “You are an apple tree observing humans during harvest season.  
> Describe what you see and how you interpret their gestures.  
> Reflect on what this reveals about interdependence between species.”

----

🌿 *Why it matters:*  
- Opens new perspective and thinking of different stakeholders
- Encourages **empathy** 
- For example, for more-than-human design:
    - Add **post-anthropocentric** and **non-human perspective**
    - Shift focus from object → relation  

note:

- How does changing the **point of view** alter narrative tone or ethics?  
- Where could perspective switching be useful in your own design research?

---

### 🔁 Demo 4 — Reflexive Looping


----


**Step 1:** Use and continue the previous (tree’s-eye-view) output.  
**Step 2:** Follow up with:


----


> “Now, review your previous description from a human environmentalist’s perspective.  
> Identify three weaknesses (clarity, depth, bias).  
> Suggest specific revisions for each and produce a refined version.”


----


🪞 *Why it matters:*  
- Promotes **self-critique** and iterative improvement  
- Turns AI into a **critical collaborator**, not just generator  
- Models design thinking: test → critique → redesign  

---



### 🧩 Strategy Flow 

----

| Stage | Intent | Strategy  | AI Role |
|--------|-----------|------------------|-------------|
| 1 | Command | Execute | Tool |
| 2 | Structured Collaboration | Contextual creation | Collaborator |
| 3 | Chain-of-Thought | Show reasoning | Co-thinker |
| 4 | Perspective Switching | Reframe subjectivity | Empathic agent |
| 5 | Reflexive Loop | Critique-refine | Co-designer |

---

### 💬 Prompting as Designing? Why?

Prompt tuning is not a trick —  
it’s a **conversation design practice**.

----

Each layer adds a new dimension of relationship:
1. Clarity (structure)  
2. Transparency (reasoning)  
3. Relationality (perspective)  
4. Reflexivity (critique)



----


Together, they turn prompting into **collaborative thinking & designing process**.


---


## (Design) Iteration Logs 

Treat prompts like prototypes:

- V1: baseline  
- V2: add role, context & reasoning  
- V3: explore with perspectives
- V4: reflexive iteration
- V5: refine tone, structure, constrain output and include examples

---

**Analyse and always ask yourself:** 

- What changed? 
- What improved? 
- What to keep?


---


## How to get the Prompt?

### Just like Design
  
- Iterate with strategies and **document the path**  
- Ethics and technodiversity are **built into** the wording  
- Share to the **Prompt Archive** to grow collective intelligence

---


## From Command to Collaboration in Design Context

---

### ⚙️ Commanding (Low-context)

> “Generate design prompts for a sustainable wearable product.”

- One-way request  
- Output likely generic (e.g., “use recyclable materials,” “monitor health data”)  
- AI acts as an **idea vending machine**, not a collaborator  

---

### 🧱 Structured Collaboration (Prompt Anatomy Applied)


----


> **Role:** You are a circular-economy design strategist.  
> **Task:** Generate 5 design prompts for sustainable wearables.  
> **Context:** Focus on modular repairability, biosourced materials, and emotional longevity.  
> **Output Format:** Numbered list, ≤30 words per item, each including a measurable design focus.  
> **Example Style:** concise, actionable, research-informed.


----


✅ Adds clarity, scope, and actionable constraints.  
✅ AI now **thinks within your design framework**.

---

### Activity 1 (10’): Role Prompting

Think a similar idea (instead of sustainable wearable) and using the handout sheet:
1. Fill the **prompt anatomy (in section 1)**  
2. Draft **V1** and run it (your development and test of prompt can and should happen in a seperate window), log V1  
3. Note issues

Deliverable: V1 output + short notes Log table

note:

Walk the room; nudge for clearer tasks and formats.

---


### 🧠 Adding Chain-of-Thought Reasoning


----


> “You are a circular-economy design strategist.  
> Let’s reason step-by-step before generating the prompts:  
> 1. Identify sustainability challenges in wearable design.  
> 2. Map where interventions are possible.  
> 3. Create 5 design prompts addressing those leverage points.  
> 4. For each, add one metric that could evaluate success.”


----


🧭 *Why it matters:*  
- Makes design reasoning **explicit and excecutable, tracable and iteratable**  
- Generates outputs aligned with *design research logic*, not random creativity  


---

### 🔁 Reflexive Looping


----


> “Review your previous design prompts as if you were a sustainability reviewer.  
> Identify two weaknesses (feasibility, novelty, clarity).  
> Revise each prompt to address those issues and explain your reasoning.”


----


🪞 *Why it matters:*  
- Embeds **evaluation and iteration** in the prompting process  
- Mirrors a **design review cycle**: ideate → critique → refine  
- AI-self assess AI outputs like prototypes  
- What about your self-assessment of the prompts?


---

### 🌍 Perspective Switching (Optional Layer)


----


> “Now, switch perspective: you are a wearable product *after five years of use*.  
> Reflect on your own lifecycle and user relationship.  
> Suggest 3 redesign prompts that would extend your meaningful existence.”


----


🌿 *Why it matters:*  
- Promotes **empathetic thinking**  
- Adds **user–object relationality** and storytelling beyond antropocentric views  
- Perfect for speculative or critical design discussions  


---


## Activity 2 (15’): Iterate with a Strategy

Pick one strategy and apply:
- Chain-of-thought  
- Reflexive loop  
- Perspective switch

Create **V2**. Log changes and improvements.

Pick another strategy **V3**

Deliverable: V2 & V3 outputs + Iteration Log

---


---

### Documentation with the Iteration Log
### Prompt Design Sheet

- Keep **Prompt Output** in the sheet 
- Note strategy used and why, i.e., **what changed + why changed** in the sheet 
- Note experiences or failures captured: what not to do, dead ends, ambiguous phrasing, i.e., **Reflection** in the sheet
- This becomes **reproducible method** and **learning evidence**


---


## Activity 3 (15’): What about your tweaks?

Repeat any strategy with revisions and your thoughts

Create **V4, 5, 6 ...**. Log changes and improvements.

Deliverable: V4 & V5 ... outputs + Iteration Log

---


### Other Quick Tricks (Copy-Ready)


----


**Meta-planner:**  
“List 3 approaches to solve X. Compare pros/cons in a table. Choose the most suitable for constraints A/B/C and justify in 80 words.”

**Self-critique loop:**  
“Evaluate your previous answer against rubric R (clarity, rigor, novelty, ethics). Score 1–5 and propose revisions. Apply them.”


---


### Ethics & Technodiversity (WIP)

- Language frames the world: watch for bias, exclusion, monocultures  
- Cite AI assistance and note version/date  
- Verify factual claims; avoid false authority  
- Explore non-Western framings and multilingual robustness

---

### The Prompt Archive (Cohort Library)

Contribute:
- Final prompt (with 5-part snapshot)  
- 1–2 best outputs (text/image)  
- One-line “Why this works”

Benefits:
- Peer learning & benchmarking  
- Shared vocabulary for future cohorts


---


## Resources

- Handout: Prompt Builder & Reflection Sheet (PDF)  
- Class Prompt Archive (Excel Sheet link)  
- Optional reading list (prompting & critical AI literacies)

---



**Next:** apply this method in the upcoming project and attach the prompt appendix to submissions.