---
name: master-skill-controller
description: "Central orchestration system for academic manuscript processing workflow. Routes tasks, controls execution order, and manages dependencies between specialized skills."
version: "1.0.0"
license: "MIT"
---

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
  module: Turnitin 2026 Advanced Plagiarism Detection
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
  module: Turnitin 2026 Advanced Plagiarism Detection
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

---

## INTEGRATED MODULE CONFIGURATION

### Reference Reconciliation Engine Integration

module_configuration:
  reference_reconciliation_engine:
    name: "Reference Reconciliation Engine"
    description: "Automated citation-reference mapping and validation system ensuring 100% consistency"
    
    capabilities:
      - citation_extraction: "Identify all in-text citations from manuscript text"
      - reference_extraction: "Parse and extract all reference list entries"
      - mapping_generation: "Build comprehensive citation-reference correlation table"
      - orphan_detection: "Identify unused citations and uncited references"
      - doi_validation: "CrossRef and PubMed API-based DOI verification"
      - mismatch_identification: "Detect author/year/content mismatches"
      - auto_resolution: "Smart fixing of citation/reference issues"
      - style_normalization: "Journal-specific citation format conversion"
      - final_validation: "Comprehensive consistency checking loop"
      
    strict_rules:
      - no_fabrication: "Never generate fake references"
      - verifiable_sources_only: "Use only authenticated academic databases"
      - scopus_pubmed_preference: "Prioritize high-impact indexed publications"
      - style_consistency_maintenance: "Ensure uniform citation formatting"
      
    auto_resolve_strategies:
      missing_reference_fix:
        - context_claim_extraction: "Identify surrounding argument and topic"
        - database_query: "Search PubMed/CrossRef/Google Scholar/Scopus"
        - relevance_filtering: "Select most appropriate recent high-impact sources"
        - verified_insertion: "Add proper reference with DOI and correct styling"
        
      orphan_reference_handling:
        - relevance_assessment: "Evaluate reference importance to manuscript"
        - text_integration: "Insert citation at relevant claim points"
        - removal_protocol: "Eliminate irrelevant unused references"
        
      broken_doi_repair:
        - crossref_query: "Validate DOI through official registries"
        - metadata_retrieval: "Fetch complete reference information"
        - entry_replacement: "Update with correct DOI and full metadata"
        
      citation_mismatch_correction:
        - alignment_process: "Match citation format with reference content"
        - replacement_strategy: "Substitute with correctly matched references"
        
    smart_insertion_protocol:
      claim_attachment:
        - statistical_data_citation: "Link references to numerical claims"
        - literature_statement_support: "Connect to prior research mentions"
        - methodology_backing: "Provide sources for techniques used"
        - theoretical_framework_citation: "Support conceptual foundations"
        
    style_normalization_formats:
      supported_styles:
        - vancouver: "[1], [2], [3] numeric format"
        - apa: "(Smith, 2020) author-date format"
        - harvard: "(Smith 2020) simplified author-date"
        - ieee: "[12] bracketed numeric citations"
        - chicago: "(Smith 2020, 45) with page numbers"
        - mla: "(Smith 45) literature format"
        
    final_validation_checks:
      - complete_mapping: "Every citation paired with reference"
      - reciprocal_citation: "Every reference has in-text citation"
      - doi_functionality: "All DOIs resolve to correct content"
      - duplicate_elimination: "No repeated or redundant entries"
      - sequential_numbering: "Proper citation sequence maintenance"
      
    output_guarantees:
      - zero_orphan_citations: "All text citations have reference entries"
      - zero_orphan_references: "All references are cited in text"
      - perfect_doi_accuracy: "100% functional DOI links"
      - journal_ready_formatting: "Compliance with target publication standards"
      - reviewer_proof_bibliography: "Flawless reference section for peer review"

---

## WORKFLOW PIPELINE INTEGRATION

workflow_pipeline:
  pre_submission_processing:
    reference_reconciliation_phase:
      processing_order:
        - citation_reference_extraction: "Simultaneous parsing of both elements"
        - mapping_table_generation: "Correlation matrix creation"
        - problem_detection: "Systematic issue identification"
        - auto_fix_implementation: "Smart resolution deployment"
        - style_normalization: "Format conversion to journal requirements"
        - final_validation_loop: "Comprehensive quality assurance"
        
      semi_automated_approach:
        ai_suggestion_generation: "Automated fix proposals"
        human_verification_layer: "Author/reviewer approval step"
        quick_scan_integration: "Efficient review process"
        finalization_protocol: "Approved changes implementation"
        
      advanced_system_integration:
        claude_gpt_processing: "AI-powered extraction and analysis"
        crossref_api_connectivity: "Official DOI validation"
        pubmed_api_integration: "Medical literature verification"
        excel_like_tracker: "Visual mapping and progress monitoring"
        
      reality_check_protocol:
        risk_mitigation: "Prevent over-automation without oversight"
        publishing_industry_alignment: "Follow professional service standards"
        quality_assurance_layer: "Human-in-the-loop verification system"

---

## EXECUTION CONTROL MATRIX

execution_control:
  phase_1_validation:
    priority: "highest"
    parallel_execution: true
    dependency_check: "citation_map_before_doi_check"
    timeout: "300_seconds"
    
  phase_2_fixing:
    priority: "high"
    sequential_execution: true
    dependency_chain: "plagiarism_fix_before_ai_humanize"
    rollback_capability: true
    
  phase_3_quality:
    priority: "medium"
    conditional_execution: "based_on_data_presence"
    expert_review_required: true
    
  phase_4_optimization:
    priority: "medium"
    impact_focused: true
    journal_specific: true
    
  phase_5_output:
    priority: "low"
    final_quality_gate: true
    format_compliance: "mandatory"

---

## ERROR HANDLING AND RECOVERY

error_handling:
  retry_mechanism:
    max_attempts: 3
    backoff_strategy: "exponential"
    fallback_procedures: "manual_override_available"
    
  data_integrity:
    checksum_verification: "before_after_processing"
    rollback_protocols: "atomic_transaction_support"
    recovery_points: "milestone_based_saving"
    
  user_intervention:
    escalation_paths: "progressive_complexity"
    notification_system: "real_time_alerts"
    override_permissions: "authorized_personnel_only"

---

## PERFORMANCE MONITORING

performance_metrics:
  processing_speed:
    target_time: "< 10_minutes_full_manuscript"
    bottleneck_identification: "real_time_monitoring"
    optimization_triggers: "performance_degradation_detection"
    
  accuracy_tracking:
    validation_scores: "continuously_monitored"
    false_positive_rates: "< 0.5%"
    user_satisfaction: "> 4.8/5.0"
    
  resource_utilization:
    cpu_efficiency: "optimal_scaling"
    memory_management: "efficient_allocation"
    network_bandwidth: "optimized_data_transfer"

---
