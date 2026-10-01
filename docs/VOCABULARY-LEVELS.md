# Vocabulary Vault — Vocabulary Classification System

## Overview

Vocabulary Vault uses a structured classification model to organize words
by **learning difficulty, linguistic complexity, usage frequency, register,
and approximate language-proficiency level**.

The system combines two complementary approaches:

1. **Vocabulary Vault Difficulty Levels** — a project-specific classification
   designed for practical vocabulary learning and organization.
2. **CEFR References** — standardized proficiency references from A1 to C2.

These systems are related, but they are **not equivalent**.

> Vocabulary Vault difficulty describes the relative complexity of a
> vocabulary item. CEFR describes language proficiency and provides a useful
> reference framework for vocabulary organization.

The classification model is intended to make a large vocabulary collection
easier to browse, prioritize, study, and revise.

---

## Classification Model

At a high level:

```text
                    VOCABULARY ENTRY
                           │
             ┌─────────────┴─────────────┐
             │                           │
             ▼                           ▼
    Vocabulary Difficulty          CEFR Reference
             │                           │
             ▼                           ▼
 Easy / Medium / Hard /           A1 → A2 → B1 →
    Shashi Tharoor                B2 → C1 → C2
             │                           │
             └─────────────┬─────────────┘
                           ▼
                Vocabulary Classification
                           │
                           ▼
                 Learning & Revision
```

The two systems provide different perspectives on the same vocabulary item.

---

# 1. Vocabulary Vault Difficulty Levels

Vocabulary Vault currently uses four principal difficulty categories:

| Level | Classification | General Description |
|---|---|---|
| 🟢 | **Easy** | Common, accessible vocabulary frequently encountered in everyday English |
| 🟡 | **Medium** | Moderately advanced vocabulary requiring greater contextual or semantic understanding |
| 🔴 | **Hard** | Advanced, academic, literary, technical, or semantically complex vocabulary |
| 🟣 | **Shashi Tharoor** | Exceptionally sophisticated, rare, erudite, ornate, archaic, or sesquipedalian vocabulary |

These levels are **Vocabulary Vault classifications**.

They are not official CEFR categories.

---

## Easy

**Easy** represents vocabulary that is generally common, concrete, familiar,
and relatively straightforward to understand or use.

Typical characteristics include:

- High-frequency everyday vocabulary
- Familiar concepts
- Straightforward meanings
- Common conversational usage
- Simple contextual interpretation
- Limited semantic ambiguity
- Early-stage vocabulary acquisition

Examples of contexts where Easy vocabulary frequently appears:

```text
Daily conversation
School
Family
Food
Travel
Shopping
Basic emotions
Common actions
Everyday objects
Simple descriptions
```

### Approximate Reference

```text
Vocabulary Vault: Easy
Approximate CEFR: A1–A2
```

This mapping is approximate rather than absolute.

A common word can still have advanced secondary meanings, idiomatic uses,
or specialized senses.

---

## Medium

**Medium** represents vocabulary that goes beyond basic everyday English but
remains reasonably common in educated conversation, general reading,
professional communication, and mainstream writing.

Typical characteristics include:

- Moderate semantic complexity
- Less frequent everyday usage
- More abstract concepts
- Greater dependence on context
- Broader synonym relationships
- Formal or professional usage
- Intermediate-to-upper-intermediate reading vocabulary

Common contexts include:

```text
News
Workplace communication
General literature
Essays
Professional writing
Detailed conversation
Non-specialist academic material
Opinion and analysis
```

### Approximate Reference

```text
Vocabulary Vault: Medium
Approximate CEFR: B1–B2
```

Medium vocabulary often represents the transition from functional English
toward more expressive and precise language.

---

## Hard

**Hard** represents advanced vocabulary requiring stronger linguistic,
contextual, academic, literary, or conceptual knowledge.

Typical characteristics include:

- Lower frequency
- Greater abstraction
- Nuanced semantic distinctions
- Formal register
- Academic usage
- Literary usage
- Specialized contexts
- Complex synonym relationships
- Greater contextual dependence
- Advanced reading comprehension

Common contexts include:

```text
Academic writing
Advanced journalism
Literature
Research
Formal argumentation
Law
Philosophy
Technical discourse
Professional analysis
High-level essays
```

### Approximate Reference

```text
Vocabulary Vault: Hard
Approximate CEFR: C1–C2
```

A Hard classification does not automatically mean that a word belongs to
C1 or C2 in an official CEFR vocabulary inventory.

The classification reflects the learning difficulty used by Vocabulary Vault.

---

## Shashi Tharoor

**Shashi Tharoor** is a custom Vocabulary Vault category for exceptionally
sophisticated vocabulary.

The name is used as a memorable project label for words characterized by
unusually elevated, erudite, ornate, rare, literary, archaic, or
sesquipedalian usage.

Typical characteristics include:

- Very low everyday frequency
- Highly sophisticated register
- Rare literary vocabulary
- Archaic or historical usage
- Unusual etymological forms
- Highly specific semantic distinctions
- Words primarily encountered in advanced literature or scholarship
- Vocabulary that may be unfamiliar even to proficient English speakers

Typical contexts can include:

```text
Classical literature
Literary criticism
Historical writing
Philosophy
Rhetoric
Specialized scholarship
Ornate prose
Rare formal expression
Advanced wordplay
```

### Classification Reference

```text
Vocabulary Vault: Shashi Tharoor
CEFR: No direct official equivalent
```

This distinction is important.

CEFR officially ends at **C2**. Vocabulary Vault does not define
"Shashi Tharoor" as an official level above C2.

Instead, it functions as a project-specific category for vocabulary whose
rarity, register, or sophistication makes the standard Easy–Hard
classification less descriptive.

---

# 2. Difficulty Classification Criteria

Vocabulary difficulty cannot reliably be determined from a single property.

Vocabulary Vault conceptually considers several dimensions.

```text
                    WORD / PHRASE
                          │
       ┌──────────────────┼──────────────────┐
       │                  │                  │
       ▼                  ▼                  ▼
   Frequency          Complexity          Register
       │                  │                  │
       ├──────────┐       │       ┌──────────┤
       ▼          ▼       ▼       ▼          ▼
   Familiarity  Context  Nuance  Domain   Rarity
       │          │       │       │          │
       └──────────┴───────┼───────┴──────────┘
                          ▼
                 Difficulty Decision
```

The major considerations are described below.

---

## Frequency

How commonly is the vocabulary encountered?

```text
Very Common
    ↓
Common
    ↓
Occasional
    ↓
Uncommon
    ↓
Rare
```

Frequency is useful, but frequency alone does not determine difficulty.

---

## Semantic Complexity

Some words describe straightforward concepts, while others encode highly
specific or abstract distinctions.

For example:

```text
Concrete concept
      ↓
Moderately abstract concept
      ↓
Highly nuanced / abstract concept
```

Greater semantic precision can increase learning difficulty.

---

## Context Dependence

A word may be easy to understand in one context but difficult in another.

Classification can therefore consider whether understanding requires:

- Specialized background knowledge
- Literary context
- Cultural context
- Historical context
- Technical context
- Idiomatic interpretation

---

## Register

Vocabulary may belong primarily to a particular register:

```text
Informal
Neutral
Formal
Academic
Technical
Literary
Archaic
```

Highly specialized or elevated registers generally increase practical
learning difficulty.

---

## Familiarity

Difficulty also depends on how likely an English learner is to have
encountered the vocabulary before.

A technically simple definition does not necessarily make an extremely rare
word easy to learn.

---

## Semantic Nuance

Words with subtle distinctions from close synonyms can require greater
understanding.

For example:

```text
General Meaning
      │
      ▼
Precise Meaning
      │
      ▼
Contextual Nuance
      │
      ▼
Register Difference
```

Vocabulary Vault therefore treats nuanced semantic understanding as part of
difficulty rather than relying only on definition length.

---

## Domain Specificity

Some vocabulary is concentrated within particular domains.

Examples include:

```text
Law
Medicine
Computer Science
Economics
Philosophy
Religion
Literature
Politics
Psychology
Science
History
```

Domain-specific vocabulary can be difficult even when its definition is
relatively concise.

---

# 3. Difficulty Decision Model

The conceptual classification process can be represented as:

```text
New Vocabulary Entry
        │
        ▼
How common is it?
        │
        ▼
How complex is the meaning?
        │
        ▼
How much context is required?
        │
        ▼
What register does it belong to?
        │
        ▼
Is it specialized, literary, or archaic?
        │
        ▼
How subtle are its semantic distinctions?
        │
        ▼
Assign Vocabulary Vault Difficulty
```

This is intentionally a learning-oriented classification model rather than
a rigid mathematical scoring system.

Language is contextual, and vocabulary difficulty can vary across speakers,
domains, and learning backgrounds.

---

# 4. CEFR Reference System

Vocabulary Vault also uses the **Common European Framework of Reference for
Languages (CEFR)** as a secondary organizational reference.

The principal CEFR proficiency levels are:

| Level | Common Label | General Description |
|---|---|---|
| **A1** | Beginner | Can understand and use very basic everyday expressions |
| **A2** | Elementary | Can communicate in simple and routine situations |
| **B1** | Intermediate | Can handle familiar situations and understand the main points of clear standard language |
| **B2** | Upper-Intermediate | Can understand more complex texts and communicate with greater fluency and detail |
| **C1** | Advanced | Can use language flexibly and effectively across demanding academic, professional, and social contexts |
| **C2** | Mastery / Proficiency | Can understand and express highly complex ideas with very high precision and flexibility |

---

## CEFR Progression

```text
Basic User
│
├── A1  Beginner
└── A2  Elementary

Independent User
│
├── B1  Intermediate
└── B2  Upper-Intermediate

Proficient User
│
├── C1  Advanced
└── C2  Mastery / Proficiency
```

Or as a progression:

```text
A1
 │
 ▼
A2
 │
 ▼
B1
 │
 ▼
B2
 │
 ▼
C1
 │
 ▼
C2
```

---

# 5. A1 — Beginner

A1 represents foundational language ability.

Vocabulary associated with this range commonly covers:

- Personal information
- Family
- Numbers
- Basic objects
- Food and drink
- Everyday actions
- Simple descriptions
- Common places
- Basic questions
- Essential social expressions

Conceptually:

```text
Basic vocabulary
      +
Immediate everyday needs
      +
Simple communication
```

Vocabulary Vault generally associates much of this range with **Easy**
vocabulary.

---

# 6. A2 — Elementary

A2 extends basic vocabulary into a wider range of familiar situations.

Common areas include:

- Shopping
- Travel
- Employment
- Daily routines
- Local geography
- Personal experiences
- Simple opinions
- Basic social communication

A2 vocabulary remains relatively accessible but provides greater expressive
range than A1.

Vocabulary Vault generally places much of A1–A2 vocabulary within the
**Easy** category.

---

# 7. B1 — Intermediate

B1 represents vocabulary useful for independent communication across many
familiar situations.

Typical areas include:

- Work
- Education
- Travel
- Personal interests
- Experiences
- Plans
- Opinions
- Explanations
- Common abstract concepts

Vocabulary becomes less dependent on purely concrete everyday objects and
begins supporting more detailed expression.

B1 commonly overlaps with Vocabulary Vault's **Medium** category.

---

# 8. B2 — Upper-Intermediate

B2 vocabulary supports more sophisticated communication and comprehension.

Typical characteristics include:

- More abstract vocabulary
- Greater precision
- Broader synonym knowledge
- Professional communication
- Detailed argumentation
- Complex reading
- More nuanced expression

B2 vocabulary can span both **Medium** and **Hard** depending on the
individual word and its usage.

---

# 9. C1 — Advanced

C1 represents advanced language use across demanding contexts.

Vocabulary at this level can include:

- Academic terminology
- Formal expressions
- Nuanced adjectives and verbs
- Advanced collocations
- Less common idioms
- Specialized professional vocabulary
- Sophisticated argumentation
- Literary language

C1 frequently overlaps with Vocabulary Vault's **Hard** classification.

---

# 10. C2 — Mastery / Proficiency

C2 represents extremely high language proficiency.

Vocabulary associated with advanced C2-level use can involve:

- Fine semantic distinctions
- Idiomatic flexibility
- Highly precise expression
- Advanced literary vocabulary
- Sophisticated register control
- Rare or specialized vocabulary
- Subtle rhetorical choices

However:

> **C2 does not mean knowing every rare English word.**

English contains enormous amounts of historical, technical, dialectal,
literary, and specialist vocabulary that even highly proficient speakers
may not know.

This is one reason Vocabulary Vault keeps its **Shashi Tharoor** category
separate from CEFR.

---

# 11. Relationship Between Difficulty and CEFR

For practical organization, Vocabulary Vault uses the following approximate
relationship:

| Vocabulary Vault Classification | Approximate CEFR Reference |
|---|---|
| **Easy** | Primarily A1–A2 |
| **Medium** | Primarily B1–B2 |
| **Hard** | Primarily C1–C2 |
| **Shashi Tharoor** | No direct official equivalent; often exceptionally rare or sophisticated vocabulary |

The mapping should be understood as:

```text
Easy ───────────────► A1 / A2

Medium ─────────────► B1 / B2

Hard ───────────────► C1 / C2

Shashi Tharoor ─────► Rare / Erudite / Literary /
                       Archaic / Exceptionally Sophisticated
                       (no official CEFR level)
```

These relationships are intentionally approximate.

---

# 12. Why the Mapping Is Not One-to-One

A vocabulary item's difficulty is not identical to a learner's CEFR level.

For example:

```text
Common word
      +
Rare secondary meaning
```

may produce different difficulty judgments depending on which meaning is
being studied.

Similarly:

```text
Simple technical term
```

may be easy for a specialist but unfamiliar to a general learner.

Therefore:

```text
Vocabulary Difficulty ≠ CEFR Proficiency
```

Vocabulary Vault uses both because each captures different information.

---

# 13. Tags and Classification

Difficulty and CEFR references can work alongside topical and contextual
tags.

Conceptually:

```text
Word / Phrase
      │
      ├── Difficulty
      │      └── Easy / Medium / Hard / Shashi Tharoor
      │
      ├── CEFR
      │      └── A1 / A2 / B1 / B2 / C1 / C2
      │
      └── Tags
             ├── Academic
             ├── Literary
             ├── Formal
             ├── Informal
             ├── Technical
             └── Domain-specific categories
```

This creates a multidimensional classification model rather than forcing
every vocabulary item into a single label.

---

# 14. Classification Examples

The following examples demonstrate the intended logic conceptually.

| Vocabulary Type | Likely Difficulty | Typical CEFR Reference |
|---|---|---|
| Common everyday object | Easy | A1–A2 |
| Familiar everyday action | Easy | A1–A2 |
| Moderately abstract term | Medium | B1–B2 |
| Formal professional vocabulary | Medium / Hard | B2–C1 |
| Academic terminology | Hard | C1–C2 |
| Advanced literary vocabulary | Hard | C1–C2 |
| Rare ornate expression | Shashi Tharoor | No direct equivalent |
| Archaic literary term | Shashi Tharoor | No direct equivalent |

These examples illustrate tendencies rather than strict rules.

---

# 15. Classification in the Vocabulary Vault Workflow

Classification forms part of the broader vocabulary-management process.

```text
Vocabulary Entry
       │
       ▼
Understand Meaning
       │
       ▼
Analyze Usage
       │
       ├── Frequency
       ├── Register
       ├── Complexity
       ├── Context
       ├── Domain
       └── Nuance
       │
       ▼
Assign Difficulty
       │
       ▼
Add CEFR Reference
       │
       ▼
Add Relevant Tags
       │
       ▼
Vocabulary Vault
```

Classification therefore describes more than whether a word simply
"looks difficult."

---

# 16. Classification in Generated Views

Difficulty information is also useful when presenting vocabulary in
generated learning views.

Conceptually:

```text
Vocabulary Vault
       │
       ├── Word
       ├── Meaning
       ├── Difficulty
       └── Other Information
              │
              ▼
       Generated Views
              │
       ┌──────┴──────┐
       ▼             ▼
    A To Z       Only Words
```

Difficulty can provide a quick visual signal while reviewing large
vocabulary collections.

The exact presentation and color implementation are part of the private
production system.

---

# 17. Classification and Anki

The same classification model can support flashcard-based revision.

```text
Vocabulary Vault
       │
       ▼
Difficulty + CEFR + Tags
       │
       ▼
Structured Flashcards
       │
       ▼
Anki
       │
       ▼
Targeted Revision
```

For example, classification can conceptually support study sessions focused
on:

```text
Easy vocabulary
Medium vocabulary
Hard vocabulary
Rare vocabulary
B2 vocabulary
C1 vocabulary
Academic vocabulary
Literary vocabulary
```

The complete Vocabulary Vault Anki collection is maintained separately from
this public repository.

See:

[Anki Flashcards](ANKI-FLASHCARDS.md)

---

# 18. Celestial Pinnacle

**Celestial Pinnacle** is an additional Vocabulary Vault designation used
for exceptionally rare, sophisticated, expressive, or linguistically
noteworthy vocabulary.

It is a **project-specific designation**, not an official CEFR level.

It should therefore never be represented as:

```text
A1 → A2 → B1 → B2 → C1 → C2 → Celestial Pinnacle
```

That would incorrectly imply that it belongs to the official CEFR scale.

Instead, its conceptual relationship is:

```text
Official CEFR
A1 → A2 → B1 → B2 → C1 → C2


Vocabulary Vault
Easy → Medium → Hard → Shashi Tharoor
                         │
                         ▼
              exceptionally rare /
              sophisticated vocabulary

Additional designation:
Celestial Pinnacle
```

Celestial Pinnacle can be used for vocabulary that is particularly notable
for combinations of:

- Extreme rarity
- Exceptional sophistication
- Literary significance
- Historical or archaic character
- Highly precise semantic nuance
- Unusual expressive power
- Specialist or scholarly usage

It remains separate from official CEFR proficiency terminology.

---

# 19. Classification Limitations

No vocabulary classification system is perfectly objective.

Difficulty can vary according to:

- Native language
- Educational background
- Profession
- Reading habits
- Age
- Cultural exposure
- Technical specialization
- Personal vocabulary size
- Context

For example:

```text
Medical term
```

may be easy for a physician and difficult for a general learner.

Likewise:

```text
Rare literary word
```

may be familiar to an avid reader while remaining unknown to many fluent
speakers.

Vocabulary Vault classifications should therefore be interpreted as
**structured learning guidance**, not universal linguistic judgments.

---

# 20. Classification Principles

The Vocabulary Vault classification system follows several principles.

## Practicality Over Artificial Precision

The purpose is to support learning, not to claim that every word has one
universally correct difficulty score.

## Context Matters

Vocabulary is classified with attention to how it is actually used.

## Frequency Matters, But Is Not Everything

A rare word is not automatically difficult, and a common word can have
complex secondary meanings.

## Register Matters

Formal, academic, literary, technical, and archaic vocabulary may require
greater contextual knowledge.

## Meaning Matters More Than Appearance

A long word is not automatically difficult.

A short word can have extremely complex semantic or idiomatic behavior.

## CEFR Remains Separate

Vocabulary Vault difficulty labels should never be presented as replacements
for official CEFR proficiency levels.

---

# 21. Classification Summary

The complete model can be summarized as:

```text
                         VOCABULARY
                              │
             ┌────────────────┴────────────────┐
             │                                 │
             ▼                                 ▼
     DIFFICULTY SYSTEM                    CEFR REFERENCE
             │                                 │
     ┌───────┼────────┐              ┌─────────┼─────────┐
     │       │        │              │         │         │
    Easy   Medium    Hard          A1/A2     B1/B2     C1/C2
                      │
                      ▼
               Shashi Tharoor
                      │
                      ▼
              Rare / Erudite /
               Literary Vocabulary

       Additional project-specific designation:
                Celestial Pinnacle
```

In practical terms:

| System | Levels | Purpose |
|---|---|---|
| Vocabulary Vault Difficulty | Easy, Medium, Hard, Shashi Tharoor | Practical learning difficulty |
| CEFR | A1, A2, B1, B2, C1, C2 | Language-proficiency reference |
| Celestial Pinnacle | Custom designation | Exceptional vocabulary classification |
| Tags | Context-dependent | Domain, register, topic, and usage classification |

---

## Visual References

### Vocabulary Vault Difficulty Levels

![Vocabulary Vault Difficulty Levels](screenshots/difficulty-levels.png)

### CEFR Reference Levels

![Vocabulary Vault CEFR Levels](screenshots/cefr-levels.png)

---

## Related Documentation

- [System Architecture](ARCHITECTURE.md)
- [Anki Flashcards](ANKI-FLASHCARDS.md)
- [Vocabulary Vault — Google Sheets](https://docs.google.com/spreadsheets/d/14Ag_rNUwVP-BIjj0KJyLUjOb-VFecCvsH6yBcZWnOAs/edit?gid=584521556#gid=584521556)
- [Vocabulary Submission Form](https://docs.google.com/forms/d/e/1FAIpQLSeurdy8PW2JJQ8Qgj77r1_EF578bXiGnSthQSRPRaypi5BNMQ/viewform?usp=header)
- [Original Notion Version](https://vocabulary-english.notion.site/English-Vocabulary-21ce0aa0c4d380b7b73af79235b5016c)
- [AnkiWeb — Somesh Diwan](https://ankiweb.net/shared/by-author/1443764638)

---

## Important Note

Vocabulary Vault's difficulty labels, CEFR references, and custom
designations are intended primarily for vocabulary organization and
learning.

CEFR officially uses the proficiency levels **A1, A2, B1, B2, C1, and C2**.

**Easy, Medium, Hard, Shashi Tharoor, and Celestial Pinnacle are Vocabulary
Vault classifications and should not be interpreted as official CEFR
proficiency levels.**

---

<p align="center">
  <strong>Vocabulary Vault</strong><br>
  Build • Learn • Retain
</p>