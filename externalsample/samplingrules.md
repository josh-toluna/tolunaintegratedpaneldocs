---
title: Sampling Rules
has_children: false
nav_order: 4
parent: External Sample Offering
---

## Sampling Rules


External Sample Partners must comply with Toluna's samplingrules. To be sampled for a Quota, each member must:
 - Be targted for only 1 Quota per Survey
 - Match ALL Layers in the Quota
 - Match ONE of the SubQuotas
 - Match at least one "AnswerID" (SubQuotaAttribute) per SubQuota with the single QuestionID
 - Match at least one "AnswerID" (SubQuotaAttribute) per QuestionID in the SubQuota with multiple QuestionIDs
 
These rules can be consolidated into simple boolean conditions:
 - Quotas are "OR" conditions
 - Layers are "AND" conditions
 - SubQuotas are "OR" conditions
 - AnswerIDs are "OR" conditions
 - Within a SubQuota
   - "OR" for the same QuestionID
   - "AND" for multiple QuestionIDs
   
### Sampling Examples

Click each button to open a new page with the JSON file for the specific example.

#### [Quota with Multiple Layers](){: .btn }

#### [Quota with Single Layer, SubQuota with Multiple QuestionIDs](){: .btn }

#### [Quota with Single Layer, SubQuota with Single QuestionID](){: .btn }