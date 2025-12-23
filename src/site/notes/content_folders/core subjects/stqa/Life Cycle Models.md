---
{"dg-publish":true,"permalink":"/content-folders/core-subjects/stqa/life-cycle-models/"}
---

# 1. Waterfall Model

## Definition

The **Waterfall Model** is a **linear and sequential** software development model where each phase must be completed **fully** before moving to the next.

## Phases

1. Requirement Analysis
    
2. System Design
    
3. Implementation (Coding)
    
4. Integration & Testing
    
5. Deployment
    
6. Maintenance


Each phase produces deliverables that act as inputs for the next phase.

## Key Characteristics

- No overlapping of phases
    
- No going back once a phase is completed
    
- Heavy documentation


## Advantages

- Simple and easy to understand
    
- Clear milestones and deliverables
    
- Works well when requirements are fixed and well understood


## Disadvantages

- Very rigid and inflexible
    
- Late testing (testing happens only after coding)
    
- Not suitable for changing requirements


## Suitability

- Small projects
    
- Stable and well-defined requirements
    
- Low-risk systems


---

# 2. Prototyping Model

## Definition

The **Prototyping Model** involves building a **working model (prototype)** of the system to understand and refine requirements through user feedback.

## Types of Prototyping

- **Throwaway Prototyping**: Prototype is discarded after requirement clarification
    
- **Evolutionary Prototyping**: Prototype is gradually improved into the final system


## Process Flow

1. Initial Requirements
    
2. Quick Design
    
3. Build Prototype
    
4. User Evaluation
    
5. Refinement
    
6. Final System Development


## Advantages

- Better requirement understanding
    
- Early user involvement
    
- Reduces requirement ambiguity


## Disadvantages

- Can lead to poor system design if prototype is rushed
    
- Users may think prototype is the final product
    
- Not suitable for large, complex systems


## Suitability

- Systems with unclear or evolving requirements
    
- User-interface-intensive applications


---

# 3. Rapid Application Development (RAD) Model

## Definition

**RAD** focuses on **fast development** using reusable components, parallel development, and minimal planning.

## Phases

1. Requirements Planning
    
2. User Design (workshops & prototypes)
    
3. Construction
    
4. Cutover (Testing & Deployment)


## Key Characteristics

- Extensive user involvement
    
- Time-boxed development
    
- Component-based construction


## Advantages

- Faster delivery
    
- High productivity
    
- Flexible to changes


## Disadvantages

- Requires skilled developers
    
- Not suitable for large, high-risk systems
    
- Depends heavily on user availability


## Suitability

- Short-term projects
    
- Systems requiring rapid delivery


---

# 4. Spiral Model (Iterative Model)

## Definition

The **Spiral Model** combines **iterative development** with **risk analysis**, progressing through repeated loops (spirals).

## Each Spiral Includes

1. Planning
    
2. Risk Analysis
    
3. Engineering
    
4. Evaluation


## Key Characteristics

- Risk-driven approach
    
- Iterative refinement
    
- Continuous user feedback


## Advantages

- Excellent risk management
    
- Flexible to changes
    
- Suitable for large and complex systems


## Disadvantages

- Expensive
    
- Complex to manage
    
- Requires risk assessment expertise


## Suitability

- High-risk projects
    
- Large and mission-critical systems


---

# 5. V-Model (Verification and Validation Model)

## Definition

The **V-Model** is an extension of the Waterfall Model where **testing activities are planned in parallel** with development phases.

## Structure

- Left side: Development phases
    
- Right side: Corresponding testing phases


|Development Phase|Testing Phase|
|---|---|
|Requirement Analysis|Acceptance Testing|
|System Design|System Testing|
|Architecture Design|Integration Testing|
|Module Design|Unit Testing|

## Advantages

- Early test planning
    
- Improved defect detection
    
- Clear relationship between development and testing


## Disadvantages

- Rigid like Waterfall
    
- No early working software
    
- Not suitable for changing requirements


## Suitability

- Safety-critical systems
    
- Well-defined requirements


---

# 6. V-Model with Simultaneous Testing

## Definition

This variation emphasizes that **testing activities run simultaneously** with development, not just planned but actively executed where possible.

## Key Enhancements

- Test cases are written alongside development
    
- Early static testing (reviews, inspections)
    
- Continuous validation


## Advantages

- Early defect detection
    
- Reduced rework cost
    
- Improved software quality


## Disadvantages

- Requires disciplined process
    
- Higher initial effort
    
- Still rigid in structure


## Suitability

- Quality-critical systems
    
- Organizations with mature testing practices


---

# 7. Modified V-Model

## Definition

The **Modified V-Model** enhances flexibility by introducing **iteration, feedback loops, and partial overlap** between phases.

## Key Features

- Backward movement between phases allowed
    
- Iterative testing cycles
    
- Continuous verification and validation


## Advantages

- More flexible than standard V-Model
    
- Better handling of requirement changes
    
- Early and continuous testing


## Disadvantages

- Increased management complexity
    
- Requires skilled coordination


## Suitability

- Medium to large projects
    
- Systems requiring both structure and flexibility


---

# 8. Comparison of All Models (Exam-Oriented)

|Aspect|Waterfall|Prototyping|RAD|Spiral|V-Model|V-Model + Testing|Modified V-Model|
|---|---|---|---|---|---|---|---|
|Approach|Linear|Iterative|Rapid & Parallel|Iterative|Linear|Linear + Early Testing|Semi-Iterative|
|Flexibility|Very Low|High|High|Very High|Low|Low|Medium|
|Risk Handling|Poor|Medium|Low|Excellent|Poor|Medium|Good|
|User Involvement|Low|Very High|Very High|High|Low|Medium|Medium|
|Testing Start|Late|After Prototype|Early|Every Iteration|Planned Early|Simultaneous|Continuous|
|Cost|Low|Medium|Medium|High|Medium|Medium|Medium–High|
|Best For|Stable Requirements|UI-based systems|Fast delivery|High-risk systems|Critical systems|Quality-focused systems|Balanced projects|

---

# 9. One-Line Exam Memory Tips

- **Waterfall** → Sequential, no flexibility
    
- **Prototyping** → Learn requirements by building first
    
- **RAD** → Speed and reuse
    
- **Spiral** → Risk-driven iteration
    
- **V-Model** → Testing mapped to development
    
- **V-Model with Testing** → Test early and continuously
    
- **Modified V-Model** → Structured but flexible


---