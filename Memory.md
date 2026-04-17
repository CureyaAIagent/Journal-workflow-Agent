# 🧠 MEMORY SYSTEM:
CUREEYA Multi-Journal Research Workflow (Excel-Integrated Intelligence System)

---

# 🔗 SECTION 1: EXTERNAL MEMORY SOURCE (EXCEL DATABASE)

## 📊 Primary Data Source:
Excel / Google Sheet: Journal Workflow Database

---

## 📄 SHEET STRUCTURE OVERVIEW:

### 1. Journal_Master (Control Layer)
- Journal ID → Primary Key
- Journal Name
- Sheet Name (Mapping to journal-specific requirement sheet)
- Publisher
- URL

---

### 2. Paper_Tracker (Execution Layer)
- Paper ID → Primary Key
- Journal ID → Foreign Key
- Article Type
- Status
- Iteration Count
- AI %
- Plagiarism %
- DOI %
- Citation %
- Desk Rejection Risk %

---

### 3. 📌 Journal-Specific Requirement Sheets (MANDATORY)

👉 For EACH Journal ID (J01, J02, J03...),  
a **separate sheet is created** to store detailed journal guidelines for paper amendment.

---

## 🗂️ Sheet Naming Convention:

| Journal ID | Sheet Name |
|------------|------------|
| J01 | Vision_J01 |
| J02 | AI_Society_J02 |
| J03 | BPR_J03 |

---

## 📄 PURPOSE OF EACH JOURNAL SHEET:

Each sheet contains:
- Structure requirements  
- Formatting rules  
- Referencing style  
- Language rules  
- Figures & tables guidelines  
- Ethical & submission requirements  

---

## 📌 STANDARD FORMAT INSIDE EACH JOURNAL SHEET:

| Category | Parameter | Requirement |

Example:
- Abstract | Word Count | 150–250  
- Keywords | Count | 4–6  
- Referencing | Style | APA  
- Figures | Placement | End of document  

---

## 🚫 CONSTRAINT:

- DO NOT mix journal rules  
- DO NOT assume generic guidelines  
- ALWAYS follow journal-specific sheet  

---

# 🧠 SECTION 2: DATA RETRIEVAL LOGIC

## 🔄 WHEN PROCESSING A PAPER:

### Step 1:
Identify Paper ID → Fetch from Paper_Tracker  

### Step 2:
Extract Journal ID  

### Step 3:
Locate Journal_Master → Get Sheet Name  

### Step 4:
Fetch ALL rules from corresponding Journal Sheet  

---

## 🎯 OUTPUT:
- Structured journal requirements  
- Formatting + structure + submission rules  

---

# 📑 SECTION 3: GUIDELINE INTERPRETATION ENGINE

## 🧠 RULE APPLICATION LOGIC:

For each journal requirement:

IF manuscript does NOT match:
→ Mark as ISSUE  
→ Categorize issue type  
→ Generate FIX PROMPT  

---

## 📊 RULE TYPES:

1. Structural Rules  
2. Formatting Rules  
3. Referencing Rules  
4. Language Rules  
5. Ethical Requirements  
6. Submission Requirements  

---

# 📊 SECTION 4: PAPER MEMORY (DYNAMIC FROM EXCEL)

⚠️ DO NOT STORE STATIC PAPER DATA HERE

---

## 🔄 ALWAYS READ FROM:
Paper_Tracker Sheet

---

## 📌 TRACK:

- Iteration Number  
- AI Score  
- Plagiarism Score  
- DOI Accuracy  
- Citation Consistency  
- Desk Rejection Risk  
- Issues Remaining  

---

# 🔁 SECTION 5: ITERATION MEMORY & IMPROVEMENT LOGIC

For each iteration:

1. Compare previous vs current metrics  
2. Identify improvement gaps  
3. Detect unresolved issues  
4. Generate next-level prompts  

---

## 🎯 TARGET THRESHOLDS:

- AI Detection < 10%  
- Plagiarism < 10%  
- DOI Accuracy = 100%  
- Citation Consistency = 100%  
- Desk Rejection Risk < 5%  

---

# 🧠 SECTION 6: PROMPT MEMORY (STATIC INTELLIGENCE)

## 🔧 Structural Fix Prompt
"Align manuscript structure strictly with journal-required sections."

## 🔬 Scientific Improvement Prompt
"Strengthen methodology, novelty, and argumentation depth."

## 🧾 Reference Fix Prompt
"Convert all references into required style and validate DOI accuracy to 100%."

## 🤖 AI Humanization Prompt
"Rewrite content with high linguistic variation to reduce AI detectability below 10%."

## 📊 Evidence Strengthening Prompt
"Enhance claims with strong supporting citations and comparative literature."

---

# ⚠️ SECTION 7: COMMON REJECTION INTELLIGENCE

Across journals, monitor:

- Scope mismatch  
- Weak novelty  
- Poor discussion depth  
- Missing or weak citations  
- High similarity index  
- Formatting non-compliance  

---

# 🎨 SECTION 8: FIGURE & DIAGRAM MEMORY RULES

- All text MUST be inside boxes  
- NO floating text  
- Clear readability and alignment  
- Maintain professional, humanized design  
- Mention figure placement in manuscript  
- Follow journal-specific figure rules from Excel  

---

# 📄 SECTION 9: TITLE PAGE & COVER LETTER MEMORY

## Title Page:
- Authors + Affiliations  
- Corresponding Author Details  
- Funding  
- Ethics  
- Conflict of Interest  
- Data Availability  

## Cover Letter:
- Journal fit justification  
- Research novelty  
- Ethical declaration  
- Submission exclusivity  

---

# 🏁 SECTION 10: DECISION ENGINE

## 📊 JOURNAL MATCHING LOGIC:

IF:
- High-quality manuscript → Q1/Q2  
- Moderate → Q2/Q3  
- Weak → Q3/Q4  

---

# 🔁 SECTION 11: LEARNING MEMORY (SYSTEM IMPROVEMENT)

After each paper:

### Add:
- New journal rules (if missing)  
- Reviewer comments patterns  
- Common rejection reasons  
- Effective prompts  

---

# 🔄 SECTION 12: MEMORY UPDATE RULE

## UPDATE ONLY IN EXCEL:

- AI %  
- Plagiarism %  
- DOI %  
- Citation %  
- Iteration count  
- Status  

---

## DO NOT STORE IN MEMORY.MD:

- Raw manuscript data  
- Journal rules (already in Excel)  
- Paper-specific details  

---

# 🧠 FINAL BEHAVIOR RULE

Always execute in this order:

1. Read Excel (Paper + Journal data)  
2. Fetch journal-specific sheet  
3. Apply memory logic  
4. Execute via content.md  
5. Update Excel  

---

# 🚫 FINAL CONSTRAINTS

- Do NOT assume journal rules  
- Do NOT override Excel data  
- Do NOT mix guidelines across journals  
- ALWAYS prioritize journal-specific sheet  

# 🚫 CONSTRAINT

- Do NOT assume journal rules
- Do NOT override Excel data
- Always prioritize sheet-based requirements
