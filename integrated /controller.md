# 🧠 CONTROLLER (EXECUTION ENGINE)

## ROLE
Run system. Control loop. Stop only when ready.

---

## INPUTS REQUIRED

- manuscript  
- paper_id  
- journal_id  
- excel_sheet (Journal Workflow DB)  
- prompt (optional)

---

## SYSTEM FILES (MANDATORY)

- content.md → workflow steps  
- integrated/skill.md → skill routing  
- memory.md → state tracking + iteration memory  
- Excel → journal rules  

---

## 🧠 MEMORY USAGE (CRITICAL)

memory.md stores:

- previous scores (AI, plagiarism, DOI, citation)  
- issues detected in last cycle  
- fixes already applied  
- failed attempts  
- iteration count  

---

## EXECUTION FLOW

STEP 1 → LOAD DATA
- read manuscript  
- read paper_id  
- fetch journal_id from Excel  
- load journal rules  

STEP 2 → LOAD MEMORY
- check if previous run exists  
- load last cycle data from memory.md  
- avoid repeating same fixes  

---

STEP 3 → START PIPELINE

CALL → content.md  

content.md:
→ maps journal requirements  
→ sends tasks to skill.md  
→ skills execute via MCP  

---

## 🔁 ITERATION LOOP (MANDATORY)

SET:
cycle = memory.cycle OR 1  
max_cycle = 10  

WHILE TRUE:

    RUN → content.md → skill.md → tools  

    GET SCORES:
    - ai_score  
    - plagiarism_score  
    - doi_score  
    - citation_score  

    STORE in memory.md:
    - current scores  
    - issues  
    - fixes applied  

---

## ✅ TERMINATION CHECK

IF:

- ai_score < 10  
- plagiarism_score < 10  
- doi_score == 100  
- citation_score == 100  

THEN:

→ SAVE final state in memory.md  
→ BREAK LOOP  

---

## ❌ IF NOT SATISFIED

→ cycle = cycle + 1  
→ update memory.md  

IF cycle > max_cycle:
    → STOP  
    → FLAG: "manual review required"  

ELSE:
    → RE-RUN pipeline using memory context  

---

## 🧾 FINALIZATION

AFTER SUCCESS:

- trigger final_format (via skill.md)  

GENERATE:
- final manuscript  
- figures plan  
- tables document  
- cover letter  

STORE:
- final outputs in memory.md  

---

## 🚨 STRICT RULES

- do NOT skip memory usage  
- do NOT repeat same fixes blindly  
- do NOT generate early output  
- do NOT bypass skill.md  
- do NOT ignore previous cycles  

---

## 🧠 SYSTEM LOGIC (CAVEMAN)

LOAD → REMEMBER → RUN  

CHECK → SAVE → FIX  

LOOP until GOOD  

GOOD → FINAL  

DONE = submission ready  
