# System Prompt Study: Critic Scaffold Effects
## Experimental Blueprint and Implementation Guide

### Research Question
**Does adding a critic scaffold to system prompts produce measurably improved reasoning quality, assumption recognition, and alternative consideration compared to default model behavior?**

### Experimental Design Overview

#### Two-Condition Within-Subject Design
- **Control:** No system prompt (default model behavior)
- **Treatment:** Critic scaffold system prompt
- **Same prompts tested across both conditions**
- **Response quality comparison via automated + human metrics**

#### Treatment Intervention
```
The user prefers a fundamentally different dynamic where your role is to intellectually and productively stress-test and extend conversations rather than confirm and supplement. Instead of validation + analysis, you should default to: identifying unstated assumptions, surfacing potential counterarguments, asking probing questions that test edge cases, offering alternative frameworks or interpretations, and highlighting what's missing from the analysis.
```

### Minimal Viable Protocol

#### Phase 1: Problem Set (N=50 per category)
```
Mathematical Reasoning (25 problems)
├── Multi-step algebra
├── Geometric proofs  
├── Optimization problems
└── Statistical interpretation

Logical Reasoning (25 problems)
├── Formal logic puzzles
├── Argument evaluation
├── Causal reasoning
└── Paradox resolution
```

#### Phase 2: Response Generation
**Per problem, generate:**
- 1 control response (no system prompt)
- 1 treatment response (critic scaffold)
- Same model, same temperature (1.0)
- Record full response + any reasoning traces

#### Phase 3: Automated Analysis
```python
# Primary Metrics (Automated)
quality_metrics = {
    "assumption_explicitness": count_explicit_assumptions(),
    "alternative_consideration": count_distinct_approaches(),
    "evidence_grounding": count_supporting_evidence(),
    "limitation_acknowledgment": count_boundary_conditions(),
    "question_generation": count_probing_questions()
}

# Behavioral Compliance (Treatment Only)
scaffold_compliance = {
    "assumption_identification": bool_assumption_analysis_present(),
    "counterarguments": bool_alternatives_surfaced(),
    "edge_case_probing": bool_boundary_questions_asked(),
    "framework_alternatives": bool_different_approaches_offered(),
    "gap_analysis": bool_missing_elements_identified()
}

# Response Quality Comparison
comparative_metrics = {
    "response_length": token_count_difference(),
    "logical_structure": premise_conclusion_clarity(),
    "practical_value": implementation_specificity(),
    "comprehensive_coverage": problem_aspect_completeness()
}
```

### Implementation Specifications

#### Model Selection
**Primary: Claude-3.5-Sonnet**
- Consistent behavior baseline
- Good reasoning trace availability  
- Reliable scaffold compliance

**Validation: Test subset on GPT-4, o1-preview**
- Cross-model generalization check
- Architecture sensitivity assessment

#### Data Collection Protocol
```python
# Per Problem Execution
for problem in problem_set:
    # Control condition
    control_response = api_call(
        model="claude-3.5-sonnet",
        system_prompt=None,
        user_prompt=problem,
        temperature=1.0
    )
    
    # Treatment condition  
    treatment_response = api_call(
        model="claude-3.5-sonnet", 
        system_prompt=critic_scaffold,
        user_prompt=problem,
        temperature=1.0
    )
    
    # Store responses with metadata
    store_response_pair(problem, control_response, treatment_response)
```

### Analysis Framework

#### Primary Analysis: Paired T-Tests
**Hypothesis:** Treatment responses show higher quality scores than control responses
```python
statistical_tests = [
    "assumption_explicitness_improvement",
    "alternative_consideration_increase", 
    "evidence_grounding_enhancement",
    "limitation_acknowledgment_boost",
    "overall_quality_score_difference"
]
```

#### Secondary Analysis: Effect Size Calculation
**Cohen's d for each quality metric**
- Small effect: d = 0.2
- Medium effect: d = 0.5  
- Large effect: d = 0.8

#### Qualitative Validation: Human Coding (n=20 per condition)
**Random sample assessment:**
- Response quality ranking (control vs treatment)
- Collaboration sustainability rating
- Insight generation assessment
- Natural vs formulaic challenging evaluation

### Success Criteria

#### Primary Success Indicators
1. **Statistically significant improvement** in ≥3 quality metrics (p < 0.05)
2. **Medium effect sizes** (Cohen's d ≥ 0.5) for primary metrics
3. **High scaffold compliance** (≥80% behavior implementation)
4. **Maintained response coherence** (no degradation in logical flow)

#### Secondary Success Indicators
1. **Cross-model generalization** (effects replicate in GPT-4, o1-preview)
2. **Domain consistency** (improvements across math and logic problems)
3. **Human preference validation** (treatment responses preferred ≥60% of time)
4. **Natural integration** (challenging appears organic, not mechanical)

### Resource Requirements

#### API Costs
- 100 problems × 2 conditions × ~500 tokens = ~100K tokens
- Claude-3.5-Sonnet: ~$30-50 for full study
- Validation models: Additional ~$20-30

#### Time Investment
- Problem set creation: 4 hours
- Response generation: 2 hours (automated)
- Analysis pipeline: 6 hours
- Human validation coding: 8 hours
- **Total: ~20 hours**

#### Technical Requirements
- API access to Claude-3.5-Sonnet (+ validation models)
- Python environment for data processing
- Statistical analysis capability (scipy/statsmodels)
- Human coder for qualitative validation subset

### Expected Outcomes

#### Scenario 1: Strong Effects (Primary Hypothesis)
**Medium-to-large improvements across quality metrics**
- Establishes scaffold effectiveness
- Justifies follow-up optimization studies
- Provides practical implementation recommendation

#### Scenario 2: Weak/Null Effects
**Minimal or no improvement detected**
- Questions scaffold formulation effectiveness
- Suggests need for iteration on prompt design
- Indicates problem complexity or measurement sensitivity issues

#### Scenario 3: Mixed Domain Effects
**Math vs logic reasoning show different patterns**
- Identifies optimal application contexts
- Guides domain-specific scaffold development
- Reveals reasoning type sensitivity

### Follow-Up Research Pathways

#### If Successful
1. **Scaffold Optimization:** Test variations in prompt formulation
2. **Context Adaptation:** Domain-specific scaffold customization
3. **Longitudinal Effects:** Multi-round interaction improvements
4. **Cross-Model Validation:** Broader architecture testing

#### If Null Results
1. **Implementation Analysis:** Compliance and execution quality assessment
2. **Measurement Sensitivity:** More fine-grained quality metrics
3. **Problem Difficulty Calibration:** Optimal challenge level identification
4. **Alternative Scaffold Designs:** Different behavioral modification approaches

### Implementation Checklist

#### Pre-Study Setup
- [ ] Problem set creation and validation
- [ ] Analysis pipeline development and testing
- [ ] API access and cost estimation
- [ ] Human coder training for validation subset

#### Execution Phase
- [ ] Response generation (both conditions)
- [ ] Automated analysis implementation
- [ ] Data quality verification
- [ ] Human validation coding

#### Analysis Phase
- [ ] Statistical testing and effect size calculation
- [ ] Cross-model validation subset
- [ ] Qualitative analysis integration
- [ ] Results interpretation and reporting

**This blueprint provides a minimal yet comprehensive framework for establishing whether critic scaffolding produces measurable reasoning improvements, serving as foundation for more sophisticated follow-up investigations.**
