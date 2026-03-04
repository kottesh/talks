---
title: "Software Estimation"
subtitle: "Techniques and Applications"
author: "Shree Kottes J(7176 22 31 050)"
institute: "Software Project Management (20MSS81)"
theme: default
fonttheme: professionalfonts
---

# What is Software Estimation?

**Definition:**
Software estimation is the process of predicting the effort, cost, duration, and resources required to develop or maintain software.

**Key Parameters:**
- **Effort:** Measured in person-months (PM)
- **Duration:** Measured in months (time to complete)
- **Size:** Measured in SLOC (Source Lines of Code) or Function Points (FP)
- **Cost:** Total financial investment required

---

# Importance of Software Estimation

**Why Estimate?**
- Plan project budget and resources effectively
- Set realistic deadlines and deliverables
- Communicate cost impact to customers
- Form appropriate project teams based on skills and budget
- Manage stakeholder expectations
- Track project progress against baseline

**Challenge:** Estimation is evolutionary - it becomes more accurate as more project information becomes available.

---

# Problems with Poor Estimation

**Over-Estimation:**
- **Parkinson's Law:** Work expands to fill the time available
- Staff may work less efficiently with easy targets
- Unnecessary resource allocation

**Under-Estimation:**
- **Brook's Law:** Adding more people to late projects causes further delays
- Risk to quality due to rushed work
- Extensive rework in later testing phases
- Team burnout and morale issues

---

# Software Estimation Techniques

**Common Techniques:**

1. **Function Point Analysis (FPA)**
   - Size-based estimation using functional components

2. **Wideband Delphi**
   - Consensus-based expert judgment technique

3. **COCOMO (Constructive Cost Model)**
   - Parametric estimation using historical data

4. **Three-Point Estimation**
   - Uses optimistic, pessimistic, and most likely estimates

5. **Expert Judgment**
   - Experience-based estimation

---

# Function Point Analysis (FPA) - Overview

**What is FPA?**
- A method to measure software size based on functionality
- Breaks systems into smaller, analyzable components
- Programming language independent
- Best suited for data processing and business systems

**Process:**
1. Count function points based on system features
2. Adjust for complexity
3. Calculate effort and other metrics

---

# FPA - Five Key Parameters

**Information Domain Characteristics:**

| Parameter | Description | Weight Range |
|-----------|-------------|--------------|
| **External Inputs (EI)** | Input screens and tables | 3-4-6 |
| **External Outputs (EO)** | Output screens and reports | 4-5-7 |
| **External Inquiries (EQ)** | Prompts and interrupts | 3-4-6 |
| **Internal Logical Files (ILF)** | Databases and directories | 7-10-15 |
| **External Interface Files (EIF)** | Shared databases/routines | 5-7-10 |

*Weight values correspond to Simple-Average-Complex complexity*

---

# FPA - Complexity Weights Table

| Measurement Parameter | Simple | Average | Complex |
|-----------------------|--------|---------|---------|
| External Inputs (EI) | 3 | 4 | 6 |
| External Outputs (EO) | 4 | 5 | 7 |
| External Inquiries (EQ) | 3 | 4 | 6 |
| Internal Logical Files (ILF) | 7 | 10 | 15 |
| External Interface Files (EIF) | 5 | 7 | 10 |

**Complexity determined by:** Number of Data Element Types (DETs) and Record Element Types (RETs)

---

# FPA - Calculation Process

**Step 1: Calculate Unadjusted Function Points (UFP)**
UFP = Σ(Count × Weight for each complexity level)

**Step 2: Calculate Complexity Adjustment Factor (CAF)**
CAF = 0.65 + 0.01 × Σ(fi)
- Where: Σ(fi) = Sum of 14 complexity factors (0-5 rating each)
- Range: 0 to 70
- CAF Range: 0.65 to 1.35

**Step 3: Calculate Final Function Points (FP)**
FP = UFP × CAF

---

# FPA - 14 Complexity Factors

The 14 factors (fi) rated from 0 to 5:

1. Data Communications
2. Distributed Data Processing
3. Performance
4. Heavily Used Configuration
5. Transaction Rate
6. Online Data Entry
7. End-User Efficiency
8. Online Update
9. Complex Processing
10. Reusability
11. Installation Ease
12. Operational Ease
13. Multiple Sites
14. Facilitate Change

---

# FPA - Derived Formulas

**Once FP is calculated, derive other metrics:**

- **Productivity**  
  FP / Person-Months (PM)

- **Effort (Person-Months)**  
  FP / Productivity

- **Project Duration**  
  Effort (PM) / Average Team Size

- **Average Staffing**  
  Effort (PM) / Duration

- **Project Cost**  
  FP × Cost per FP  
  **or**  
  Effort × Cost per PM

- **Defect Density**  
  Defects / FP

- **Error Rate**  
  Errors / FP

- **Documentation Size**  
  Pages / FP

- **Maintenance Cost**  
  $ / FP

---

# FPA - Problem Statement

**Given Data:**
- Number of user inputs = 24 (Average)
- Number of user outputs = 46 (Simple)
- Number of inquiries = 8 (Complex)
- Number of files = 4 (Average)
- Number of external interfaces = 2 (Simple)
- Effort = 36.9 person-months
- Technical documents = 265 pages
- User documents = 122 pages
- Cost = $7,744/month
- Processing complexity factors: 4, 1, 0, 3, 3, 5, 4, 4, 3, 3, 2, 2, 4, 5

**Calculate:** Function Points, Productivity, Documentation metrics, Cost per FP

---

# FPA - Solution (Step 1: UFP)

**Calculate Unadjusted Function Points (UFP):**

| Component | Count | Complexity | Weight | Total |
|-----------|-------|------------|--------|-------|
| External Inputs (EI) | 24 | Average | 4 | 96 |
| External Outputs (EO) | 46 | Simple | 4 | 184 |
| External Inquiries (EQ) | 8 | Complex | 6 | 48 |
| Internal Files (ILF) | 4 | Average | 10 | 40 |
| External Interfaces (EIF) | 2 | Simple | 5 | 10 |

**UFP = 96 + 184 + 48 + 40 + 10 = 378**

---

# FPA - Solution (Step 2: CAF)

**Calculate Complexity Adjustment Factor (CAF):**

Given complexity factors: 4, 1, 0, 3, 3, 5, 4, 4, 3, 3, 2, 2, 4, 5

Σ(fi) = 4 + 1 + 0 + 3 + 3 + 5 + 4 + 4 + 3 + 3 + 2 + 2 + 4 + 5 = **43**

**CAF = 0.65 + 0.01 × Σ(fi)**
**CAF = 0.65 + 0.01 × 43**
**CAF = 0.65 + 0.43 = 1.08**

---

# FPA - Solution (Step 3: Final FP)

**Calculate Function Points:**

**FP = UFP × CAF**
**FP = 378 × 1.08**
**FP = 408.24 ≈ 408 Function Points**

---

# FPA - Solution (Additional Metrics)

**Productivity:**
- Productivity = FP / Effort
- Productivity = 408 / 36.9 = **11.06 FP/PM**

**Documentation Metrics:**
- Total documentation = 265 + 122 = 387 pages
- Pages per FP = 387 / 408 = **0.95 pages/FP**

**Cost per Function Point:**
- Total cost = $7,744 × 36.9 = $285,753.60
- Cost per FP = $285,753.60 / 408 = **$700.38/FP**

---

# Wideband Delphi - Overview

**Background:**
- Original Delphi method developed in 1940s by RAND Corporation
- Wideband Delphi refined in 1970s by Barry Boehm and John Farquhar
- Added greater interaction and communication between participants

**What is it?**
- Consensus-based estimation technique
- Uses expert judgment from experienced team members
- Iterative process to reach agreement on estimates

**Best for:** Projects with experienced team members available

---

# Wideband Delphi - Process

**Team Setup:**
- 3 or more experienced staff members
- Mix of skills and perspectives

**Process Steps:**
1. **Kickoff Meeting:** Present task to be estimated
2. **Individual Estimation:** Each person estimates independently
3. **Estimation Meeting:** Plot all estimates and discuss assumptions
4. **Discussion:** Identify differences in assumptions
5. **Re-estimation:** Agree on assumptions and re-estimate
6. **Iteration:** Continue until estimates converge
7. **Final Estimate:** Calculate using three-point formula

---

# Wideband Delphi - Method Flow

**Step-by-Step Process:**

1. **Task Presentation**
   - Clear problem statement provided
   - Scope and constraints explained

2. **Independent Work**
   - Each expert estimates assuming uninterrupted work
   - No consultation with others initially

3. **Anonymous Collection**
   - Estimates collected without attribution
   - Reduces influence and bias

4. **Group Discussion**
   - Plot estimates on chart/graph
   - Discuss outliers and assumptions
   - Identify hidden complexities

5. **Consensus Building**
   - Multiple rounds if needed
   - Agreement on realistic estimate

---

# Wideband Delphi - Formula

**Three-Point Estimation Formula:**

**Effort Estimate = (O + 4M + P) / 6**

Where:
- **O = Optimistic estimate** (lowest estimate in person-months)
- **M = Most Likely estimate** (average/mode of most common estimates)
- **P = Pessimistic estimate** (highest estimate in person-months)

**This is a weighted average giving more weight to the most likely scenario**

Alternative: **Triangular Distribution = (O + M + P) / 3**

---

# Wideband Delphi - Problem Statement

**Scenario:**
A software development team is estimating effort for a new mobile application feature. Five experienced developers participate in the Wideband Delphi session.

**Estimation Results (Round 1):**
- Developer A: 2.5 person-months
- Developer B: 4.0 person-months
- Developer C: 3.5 person-months
- Developer D: 5.0 person-months
- Developer E: 3.0 person-months

**Task:** Calculate the effort estimate using the Wideband Delphi formula.

---

# Wideband Delphi - Solution (Step 1)

**Step 1: Identify the Three Key Values**

From the estimates: 2.5, 3.0, 3.5, 4.0, 5.0 person-months

- **Optimistic (O)** = Lowest estimate = **2.5 PM**

- **Pessimistic (P)** = Highest estimate = **5.0 PM**

- **Most Likely (M)** = Average of middle estimates or mode
  - Middle values: 3.0, 3.5, 4.0
  - Average: (3.0 + 3.5 + 4.0) / 3 = 10.5 / 3 = **3.5 PM**

---

# Wideband Delphi - Solution (Step 2)

**Step 2: Apply the Formula**

**Formula:** Effort Estimate = (O + 4M + P) / 6

**Substituting values:**

Effort Estimate = (2.5 + 4(3.5) + 5.0) / 6

Effort Estimate = (2.5 + 14.0 + 5.0) / 6

Effort Estimate = 21.5 / 6

**Effort Estimate = 3.58 person-months**

**Rounded: ≈ 3.6 person-months**

---

# Wideband Delphi - Solution (Interpretation)

**Result Analysis:**

**Final Estimate: 3.6 person-months**

**What this means:**
- The weighted average gives more importance to the most likely scenario
- The estimate accounts for both optimistic and pessimistic views
- This provides a balanced, realistic estimate

**Next Steps:**
- If estimates still vary widely, conduct another discussion round
- Document assumptions that led to this estimate
- Use this as baseline for project planning

---

# Wideband Delphi - Advantages & Disadvantages

**Advantages:**
- Very simple and straightforward process
- Consensus-based estimates more accurate than individual ones
- People doing the work make the estimates
- Assumptions are documented and agreed upon
- Reduces individual bias
- Incorporates diverse perspectives

**Disadvantages:**
- Requires management cooperation and support
- Time-consuming with multiple rounds
- May not align with management expectations
- Requires experienced team members
- Can be influenced by dominant personalities

---

# Comparison: FPA vs Wideband Delphi

| Aspect | Function Point Analysis | Wideband Delphi |
|--------|------------------------|-----------------|
| **Basis** | Functional size measurement | Expert judgment |
| **Input Required** | Detailed requirements | Expert experience |
| **Accuracy** | High for similar projects | Depends on expert quality |
| **Time** | Moderate calculation time | Can be time-consuming |
| **Best For** | Data processing systems | Novel/uncertain projects |
| **Objectivity** | More objective/quantitative | More subjective |
| **Dependencies** | Requires complete specs | Requires expert availability |

---

# When to Use Each Technique

**Use Function Point Analysis when:**
- Requirements are well-defined and documented
- Developing business/data processing systems
- Need objective, repeatable measurements
- Historical FP data available for comparison
- Contract requires size-based pricing

**Use Wideband Delphi when:**
- Requirements are uncertain or evolving
- Limited historical data available
- Expert team members are accessible
- Project involves novel technology or domain
- Need quick initial estimates
- Building consensus is important

---

# Conclusion

**Key Takeaways:**

- Software estimation is critical for project success
- Different techniques serve different purposes
- Function Point Analysis provides objective size measurement
- Wideband Delphi leverages expert consensus
- Estimation accuracy improves with experience and data
- Regular refinement is essential
- Combine multiple techniques for best results

---

# Q&A

**Questions?**

Thank you for your attention!

