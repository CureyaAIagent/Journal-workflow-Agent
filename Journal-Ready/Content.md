# CONTENT.md — Journal Workflow (Caveman Mode)

## OBJECTIVE
Make manuscript journal-ready using:
- given prompt + manuscript
- extract paper + journal id
- Excel rules (must)
- skill routing (must)
- controller loop

---

## DEPENDENCY
Needs:
- controller.md
- journal-workflow-agent/integrated/skill.md
- memory.md
- journal_excel_data

---

## RULE (STRICT)
ALL skills via:
→ journal-workflow-agent/integrated/skill.md

Flow:
controller → skill.md → tools

NO direct calls

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
 "manuscript_text":"str",
 "instruction_prompt":"str",
 "journal_excel_data":"file"
}

---

## OUTPUT
{
 "paper_id":"str",
 "journal_id":"str",
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

### STEP 0 — EXTRACT
→ from prompt + manuscript:

- paper_id
- journal_id

→ match journal_id in Excel  
→ extract journal_rules  

→ save memory  

OUT:
{
 "step":"extract",
 "ok":true,
 "data":{
  "paper_id":"str",
  "journal_id":"str",
  "rules":{}
 }
}

---

### STEP 1 — STRUCTURE
→ apply journal_rules  
→ format manuscript  

OUT:
{
 "step":"structure",
 "ok":true,
 "data":{"manuscript":"str"}
}

---

### STEP 2 — REFERENCES
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

### STEP 3 — QUALITY
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

### STEP 4 — OPTIMIZE
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

### STEP 5 — DIAGRAM
IF no visuals:
→ via skill.md:
 - research_diagram_toolkit

OUT:
{
 "step":"diagram",
 "ok":true,
 "data":{"added":true}
}

---

### STEP 6 — FINAL CHECK
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
- paper_id
- journal_id
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
