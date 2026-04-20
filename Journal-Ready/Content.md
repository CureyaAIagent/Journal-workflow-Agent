# CONTENT.md — Journal Workflow (Caveman Mode)

## OBJECTIVE
Make manuscript journal-ready using:
- Excel rules (must)
- skill routing (must)
- controller loop

---

## DEPENDENCY
Needs:
- controller.md
- journal-workflow-agent/integrated/skill.md  ← (MASTER SKILL ROUTER)
- memory.md
- journal_excel_data

---

## RULE (STRICT)
ALL skills via:

→ journal-workflow-agent/integrated/skill.md

NO direct calls  
NO bypass  

Flow:
controller → skill.md → tools

---

## FAILSAFE
If no Excel:
{
 "status":"fail",
 "reason":"journal mapping required"
}

---

## INPUT
{
 "paper_id":"str",
 "manuscript_text":"str",
 "target_journal":"str",
 "instruction_prompt":"str",
 "journal_excel_data":"file"
}

---

## OUTPUT
{
 "final_manuscript":"str",
 "validation":{
  "ai":"<10",
  "plag":"<10",
  "doi":"100",
  "citation":"100",
  "format":"100"
 },
 "submission":{
  "cover_letter":"str",
  "highlights":"str",
  "graphical_abstract":"opt"
 }
}

---

## FLOW

### STEP 1 — MAP
→ read Excel  
→ save memory  

OUT:
{
 "step":"map",
 "ok":true,
 "data":{"rules":{}}
}

---

### STEP 2 — STRUCTURE
→ format manuscript  

OUT:
{
 "step":"structure",
 "ok":true,
 "data":{"manuscript":"str"}
}

---

### STEP 3 — REFERENCES
→ via journal-workflow-agent/integrated/skill.md:
 - reference_reconciliation_engine
 - doi_reference_validator

OUT:
{
 "step":"ref",
 "ok":true,
 "data":{
  "citation":92,
  "doi":95,
  "orphans":true
 }
}

---

### STEP 4 — QUALITY
→ via journal-workflow-agent/integrated/skill.md:
 - plagiarism_reference_integrity_analyzer
 - ai_content_detection_system

OUT:
{
 "step":"quality",
 "ok":true,
 "data":{
  "plag":14,
  "ai":18
 }
}

---

### STEP 5 — OPTIMIZE
→ via journal-workflow-agent/integrated/skill.md:
 - ai_humanization_engine
 - academic_language_optimizer

OUT:
{
 "step":"opt",
 "ok":true,
 "data":{"manuscript":"str"}
}

---

### STEP 6 — DIAGRAM
IF no visuals:
→ via journal-workflow-agent/integrated/skill.md:
 - research_diagram_toolkit

OUT:
{
 "step":"diagram",
 "ok":true,
 "data":{"added":true}
}

---

### STEP 7 — FINAL
Need:
- ai <10
- plag <10
- doi =100
- citation =100
- format =100

OUT:
{
 "step":"final",
 "ok":true,
 "data":{
  "ai":8,
  "plag":6,
  "doi":100,
  "citation":100,
  "format":100
 }
}

---

## LOOP (controller)
Repeat until:
ai<10 && plag<10 && doi=100 && citation=100

---

## MEMORY
Store:
- rules
- manuscript
- scores
- iteration

---

## END
{
 "status":"success",
 "ready":true
}
