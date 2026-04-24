# README DiVINE Knowledge Graph Operational Manual
## Operationalizing Digitalization Through Structured Knowledge

**Version:** 1.0  
**Date:** April 2026  
**Status:** Operational Framework  
**Audience:** Researchers, Objective Leaders, Data Stewards, and Information Architects

---

## Executive Overview

This manual establishes the operating procedures for maintaining the **DiVINE Knowledge Graph (KG)** in WebProtégé. The KG is not a repository for completed analysis—it is a **living system** for capturing, structuring, and linking the complexity of digital innovation and value transformation across our research domains.

### Purpose Statement
The DiVINE KG operationalizes our digitalization vision by:
- **Mapping complexity** through explicit entity relationships and contextual dependencies
- **Enabling logical inference** via semantic links and machine-readable properties
- **Capturing unstructured insights** from continuous research inputs (interviews, documents, workshops) into structured form
- **Supporting reproducible analysis** through consistent evidence attribution and source tracing
- **Facilitating knowledge reuse** across research teams and future phases

This manual is the authoritative guide for consistent, high-quality KG entries.

---

## Section 1: Rationale for the Knowledge Graph

### 1.1 Why a Structured Knowledge Graph?

#### The Complexity Challenge
DiVINE research generates enormous volumes of semi-structured insights:
- **Interview transcripts** (unstructured narrative)
- **Policy documents** (domain-specific language, implicit relationships)
- **Organizational records** (fragmented across systems and stakeholders)
- **Stakeholder feedback** (varied perspectives on the same phenomenon)

**Traditional databases** organize data in rows and columns. They struggle with:
- **Implicit relationships** ("This barrier is influenced by that regulation" – which field captures this link?)
- **Polysemy** ("Digital" means different things to different stakeholders)
- **Tractability for inference** (joins across tables require SQL; capturing logical rules requires coding)

#### The Knowledge Graph Advantage
A Knowledge Graph represents knowledge as **entities (nodes) and relationships (edges)**. This enables:

| Challenge | Traditional DB | Knowledge Graph |
|-----------|---|---|
| **Representing N:N relationships** | Requires junction tables | Native support |
| **Capturing implicit context** | Lost or must be normalized into separate fields | Explicit semantic links (triples) |
| **Cross-domain reasoning** | Difficult; requires pre-defined schema | Natural; relationships are first-class citizens |
| **Unstructured → Structured** | Requires manual categorization | Supports gradual formalization via linked annotation |
| **Supporting SPARQL queries** | Not applicable | Core capability |
| **Machine-learning readiness** | Limited; poor feature representation | Direct; graph embeddings + labeled edges |

### 1.2 Mapping Complexity: The Three Layers

Our KG operates across three **layers of knowledge**:

#### Layer 1: **The Problem Space** (What we observe)
- **ContextualFactors**: Conditions, constraints, and preconditions in the operating environment
- **Barriers**: Obstacles and inhibitors to digital value transformation (Subclasses A–F)
- **Pillars**: Strategic domains or capability areas within digitalization
- **Stakeholders**: Actors whose perspectives or actions shape the system

*Example triple:*  
`A01_Legacy_Fleet → isA_ContextualFactor → Digital_Readiness_Gap`

#### Layer 2: **The Response Space** (What we propose)
- **Measures**: Specific interventions, policies, or actions designed to address barriers
- **MeasureClusters**: Thematic groupings of related measures (for synthesis and reporting)
- **InformationNeeds**: Defined information gaps (IN1–IN7) requiring future research or data collection

*Example triple:*  
`Measure_MOD_001 → addresses → A01_Legacy_Fleet`

#### Layer 3: **The Evidence and Metadata Layer** (How we know)
- **InformationSources**: Documentary evidence, interview data, workshop outputs, or policy references
- **GlossaryTerms**: Controlled vocabulary for consistent terminology across the KG
- **MaturityLevels**: Qualitative assessment of confidence or development stage (Emerging, Established, Mature, Advanced)

*Example triple:*  
`A01_Legacy_Fleet → isDefinedBySource → Interview_SWeden_Dairy_2024_S03 → hasMaturityLevel → Established`

### 1.3 Why Relationships Are Central

In traditional data models, relationships are *implicit*:
- A spreadsheet links a "Barrier Name" to a "Pillar ID" via a hidden database foreign key.
- The semantic meaning ("This barrier *impedes* that pillar") is embedded in the analyst's interpretation.

In our KG, relationships are **explicit and machine-readable**:
- `A01_Legacy_Fleet` has a property `impedes` pointing to `P02_Automation`
- `Measure_MOD_001` has a property `supports` pointing to `P02_Automation`
- A SPARQL query can then reason: *"Which measures indirectly support barriers that impede P02_Automation?"*

This **explicitness** enables:
- **Automated consistency checks** (Is this barrier linked to any pillar? Any measure?)
- **Bidirectional navigation** (Forward: barriers → measures; backward: measures → affected barriers)
- **Aggregation at scale** (Summarize all measures addressing a cluster of related barriers)

### 1.4 Handling Unstructured Inputs

DiVINE generates continuous, ongoing research outputs. The KG accommodates:

**Incremental Formalization Workflow:**
1. **Capture Phase**: Raw insight from interview/document → `rdfs:comment` (informal note)
2. **Structuring Phase**: Insight refined → `hasDescription` (formal text) + linked to existing concepts
3. **Linking Phase**: Insight connected to barriers, measures, pillars → explicit properties added
4. **Enrichment Phase**: Verbatim evidence extracted → `hasExtract` (with source and citation)

*Example evolution:*
