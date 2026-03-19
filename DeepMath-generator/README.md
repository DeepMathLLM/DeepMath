# DeepMath-Generator

## 🔬 Project Overview

**DeepMath-Generator** is the second major initiative of the DeepMath project. While our first work focused on **measuring** mathematical creativity in LLMs, this project dares to ask a more profound question:

**Can large language models not just solve problems, but create them?**

The answer, as revealed in our paper ["Can LLM generate interesting mathematical research problems?"](./), is a resounding **yes**. Through an innovative multi-agent system, we have successfully generated **665 expert-verified, research-level problems in differential geometry**—marking a historic milestone in AI-assisted mathematical discovery.

---

## ⚙️ Generation Workflow

The DeepMath-Generator employs a sophisticated two-agent architecture to ensure both creativity and quality in problem generation. Below is the complete workflow:

                    ┌─────────────────┐
                    │   Knowledge     │
                    │   Point Input   │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │   Generator     │
                    │      LLM        │◄────────┐
                    │ (Creative Role) │         │
                    └────────┬────────┘         │
                             │                   │
                     Generates Problem           │
                             │                   │
                             ▼                   │
                    ┌─────────────────┐          │
                    │   Reviewer      │          │
                    │      LLM        │          │
                    │ (Quality Control│          │
                    └────────┬────────┘          │
                             │                   │
                    ┌────────┴────────┐          │
                    ▼                 ▼          │
                ┌──────────┐    ┌──────────┐    │
                │  Pass?   │───►│   Fail   │────┘
                └────┬─────┘ No └──────────┘
                     │ Yes              
                     ▼                   
            ┌─────────────────┐          
            │  Save to .tex   │          
            │  (Qualified)    │          
            └─────────────────┘          
                     │                    
                     ▼                    
    ┌────────────────────────────────────┐
    │   Check Termination Condition:     │
    │  Either PASS or MAX_ATTEMPTS hit  │
    └────────────────────────────────────┘
                     │
                     ▼
    ┌────────────────────────────────────┐
    │    Move to next problem slot       │
    │ (Target: 5 problems per knowledge  │
    │            point)                  │
    └────────────────────────────────────┘
                     │
                     ▼
    ┌────────────────────────────────────┐
    │    Move to next knowledge point    │
    │   (200 knowledge points total)     │
    └────────────────────────────────────┘
                     │
                     ▼
            ┌─────────────────┐
            │   Final Set:    │
            │ 665 Qualified   │
            │   Problems      │
            └─────────────────┘

### 🔄 Step-by-Step Process

1. **Input**: The system receives a specific mathematical knowledge point in differential geometry as the generation target.

2. **Generation Phase**: 
   - The **Generator LLM** (creative role) produces an original research problem based on the given knowledge point
   - Each generated problem aims to be novel, non-trivial, and research-worthy

3. **Review Phase**:
   - The **Reviewer LLM** (quality control role) evaluates the generated problem against rigorous criteria
   - Assessment includes: originality, mathematical validity, research potential, and clarity

4. **Iterative Refinement**:
   - If the problem fails review, it returns to the Generator for improvement
   - This cycle continues until the problem passes review or reaches attempt limits
   - Once a problem passes, it is immediately saved

5. **Batch Completion**:
   - This process repeats until **5 qualified problems** are generated for the current knowledge point
   - The system then advances to the next knowledge point

6. **Large-Scale Iteration**:
   - The entire workflow iterates across **200 distinct knowledge points** in differential geometry
   - Final output: **665 qualified problems** (some knowledge points yielded fewer than 5 passing problems)

---

## 📁 Repository Contents

| File/Folder | Description |
|-------------|-------------|
| [`generator_prompt.md`](./generator_prompt.md) | System prompt for the Generator LLM (creative role) |
| [`reviewer_prompt.md`](./reviewer_prompt.md) | System prompt for the Reviewer LLM (quality control) |
| [`problems/`](./problems/) | Complete collection of 665 expert-verified problems |

---

## 🎯 Key Achievements

- **665 qualified, expert-verified research problems** in differential geometry
- **200 knowledge points** systematically explored
- **Two specialized LLM agents** with distinct creative and evaluative roles
- **Rigorous quality control** through iterative review process
- **First-of-its-kind demonstration** of LLMs generating genuinely novel mathematical research directions

---

## 🔗 Related Resources

- [Main DeepMath Project](../)
- [DeepMath-Creative Benchmark](../DeepMath-Creative/)
- [Research Paper: "Can LLM generate interesting mathematical research problems?"](./)

---

**From knowledge to creativity — DeepMath-Generator: Where AI becomes a mathematical discoverer.**
