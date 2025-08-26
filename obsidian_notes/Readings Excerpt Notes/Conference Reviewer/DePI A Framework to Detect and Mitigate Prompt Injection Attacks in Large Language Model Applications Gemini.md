---
tags: 
aliases: 
date of note: 2025-07-01
---
### **Appropriateness**

**Does this paper fit in AMLC?**

- ✅ Yes = This paper is appropriate to the AMLC audience (most submissions).
    

---

### **Type of Contribution**

**Which category does this paper best fit?**

- 🏗️ Deployed = This paper describes contributions in a deployed system.
    
    - Reviewer's note: The work is framed as a framework with direct application and testing for a critical Amazon system (BRP), and the customer problem statement suggests it's being integrated into production systems.
        

---

### **Customer Problem**

**Was the Amazon customer problem that this work addresses clearly stated?**

- ✅ Yes = The paper clearly states a customer problem.
    
    - Reviewer's note: The paper clearly articulates the threat of prompt injection attacks against LLM agents used in Amazon's Buyer Risk Prevention (BRP) and Seller Partner Support (SPS) organizations, detailing the potential for manipulated fraud decisions and financial impact.
        

---

### **Paper Strengths**

**Please provide feedback to the authors on the paper strengths.**

This is a timely and highly relevant paper that addresses what is arguably the most critical security vulnerability for applied LLM systems at Amazon. The primary strength of this work is its systematic and practical approach to a complex problem. The proposed DePI framework, which encompasses evaluation, detection, and simulation, provides a robust, flywheel-like model for continuously improving security posture, which is exactly what is needed for the evolving threat landscape.

The paper's exploration of two complementary defense mechanisms—Prompt Enhancement and an Auxiliary Detector—is another significant strength. This dual approach offers both a low-friction, immediate mitigation path (prompt engineering) and a more robust, scalable long-term solution (a fine-tuned auxiliary model). The empirical results are strong, particularly the demonstration that a fine-tuned LLM (AD-SFT) significantly outperforms embedding-based classifiers, achieving near-perfect recall and precision on the test sets . This provides a clear, data-driven recommendation for the most effective architecture.

Finally, the work on synthetic data generation is a standout contribution. Recognizing the scarcity of high-quality, domain-specific attack data is key, and the authors present a clear methodology for creating it. The analysis showing that combining real and synthetic data yields the best performance, and that domain-specific seeds are crucial, offers an invaluable and actionable insight for other teams at Amazon facing similar data challenges.

---

### **Paper Weaknesses**

**Please provide feedback to the authors on the paper weaknesses / areas for improvement.**

While the paper is strong, there are opportunities for improvement. The "framework" aspect of DePI, while conceptually sound, feels underdeveloped in the paper's narrative. The work heavily focuses on the "Detection/Prevention" component, while the "Evaluation" and "Simulation" loops are presented more as inputs to the process rather than fully integrated parts of a flywheel. To strengthen the paper, I would suggest elaborating on how the framework enables a continuous cycle: for example, how are the outputs of the detector used to inform the next round of resilience evaluation or to guide the generation of more challenging synthetic attacks?

Second, the evaluation of the "Prompt Enhancement" techniques, while showing positive results, feels somewhat preliminary. The directive-based and reasoning-based enhancements are effective against the demonstrated attack but are still fundamentally heuristic. A discussion of their limitations against more sophisticated, multi-turn, or obfuscated attacks would add more depth. This would also help motivate the necessity of the more complex Auxiliary Detector more strongly.

Finally, while the results for the Auxiliary Detector are impressive, the evaluation could be strengthened by testing against a third, completely held-out dataset that was not used for seeding the synthetic data (i.e., not `deepset` or `safeguard`). This would provide more convincing evidence of the model's ability to generalize to truly unseen attack patterns and mitigate concerns that the performance gains are tied too closely to the data distributions used in training and synthetic generation. The connection to the production system is mentioned but could be made more concrete in the results section (e.g., performance metrics from a shadow-mode deployment or A/B test).

---

### **Customer Problem Importance**

**Is the customer problem that this paper addresses an important problem to solve?**

- ✅ Yes = The paper addresses an important customer problem to solve.
    
    - Reviewer's note: Prompt injection is the OWASP #1 threat for LLM applications and poses a direct risk to critical Amazon functions like fraud detection.
        

---

### **Problem Solution**

**How far did the work go in solving the customer problem?**

- 4️⃣ = The paper provides a solution that is substantially different from an existing solution.
    
    - _Reviewer's note: The paper provides a well-researched, multi-pronged solution with strong empirical backing that moves well beyond generic LLM safeguards and tailors defenses to a specific, high-stakes Amazon use case._
        

---

### **Originality**

**How original is the approach or application?**

- 3️⃣ = Notable extension of existing work.
    
    - _Reviewer's note: While the concepts of auxiliary detectors and synthetic data generation exist, this paper provides a novel and comprehensive application of these techniques as a cohesive framework for the prompt injection problem within Amazon. The detailed analysis comparing different detector architectures and data strategies provides significant original value._
        

---

### **Clarity**

**Is the paper well-structured and well-written?**

- 5️⃣ = Very clear.
    
    - _Reviewer's note: The paper is well-organized, easy to follow, and effectively uses tables and figures to support its claims. The methodology and results are presented with high clarity._
        

---

### **Presentation Format**

**If accepted, how should this paper be presented?**

- 🎤 Oral Presentation
    

---

### **Overall Decision**

**How important is it to accept this paper to AMLC?**

- 5️⃣ = I would fight for this paper to be accepted.
    
    - _Reviewer's note: This paper tackles a Tier 1 problem for applied AI at Amazon with scientific rigor and a practical mindset. The findings are highly actionable for numerous teams across the company. It represents exactly the kind of high-impact, applied science work that AMLC should showcase._
        

---

### **Confidence**

**How confident are you in your review?**

- 5️⃣ = Positive my evaluation is correct; read carefully, familiar with related work.


-----------
##  Recommended Notes