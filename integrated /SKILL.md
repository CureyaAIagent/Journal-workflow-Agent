# 🧠 MASTER SKILL CONTROLLER

## ROLE
Route tasks. Control order. No execution.

---

## RULE 0: LOAD REAL SKILLS (MANDATORY)

Each task MUST load its actual SKILL.md file.

FORMAT:

task:
  module: <name>
  path: <github_path_to_SKILL.md>

---

## RULE 1: ALWAYS FOLLOW ORDER (NO RANDOM CALLS)

### PHASE 1 → VALIDATE (MUST FIRST)

plagiarism_check:
  module: Turnitin 2.26 Advanced Plagiarism Detection
  path: claude-academic-humanizer-skills/turnitin-2026-advanced-plagiarism-detection-system/SKILL.md

ai_detection:
  module: AI Content Detection Systems
  path: claude-academic-humanizer-skills/ai-content-detection/SKILL.md

citation_map:
  module: Reference Reconciliation Engine
  path: claude-academic-humanizer-skills/reference-reconciliation-engine/SKILL.md

doi_check:
  module: DOI Reference Validator
  path: claude-academic-humanizer-skills/doi_reference_validator/SKILL.md

integrity_check:
  module: Integrity Analyzer
  path: claude-academic-humanizer-skills/plagiarism-reference-integrity-analyzer/SKILL.md

---

### PHASE 2 → FIX CORE PROBLEMS

plagiarism_fix:
  module: Turnitin 2.26 Advanced Plagiarism Detection
  path: claude-academic-humanizer-skills/turnitin-2026-advanced-plagiarism-detection-system/SKILL.md

ai_humanize:
  module: AI Writing Humanizer + Linguistic Variation Engine
  path: claude-academic-humanizer-skills/ai-writing-humanizer/SKILL.md
  path: claude-academic-humanizer-skills/linguistic-variation-engine/SKILL.md

citation_fix:
  module: Reference Reconciliation Engine
  path: claude-academic-humanizer-skills/reference-reconciliation-engine/SKILL.md

evidence_add:
  module: Evidence Citation Enhancer
  path: claude-academic-humanizer-skills/evidence-citation-enhancer/SKILL.md

---

### PHASE 3 → SCIENCE QUALITY

critical_analysis:
  module: Academic Paper Critical Analysis Toolkit
  path: claude-academic-humanizer-skills/academic-paper-critical-analysis-toolkit/SKILL.md

stats_check:
  module: Statistical Validation Engine
  path: claude-academic-humanizer-skills/statistical-validation-engine/SKILL.md

---

### PHASE 4 → OPTIMIZE IMPACT

citation_boost:
  module: Citation Impact Optimizer
  path: claude-academic-humanizer-skills/citation-impact-optimizer/SKILL.md

manuscript_refine:
  module: Comprehensive Academic Manuscript
  path: claude-academic-humanizer-skills/comprehensive-academic-manuscript/SKILL.md

---

### PHASE 5 → VISUALS + OUTPUT

diagrams:
  module: Research Diagram Toolkit
  path: claude-academic-humanizer-skills/research-diagram-toolkit/SKILL.md

final_format:
  module: Comprehensive Academic Manuscript
  path: claude-academic-humanizer-skills/comprehensive-academic-manuscript/SKILL.md

---

## RULE 2: TRIGGERS (ONLY RUN WHEN NEEDED)

IF plagiarism >10 → run plagiarism_fix  
IF AI >10 → run ai_humanize  
IF DOI <100 → run doi_check + citation_fix  
IF missing refs → run citation_fix  
IF weak claims → run evidence_add  
IF data present → run stats_check  

---

## RULE 3: DEPENDENCIES (STRICT)

- citation_map → BEFORE doi_check  
- plagiarism_fix → BEFORE ai_humanize  
- ai_humanize → BEFORE manuscript_refine  
- ALL validation → BEFORE final_format  

---

## RULE 4: FINAL DRAFT (ONLY WHEN READY)

CONDITIONS:
- AI <10  
- Plagiarism <10  
- DOI = 100  
- Citation = 100  

THEN:
→ run manuscript_refine (FINAL)

---

## RULE 5: OUTPUT FORMAT (ALL SKILLS)

```json
{
  "status": "ok",
  "score": "...",
  "issues": [],
  "fix_applied": true
}
