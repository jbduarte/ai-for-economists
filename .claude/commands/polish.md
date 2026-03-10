---
name: polish
description: Context-aware prose polishing for academic economics papers. Takes a passage, locates it within the paper, builds full context (core message, key results, section function, paragraph purpose), diagnoses every sentence, and rewrites with architectural discipline. Use when refining specific passages, tightening prose, or improving the argumentative coherence of a section. Triggers include "polish this passage," "tighten this paragraph," "improve this section," or any request to refine existing academic prose.
---

# Polish: Context-Aware Academic Prose Refinement

This skill takes a passage from an economics paper, understands its exact role within the paper's architecture, and produces a tighter, more purposeful rewrite. Every edit is justified by the passage's context — not by generic "improvement."

## When to Use

- Refining a specific passage, paragraph, or section of a draft
- Tightening prose that feels loose, repetitive, or disconnected from the paper's argument
- Ensuring a passage properly serves the paper's narrative arc
- After writing a first draft with `/lucas-carvalho-style` and wanting to sharpen it

## Invocation

The user provides:
1. **The passage** to polish (pasted text, or a pointer like "paragraph 2 of Section 4")
2. **The paper** (file path to the .tex or .md file, or the full paper in context)

If the user only provides the passage without the paper, **ask for the paper**. Polishing without full paper context produces generic edits — the entire point of this skill is context-aware refinement.

## Execution Protocol

### Phase 1: Build Context Stack

Read the full paper and extract, in this order:

**Layer 1 — Paper-level context:**
- **Core message**: The single sentence a reader should remember. Not the question — the answer.
- **Key results**: The 3-5 findings with their magnitudes and qualifications.
- **Intellectual stakes**: What prior belief does this paper update? For whom?
- **Narrative arc**: Puzzle → framework → evidence → resolution.

**Layer 2 — Section-level context:**
- **Section function**: What job does this section perform in the paper's argument? State in one sentence.
- **Section position in arc**: Where are we in the narrative? What has the reader already accepted? What must they accept next?

**Layer 3 — Local context:**
- **Surrounding paragraphs**: Read the paragraph before and after the target passage. What argument is being built across this sequence?
- **Paragraph purpose**: What single claim does the target paragraph make? How does it advance the section's function?

**Layer 4 — Results awareness:**
- **Relevant results**: Which of the paper's key findings does this passage relate to (directly or indirectly)?
- **Consistency check**: Does the passage make any claim not supported by actual results? Does it omit results that would strengthen its argument?

Present this context stack to the user as a brief summary before proceeding to diagnosis. Format:

```
CONTEXT STACK
─────────────
Core message: [one sentence]
Section function: [one sentence]
Paragraph purpose: [one sentence]
Relevant results: [list the specific findings this passage connects to]
Narrative position: [what the reader has accepted so far → what this passage must accomplish → what comes next]
```

### Phase 1.5: Specialist Swarm (for sections or full introductions)

When the passage being polished is a **full section** (e.g., the entire introduction) or spans **more than 3 paragraphs**, launch a swarm of specialist agents in parallel before proceeding to the sentence-level diagnosis. For shorter passages (1-3 paragraphs), skip directly to Phase 2.

The swarm produces findings that feed into Phase 2's diagnosis table. Each agent reads the passage through a single specialized lens and returns a structured list of issues. Launch all four agents **simultaneously** using the Task tool.

#### Agent 1: Hostile Referee

**Prompt focus**: Identification concerns, overclaiming, missing caveats, framing weaknesses.

For each sentence, ask: "What objection would a hostile referee at a top-5 journal raise?"

Flag sentences that:
- Invite an identification objection ("isn't this just picking up the business cycle?")
- State results more strongly than the evidence supports (e.g., claiming blanket robustness when one specification fails)
- Present descriptive evidence using causal language ("governs," "determines" when the design supports "is associated with")
- Frame subsample splits as "testable predictions" when they are estimated from the same data
- Omit important caveats that appear in the paper's own results section
- Make novelty claims stronger than the literature warrants

Output format: For each finding — the exact sentence, the referee's objection (phrased as they would write it), severity (CRITICAL/MODERATE/MINOR), and a suggested rewrite that preempts the objection.

#### Agent 2: Logic & Argumentation

**Prompt focus**: Argument chains, hidden premises, scope overreach, conditional vs. unconditional claims, cross-section consistency.

For every argument in the passage, trace the chain: Premise 1 + Premise 2 → Conclusion.

Flag any link where:
- A premise is unstated or implicit (e.g., "integration amplifies transmission" assumes a specific causal channel — is it stated?)
- The conclusion exceeds the premises' scope (e.g., premises establish a result for prices, but the conclusion is stated for "macroeconomic outcomes" including output)
- A conditional claim is presented as unconditional (e.g., "FI is a state variable in its own right" — conditional on the identification tests holding)
- The passage contradicts claims made elsewhere in the paper (e.g., intro says "survives all tests" but robustness section says GDP fails one)
- A hidden quantifier creates ambiguity (e.g., "no detectable effect" could mean "point estimate is zero" or "statistically insignificant")
- The argument jumps from one step to the next without establishing the logical connection

Output format: For each finding — the argument chain (premises → conclusion), the logical gap, severity (CRITICAL/MODERATE/MINOR), and the missing premise or rewrite that closes the gap.

#### Agent 3: Math & Numbers Auditor

**Prompt focus**: Every quantitative claim verified against the paper's actual tables, figures, and results text.

For EVERY number in the passage:
- Locate the source in the paper (section, table, figure, equation)
- Verify exact match or flag discrepancy
- Check that verbal descriptions match numerical values (e.g., "about two years" for a peak at quarter 9 — is that accurate?)
- Verify counts (number of countries, meetings, observations)
- Check internal arithmetic consistency (do regime differences equal the gap between high and low values?)
- Flag any number that appears in the passage but cannot be found in the paper body

Output format: For each number — [claim in passage] → [source in paper] → [Match? Yes/No/Approximate] → [discrepancy if any] → [severity].

#### Agent 4: AI Detection Scanner

**Prompt focus**: Patterns that would trigger AI detection tools or raise editor suspicion.

Analyze:
- **Sentence length variation**: List word counts, compute coefficient of variation (CV > 0.5 = human; CV < 0.3 = AI flag)
- **AI filler phrases**: Flag any instance from the standard lexicon (furthermore, moreover, notably, crucial, delve, underscores, nuanced, multifaceted, leveraging, pivotal, holistic, landscape, comprehensive, it is important to note, it is worth noting)
- **Structural repetition**: Do multiple paragraphs follow the same template?
- **"We show/find" density**: Count all result-reporting phrases; flag if > 3-4 in the passage
- **Hedging distribution**: Map where hedging occurs — AI hedges uniformly; human writers hedge weak results more than strong ones
- **Paragraph length uniformity**: Flag if all paragraphs are roughly equal length

Output format: For each flag — what was detected, where, severity (HIGH/MEDIUM/LOW), and a suggested fix. End with an overall risk assessment (LOW/MODERATE/HIGH).

#### Swarm Consolidation

After all four agents complete, consolidate their findings:

1. **Deduplicate**: If two agents flagged the same sentence (e.g., Hostile Referee and Logic both caught an overclaim), keep the more specific diagnosis
2. **Cross-reference**: Some issues only become visible by combining findings (e.g., Agent 3 finds a number is wrong AND Agent 1 finds the sentence overclaims — the fix must address both)
3. **Priority sort**: CRITICAL findings from any agent take precedence; within severity, prefer findings from the Hostile Referee (most consequential for publication)

Present the consolidated findings to the user as a **Swarm Report** before proceeding to Phase 2:

```
SWARM REPORT
────────────
CRITICAL [N findings]
1. [Source agent] — [sentence] — [issue] — [suggested fix]
2. ...

MODERATE [N findings]
1. ...

MINOR [N findings]
1. ...

AI DETECTION: [LOW/MODERATE/HIGH risk] — [summary]
```

The swarm findings then feed directly into Phase 2's diagnosis table, populating the "Referee risk" and "Issues" columns with specific, verified problems rather than generic assessments.

### Phase 2: Sentence-Level Diagnosis

For each sentence in the passage, identify:

1. **Role**: Claim / Evidence / Qualification / Transition / Synthesis — or **Unclassifiable** (which means it's likely filler)
2. **Serves context?**: Does this sentence serve the paragraph's purpose? Yes / Partially / No
3. **Connects to core message?**: Can you trace a path from this sentence to the paper's core message? Direct / Indirect / Untraceable
4. **Craft issues**: Any of the following:
   - Buries important information in a subordinate clause
   - Uses vague language where the paper's actual results provide specifics
   - Hedges unnecessarily (or insufficiently)
   - Opens with throat-clearing ("It is important to note that...")
   - Passive voice where active would be stronger
   - Redundant with a neighboring sentence
   - Breaks the paragraph's argumentative flow
5. **Referee risk**: Read each sentence as a hostile referee looking for flaws. Flag any sentence that:
   - Invites an identification objection ("isn't this just picking up X?")
   - Narrows the identifying variation to a single episode when broader variation exists
   - Makes a causal claim without acknowledging the identification strategy that supports it
   - Overstates precision or generality beyond what the data can support
   - Presents a design choice without preempting the obvious alternative a referee would suggest
   - Frames a limitation as if it doesn't exist rather than acknowledging and addressing it
   For each flagged sentence, state the specific objection a referee would raise and propose a rewrite that preempts it.

Present the diagnosis as a compact table:

```
DIAGNOSIS
─────────
#  | Role         | Serves para? | Core connection | Referee risk                              | Issues
1  | Claim        | Yes          | Direct          | —                                         | —
2  | Evidence     | Partially    | Indirect        | —                                         | Buries magnitude in subordinate clause
3  | Claim        | Yes          | Direct          | "Isn't this just picking up the crisis?"   | Narrows variation to one episode
4  | Transition   | Yes          | Indirect        | —                                         | Weak; doesn't propel reader forward
...
```

### Phase 3: Rewrite

Produce the polished passage with the following discipline:

**Structural rules:**
- Every sentence must have a classifiable role (claim/evidence/qualification/transition/synthesis)
- The paragraph must open with a topic sentence that states its claim
- The paragraph must close with a synthesis or transition — never trail off on evidence
- No sentence may be redundant with another

**Contextual rules:**
- Echo specific language from the paper's introduction or core message where results are being delivered (threading)
- Use the paper's actual magnitudes and result descriptions — never vague where specifics exist
- Calibrate hedging to the actual strength of the evidence: strong results get confident language; suggestive results get appropriately qualified language
- If the passage is in the results section, lead with the finding, not with methodology description
- If the passage is in the introduction, ensure every previewed claim has a corresponding result in the paper

**Voice rules (Lucas-Carvalho):**
- Apply the Lucas-Carvalho style guidelines from the `lucas-carvalho-style` skill
- Match the mode to the section: Lucas voice for theoretical/framing sections, Carvalho voice for empirical sections, blended for introductions and conclusions
- Maintain the author's argument and intent — polish the prose, don't rewrite the economics

### Phase 4: Present the Revision

Output the polished passage, then provide a **change summary** explaining each substantive edit:

```
CHANGES
───────
- Sentence 1: Sharpened topic sentence to state the claim directly instead of approaching it obliquely
- Sentence 2: Moved coefficient estimate to stress position; replaced "there is an effect" with "consumption contracts by 1.2 percent"
- Sentence 3: DELETED — redundant with sentence 1; added no new information
- Sentence 4: Replaced generic transition ("We also find") with threaded transition connecting to Section 3 mechanism
- Sentence 5 (new): Added synthesis sentence that connects the paragraph's finding to the core message
```

**Do not**:
- List cosmetic changes (word swaps that don't affect meaning or architecture)
- Describe changes as "improved clarity" without saying *how*
- Make changes without justification tied to one of the four context layers

## Interaction Patterns

### If the passage is fine
Say so. Not every passage needs rewriting. If the diagnosis shows all sentences serving their roles with traceable connections to the core message, report: "This passage is architecturally sound. No substantive edits needed." Optionally flag minor craft improvements.

### If the problem is structural, not prose
Sometimes the issue isn't word-level — the paragraph is making the wrong claim for its position, or the section is covering the wrong ground. In this case, flag the structural issue before attempting to polish prose: "The prose is competent, but this paragraph is doing work that belongs in [other section]. Rewriting the sentences won't fix a misplaced argument."

### If context is ambiguous
If you cannot determine the passage's purpose from the paper context, ask: "I can see this passage sits in Section 4 (Results), but I'm not sure which finding it's meant to present. Is this discussing [Result A] or [Result B]?" Do not guess.

### Iterative polishing
The user may ask you to re-polish after your first pass, or to polish the next paragraph. Maintain the context stack across iterations — do not re-derive it unless the user provides new information about the paper.

## Quality Standard

The polished passage should pass five tests:

1. **The deletion test**: Can any sentence be removed without loss? If yes, remove it.
2. **The role test**: Can every sentence's role be named? If not, rewrite or remove it.
3. **The thread test**: Can a reader trace why this passage exists in this paper? If the connection to the core message is not apparent, make it explicit.
4. **The referee test**: Would a hostile referee at a top-5 journal raise an objection to any sentence? If yes, rewrite to preempt the objection. Every CRITICAL finding from the swarm must be addressed; MODERATE findings should be addressed unless doing so would damage the prose.
5. **The numbers test**: Does every quantitative claim match the paper's actual results? If any number is wrong, fix it. If any verbal description mischaracterizes a numerical result, correct it.
