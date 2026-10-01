# Vocabulary Vault — System Architecture

## Overview

**Vocabulary Vault** is a structured English vocabulary learning and
management system built around Google Sheets, Google Forms, and a private
Google Apps Script automation layer.

The system is designed around one core architectural principle:

> **Maintain a single source of truth and derive specialized learning views from it.**

Vocabulary can be entered manually or submitted through a Google Form.
The automation layer validates and processes supported entries, maintains
system metadata, records operational events, and keeps derived vocabulary
views synchronized with the primary dataset.

The public repository documents the architecture and behavior of the system.
The complete production Apps Script implementation, internal formulas,
validation rules, and commercial Anki collection remain private.

---

## Live Project

| Resource | Purpose |
|---|---|
| [Vocabulary Vault — Google Sheets](https://docs.google.com/spreadsheets/d/14Ag_rNUwVP-BIjj0KJyLUjOb-VFecCvsH6yBcZWnOAs/edit?gid=584521556#gid=584521556) | Main vocabulary database and generated learning views |
| [Vocabulary Submission Form](https://docs.google.com/forms/d/e/1FAIpQLSeurdy8PW2JJQ8Qgj77r1_EF578bXiGnSthQSRPRaypi5BNMQ/viewform?usp=header) | Structured vocabulary submission workflow |
| [Original Notion Version](https://vocabulary-english.notion.site/English-Vocabulary-21ce0aa0c4d380b7b73af79235b5016c) | Earlier version of the vocabulary project |
| [AnkiWeb — Somesh Diwan](https://ankiweb.net/shared/by-author/1443764638) | Public Anki resources and shared decks |

---

## Architecture at a Glance

```text
┌───────────────────────────────────────────────────────────────┐
│                         INPUT LAYER                           │
│                                                               │
│       Manual Entry                    Google Form             │
└───────────────┬───────────────────────────┬───────────────────┘
                │                           │
                └─────────────┬─────────────┘
                              │
                              ▼
┌───────────────────────────────────────────────────────────────┐
│                     AUTOMATION LAYER                          │
│                                                               │
│   Normalization  •  Validation  •  Duplicate Protection      │
│   Metadata       •  Audit Logging •  Error Handling          │
│   View Generation              •  Concurrency Protection      │
└───────────────────────────────┬───────────────────────────────┘
                                │
                                ▼
┌───────────────────────────────────────────────────────────────┐
│                       DATA LAYER                              │
│                                                               │
│                     VOCABULARY VAULT                          │
│                      Source of Truth                          │
└───────────────────────────────┬───────────────────────────────┘
                                │
              ┌─────────────────┼─────────────────┐
              │                 │                 │
              ▼                 ▼                 ▼
       ┌────────────┐     ┌────────────┐    ┌────────────┐
       │   A To Z   │     │ Only Words │    │ Audit Log  │
       │   View     │     │    View    │    │            │
       └──────┬─────┘     └──────┬─────┘    └────────────┘
              │                  │
              └────────┬─────────┘
                       │
                       ▼
┌───────────────────────────────────────────────────────────────┐
│                      LEARNING LAYER                           │
│                                                               │
│       Browsing  •  Revision  •  Pronunciation  •  Recall      │
│                              │                                │
│                              ▼                                │
│                     Anki Flashcards                           │
│                    Separate Resource                          │
└───────────────────────────────────────────────────────────────┘
```

---

## 1. Input Layer

Vocabulary Vault supports two primary entry paths.

### Manual Entry

Vocabulary can be entered directly into the primary Google Sheets
database.

A supported manual entry passes through the automation layer before it
becomes part of the maintained vocabulary collection.

```text
Manual Entry
     │
     ▼
Normalize
     │
     ▼
Validate
     │
     ▼
Duplicate Check
     │
     ▼
Metadata Processing
     │
     ▼
Vocabulary Vault
```

This workflow is useful when vocabulary is being researched or added while
working directly inside the spreadsheet.

### Google Form Entry

The project also provides a dedicated Google Form for structured
vocabulary submission.

**Submission Form:**  
[Open Vocabulary Submission Form](https://docs.google.com/forms/d/e/1FAIpQLSeurdy8PW2JJQ8Qgj77r1_EF578bXiGnSthQSRPRaypi5BNMQ/viewform?usp=header)

The form provides a controlled input interface while the automation layer
handles integration with the main vocabulary database.

```text
Google Form
     │
     ▼
Form Submission
     │
     ▼
Automation Layer
     │
     ├── Normalize
     ├── Validate
     ├── Check Duplicate
     └── Process Metadata
     │
     ▼
Vocabulary Vault
```

The production form mapping and processing implementation are intentionally
not published.

---

## 2. Automation Layer

Google Apps Script provides the automation layer between input sources,
the primary database, generated views, and operational logging.

Its responsibilities can be grouped into six areas.

| Responsibility | Purpose |
|---|---|
| Input processing | Normalizes supported vocabulary input |
| Validation | Prevents malformed or unsupported entries |
| Duplicate protection | Reduces duplicate vocabulary records |
| Metadata management | Maintains system-controlled entry information |
| Audit logging | Records significant automation events |
| View generation | Synchronizes derived learning views |

Additional safeguards handle errors and overlapping automation operations.

### Processing Pipeline

```text
Incoming Vocabulary
        │
        ▼
┌───────────────────┐
│    Normalize      │
└─────────┬─────────┘
          ▼
┌───────────────────┐
│     Validate      │
└─────────┬─────────┘
          ▼
┌───────────────────┐
│ Duplicate Guard   │
└─────────┬─────────┘
          ▼
┌───────────────────┐
│     Metadata      │
└─────────┬─────────┘
          ▼
┌───────────────────┐
│ Database Commit   │
└─────────┬─────────┘
          │
          ├──────────────► Audit Log
          │
          ▼
┌───────────────────┐
│ Refresh Views     │
└───────────────────┘
```

The repository intentionally documents this pipeline at an architectural
level rather than publishing its production algorithms.

---

## 3. Primary Data Layer

The **Vocabulary Vault** sheet is the authoritative vocabulary database.

**Google Sheets:**  
[Open Vocabulary Vault](https://docs.google.com/spreadsheets/d/14Ag_rNUwVP-BIjj0KJyLUjOb-VFecCvsH6yBcZWnOAs/edit?gid=584521556#gid=584521556)

A vocabulary record can contain learning information such as:

- Word or phrase
- Meaning in English
- Example usage
- Synonyms
- Antonyms
- Part of speech
- Tags
- Difficulty classification
- Meaning in Hindi
- Pronunciation access
- System metadata

The exact internal field contract is intentionally not reproduced in this
public architecture document.

### Source of Truth

The primary database owns the vocabulary data.

```text
                    Vocabulary Vault
                     SOURCE OF TRUTH
                           │
                 ┌─────────┴─────────┐
                 │                   │
                 ▼                   ▼
              A To Z             Only Words
           Derived View          Derived View
```

The generated sheets are **views of the main dataset**, not independently
maintained vocabulary databases.

This avoids unnecessary duplication and reduces synchronization problems.

---

## 4. Data Model

Vocabulary Vault conceptually separates user-facing learning information
from system-managed information.

```text
Vocabulary Record
│
├── Learning Data
│   ├── Word / Phrase
│   ├── English Meaning
│   ├── Example Usage
│   ├── Synonyms
│   ├── Antonyms
│   ├── Part of Speech
│   ├── Tags
│   ├── Difficulty
│   └── Hindi Meaning
│
└── System Data
    ├── Attribution
    ├── Creation Information
    ├── Internal Identity
    └── Operational Metadata
```

This separation allows the database to remain useful to learners while also
supporting reliable automation.

---

## 5. Metadata and Entry Identity

The system maintains selected metadata automatically.

Metadata supports:

- Entry attribution
- Creation tracking
- Internal identification
- Auditability
- Synchronization
- Future revision workflows

A key design decision is to separate visible ordering from permanent
identity.

```text
Display Number
      ≠
Internal Entry Identity
```

A visible row or serial number may change as data is reordered or maintained.
A system identity should remain logically associated with the underlying
entry.

The production identity-generation mechanism is private.

---

## 6. Generated Views

The system creates specialized views from the primary Vocabulary Vault
dataset.

### A To Z

The **A To Z** sheet provides an alphabetically organized vocabulary view.

Its purpose is to make the collection easier to browse and review.

```text
Vocabulary Vault
       │
       ▼
Read Current Data
       │
       ▼
Select Relevant Fields
       │
       ▼
Alphabetical Organization
       │
       ▼
Presentation Processing
       │
       ▼
A To Z
```

The view can provide:

- Word or phrase
- English meaning
- Example usage
- Synonyms
- Antonyms
- Pronunciation access

Sorting rules, formatting configuration, dimensions, colors, and generation
logic are part of the private production implementation.

### Only Words

The **Only Words** sheet provides a focused learning-oriented representation
of the vocabulary collection.

```text
Vocabulary Vault
       │
       ▼
Select Learning Data
       │
       ▼
Transform
       │
       ▼
Apply Presentation
       │
       ▼
Only Words
```

The view can contain selected information such as:

- Word or phrase
- English meaning
- Example usage
- Synonyms
- Antonyms
- Hindi meaning
- Pronunciation access

Both generated views depend on the Vocabulary Vault rather than maintaining
separate copies of the vocabulary database.

---

## 7. Classification Layer

Vocabulary Vault uses two complementary classification concepts.

### Difficulty

The project-specific difficulty system contains four principal categories:

| Classification | General Purpose |
|---|---|
| Easy | Common and relatively accessible vocabulary |
| Medium | Vocabulary with moderate linguistic depth |
| Hard | Advanced, academic, literary, or complex vocabulary |
| Shashi Tharoor | Rare, erudite, ornate, or exceptionally sophisticated vocabulary |

Difficulty can also influence how entries are presented visually in
generated views.

### CEFR References

Vocabulary entries can additionally use CEFR references:

```text
A1 → Beginner
A2 → Elementary
B1 → Intermediate
B2 → Upper-Intermediate
C1 → Advanced
C2 → Mastery
```

The custom difficulty system and CEFR references serve different purposes:

```text
Custom Difficulty
        +
CEFR Reference
        │
        ▼
Vocabulary Classification
```

CEFR references in Vocabulary Vault are organizational learning references,
not formal assessments of an individual learner's proficiency.

See the complete classification documentation:

[Vocabulary Classification System](VOCABULARY-LEVELS.md)

---

## 8. Pronunciation Layer

Pronunciation is treated as part of the learning experience rather than as
a duplicate audio database.

Supported vocabulary views provide access to British-English pronunciation
references.

```text
Vocabulary Entry
       │
       ▼
Pronunciation Access
       │
       ▼
British-English Reference
       │
       ▼
Listen / Observe / Repeat
```

The production URL construction and spreadsheet formula implementation are
intentionally not published.

---

## 9. Audit and Observability

The system contains an audit layer for recording important automation
activity.

Typical event categories include:

```text
Entry Processing
Validation Events
Duplicate Rejections
Metadata Operations
View Regeneration
System Errors
Automation Events
```

The conceptual flow is:

```text
Automation Event
       │
       ▼
   Audit Layer
       │
       ▼
Event + Context + Time
       │
       ▼
    Audit Log
```

The audit log helps with debugging, maintenance, and understanding how the
system changes over time.

The complete event schema remains part of the private implementation.

---

## 10. Reliability

Spreadsheet automation can encounter overlapping operations, partial input,
or runtime errors.

The production architecture therefore includes reliability controls around
critical operations.

### Concurrency Protection

```text
Automation Request
        │
        ▼
Concurrency Guard
        │
     ┌──┴───┐
     │      │
Available  Busy
     │      │
     ▼      ▼
 Execute   Handle Safely
```

This reduces the possibility of multiple regeneration operations interfering
with one another.

### Error Handling

```text
Operation
    │
    ▼
 Execute
    │
 ┌──┴─────┐
 │        │
Success  Failure
 │        │
 ▼        ▼
Continue  Record Error
              │
              ▼
           Audit Log
```

Exact locking intervals, exception behavior, and recovery implementation are
private.

---

## 11. Synchronization Model

Generated views are refreshed after supported changes to the source data.

```text
Vocabulary Change
        │
        ▼
Vocabulary Vault Updated
        │
        ▼
Regeneration Requested
        │
     ┌──┴─────────────┐
     │                │
     ▼                ▼
  A To Z          Only Words
     │                │
     └────────┬───────┘
              ▼
       Synchronized Views
```

This model allows the main database to evolve while derived views remain
consistent with it.

---

## 12. Presentation Layer

The presentation layer transforms structured vocabulary data into views that
are easier to read and study.

It handles concepts such as:

- Typography
- Structured headers
- Content wrapping
- Difficulty indicators
- Bilingual presentation
- Learning-oriented spacing
- Pronunciation access
- Generated-view consistency

The conceptual separation is:

```text
Raw Structured Data
        │
        ▼
Presentation Rules
        │
        ▼
Learning-Oriented Interface
```

Exact visual configuration is intentionally left out of the public
implementation.

---

## 13. Learning Layer

Vocabulary Vault is not intended to function only as a database.

The broader learning workflow is:

```text
Collect
   │
   ▼
Understand
   │
   ▼
Classify
   │
   ▼
Review
   │
   ▼
Recall
   │
   ▼
Retain
```

Google Sheets provides structured vocabulary management.

Generated views provide browsing and revision.

Pronunciation references provide spoken-language support.

Anki provides the spaced-repetition layer.

---

## 14. Anki Integration

The Anki workflow is downstream from the vocabulary database.

```text
Vocabulary Vault
       │
       ▼
Structured Vocabulary
       │
       ▼
Flashcard Transformation
       │
       ▼
Anki
       │
       ▼
Active Recall
       │
       ▼
Spaced Repetition
       │
       ▼
Long-Term Retention
```

Public Anki resources can be viewed here:

[Somesh Diwan — AnkiWeb](https://ankiweb.net/shared/by-author/1443764638)

The complete Vocabulary Vault Anki collection is maintained separately and
is **not included in this public repository**.

See:

[Anki Flashcards](ANKI-FLASHCARDS.md)

---

## 15. Project Evolution

Vocabulary Vault originally began as a structured Notion vocabulary
database.

[View the original Notion version](https://vocabulary-english.notion.site/English-Vocabulary-21ce0aa0c4d380b7b73af79235b5016c)

As the collection expanded, the architecture evolved to support more
structured automation, validation, metadata, generated views, logging, and
learning workflows.

```text
Notion
   │
   ▼
Structured Vocabulary Collection
   │
   ▼
Google Sheets
   │
   ▼
Google Apps Script Automation
   │
   ▼
Vocabulary Vault
   │
   ├──────────────┐
   ▼              ▼
Generated      Google Form
Views          Workflow
   │
   ▼
Anki / Spaced Repetition
```

The Notion version therefore represents an earlier stage of the project,
while the Google Sheets architecture represents the current system.

---

## 16. Design Principles

### Single Source of Truth

The main Vocabulary Vault is the authoritative dataset.

```text
One Primary Dataset
        │
        ├────► A To Z
        └────► Only Words
```

### Separation of Concerns

Each component has a focused responsibility.

| Component | Responsibility |
|---|---|
| Google Form | Structured input |
| Vocabulary Vault | Primary data |
| Apps Script | Automation |
| A To Z | Alphabetical browsing |
| Only Words | Focused learning view |
| Audit Log | Operational history |
| Anki | Spaced repetition |

### Automation Over Repetition

Repetitive data-management operations are automated where appropriate.

### Derived Views Over Duplicate Databases

Generated views depend on the primary dataset instead of becoming separate
sources of truth.

### Learning First

Technical automation exists to improve the vocabulary-learning workflow,
not simply to add complexity.

---

## 17. Public Architecture vs. Private Implementation

This repository is intended to demonstrate the project architecture without
publishing the complete production implementation.

### Publicly Documented

```text
Project architecture
System responsibilities
Data flow
Feature overview
Classification model
Screenshots
High-level automation structure
Anki previews
Project evolution
```

### Maintained Privately

```text
Complete production Apps Script
Exact validation rules
Internal configuration
Exact field mappings
Production formulas
Duplicate-detection implementation
Metadata-generation implementation
Regeneration algorithms
Internal presentation configuration
Concurrency configuration
Production Anki deck files
Complete commercial flashcard collection
```

The public architecture therefore explains **what the system does and how
its components interact**, while the production repository retains the
implementation details required to reproduce the complete system.

---

## 18. Public Apps Script Representation

The repository contains only a high-level representation of the Apps Script
architecture.

```text
apps-script/
└── Architecture.gs
```

The public file documents responsibilities such as:

```text
Configuration
      │
      ├── Audit Layer
      ├── Metadata Layer
      ├── Manual Entry Processing
      ├── Form Processing
      ├── A To Z Generation
      ├── Only Words Generation
      └── Presentation Helpers
```

Function bodies containing production algorithms are intentionally omitted.

The file exists for architectural documentation rather than direct
deployment.

---

## 19. Repository Structure

```text
English-Vocabulary/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── apps-script/
│   └── Architecture.gs
│
├── docs/
│   ├── ARCHITECTURE.md
│   ├── VOCABULARY-LEVELS.md
│   ├── ANKI-FLASHCARDS.md
│   │
│   └── screenshots/
│       ├── vocabulary-vault.png
│       ├── form-responses.png
│       ├── a-to-z.png
│       ├── only-words.png
│       ├── difficulty-levels.png
│       ├── cefr-levels.png
│       ├── anki-basic-front.jpg
│       ├── anki-basic-back.jpg
│       ├── anki-vault-front.jpg
│       └── anki-vault-back.jpg
│
└── assets/
    ├── vocabulary-vault-logo.png
    └── vip.gif
```

---

## 20. Complete System Flow

The overall architecture can be summarized as:

```text
                         INPUT
                           │
              ┌────────────┴────────────┐
              │                         │
              ▼                         ▼
        Manual Entry               Google Form
              │                         │
              └────────────┬────────────┘
                           ▼
                     AUTOMATION
                           │
       ┌───────────────────┼───────────────────┐
       │                   │                   │
       ▼                   ▼                   ▼
  Validation          Metadata            Audit
       │                   │                   │
       └───────────────────┼───────────────────┘
                           ▼
                   VOCABULARY VAULT
                    Source of Truth
                           │
              ┌────────────┴────────────┐
              │                         │
              ▼                         ▼
           A To Z                  Only Words
              │                         │
              └────────────┬────────────┘
                           ▼
                    LEARNING / REVIEW
                           │
                ┌──────────┴──────────┐
                │                     │
                ▼                     ▼
         Pronunciation               Anki
                                   Flashcards
                                      │
                                      ▼
                              Spaced Repetition
                                      │
                                      ▼
                              Long-Term Retention
```

---

## Technology Stack

| Layer | Technology |
|---|---|
| Primary datastore | Google Sheets |
| Structured input | Google Forms |
| Automation | Google Apps Script |
| Auditability | Spreadsheet-based event logging |
| Vocabulary views | Generated Google Sheets views |
| Pronunciation | British-English pronunciation references |
| Flashcards | Anki |
| Documentation | Markdown / GitHub |
| Earlier prototype | Notion |

---

## Production Implementation

The complete production implementation is not distributed through this
repository.

This includes the production Google Apps Script, internal configuration,
exact formulas, validation algorithms, metadata strategy, generated-view
implementation, and complete Anki collection.

The public repository is intended to document the engineering architecture,
showcase the project, provide selected public resources, and offer a clear
overview of how Vocabulary Vault operates.

---

## Related Documentation

- [Vocabulary Classification System](VOCABULARY-LEVELS.md)
- [Anki Flashcards](ANKI-FLASHCARDS.md)
- [Public Apps Script Architecture](../apps-script/Architecture.gs)
- [Vocabulary Submission Form](https://docs.google.com/forms/d/e/1FAIpQLSeurdy8PW2JJQ8Qgj77r1_EF578bXiGnSthQSRPRaypi5BNMQ/viewform?usp=header)
- [Vocabulary Vault — Google Sheets](https://docs.google.com/spreadsheets/d/14Ag_rNUwVP-BIjj0KJyLUjOb-VFecCvsH6yBcZWnOAs/edit?gid=584521556#gid=584521556)
- [Original Notion Version](https://vocabulary-english.notion.site/English-Vocabulary-21ce0aa0c4d380b7b73af79235b5016c)
- [AnkiWeb Profile](https://ankiweb.net/shared/by-author/1443764638)

---

## Contact and Corrections

Vocabulary Vault is continuously maintained.

If you notice an incorrect meaning, example, synonym, antonym, Hindi
translation, classification, grammatical detail, or another vocabulary
issue, you can open an issue in the GitHub repository or contact:

**Somesh Diwan**  
**Email:** someshdiwan@icloud.com

For information about the complete paid Anki flashcard collection, see
[Anki Flashcards](ANKI-FLASHCARDS.md).

---

<p align="center">
  <strong>Vocabulary Vault</strong><br>
  Build • Learn • Retain
</p>
