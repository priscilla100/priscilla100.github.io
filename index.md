---
layout: homepage
---

## About Me

I am a **third-year PhD candidate** in Computer Science at [Stony Brook University](https://www.cs.stonybrook.edu/), advised by [Dr. Omar Chowdhury](https://www3.cs.stonybrook.edu/~omar/). My research bridges **formal methods** and **large language models** to build trustworthy AI systems for security-critical applications.

I work on two interconnected problems:

1. **Evaluation**: How reliable are LLMs for generating formal specifications? My systematic evaluation framework assesses LLM-generated temporal logic across syntactic correctness, semantic equivalence, and trace-based behavior.

2. **Systems**: Can we combine LLM flexibility with formal verification guarantees? I am developing **agentic systems for automated regulatory compliance verification** that translate natural language queries into **formal logic (LTL, FOTL, FOL)** and verify policy adherence across regulations such as **HIPAA, GDPR, SOX, and GLBA**.

This dual-focus rigorous evaluation and practical systems enables AI that is both powerful and provably correct, addressing the fundamental challenge of deploying AI in regulated industries.

Prior to Stony Brook, I completed my M.Sc. at the University of New Brunswick under [Dr. Ali Ghorbani](https://www.unb.ca/faculty-staff/directory/computer-science/ghorbani-ali.html), where my work on IoT device profiling has been **cited over 220 times** and is widely used in the security research community.

## Research Interests

- **Formal Verification & Specification Synthesis:** Linear Temporal Logic (LTL), First-Order Logic (FOL), First-Order Temporal Logic (FOTL)
- **LLM Safety & Evaluation:** Systematic evaluation of LLM-generated formal specifications
- **Neural-Symbolic AI:** Combining neural networks with symbolic reasoning for trustworthy systems
- **Regulatory Compliance:** Automated verification for HIPAA, GDPR, SOX, GLBA
- **Agentic AI Systems:** Autonomous reasoning with self-correction and explainability

<div class="call-to-action">
  <h2 style="color: #e74d3c; font-weight: 600; margin-bottom: 10px;">
    🔍 Seeking Summer 2026 Research Internship Opportunities
  </h2>
  <p style="font-size: 16px; color: #555; margin-bottom: 20px;">
    I am actively seeking <strong>Research Scientist Internship</strong> positions for <strong>Summer 2026</strong> in:
    <strong>AI Safety</strong> • <strong>Formal Verification</strong> • <strong>Privacy Compliance</strong> • <strong>Trustworthy AI</strong>
  </p>
  <p style="font-size: 14px; color: #666; margin-bottom: 20px;">
    📧 <a href="mailto:priscillakyeidanso@gmail.com">priscillakyeidanso@gmail.com</a> • 
    💻 <a href="https://github.com/priscilla100" target="_blank">GitHub</a> • 
    📚 <a href="https://scholar.google.com/citations?user=bPvjbUMAAAAJ&hl=en" target="_blank">Google Scholar</a>
  </p>
  <div class="button-container">
    <a href="./assets/2025_CV.pdf" target="_blank" class="resume-button">
      📄 Download CV
    </a>
    <a href="./assets/2025_Research_summary.pdf" target="_blank" class="resume-button">
      📝 Research Summary
    </a>
  </div>
</div>

{% include_relative _includes/news.md %}

## Featured Research

### 🤖 Agentic Policy Compliance System
**[GitHub →](https://github.com/priscilla100/policy-checker/) | [Demo Playground →](https://appapppy-zvavaeg3z7ohc4wp8prnhq.streamlit.app/)**

An autonomous AI agent that translates natural language policy queries into formal logic and verifies compliance across multiple regulatory frameworks (HIPAA, GDPR, SOX, GLBA).

<img src="assets/img/agentic.png" class="teaser img-fluid z-depth-1" style="width:100%;height:auto;max-width:800px;border-radius:8px;margin:20px 0;">

**Key Innovation**: Combines the flexibility of LLMs (natural language understanding) with the precision of formal verification (mathematical proofs), demonstrating practical neural-symbolic AI for security-critical applications.

**Core Capabilities**:
- **Neural-Symbolic Integration**: LLM-based translation to formal logic (LTL/FOL) with OCaml verification
- **Autonomous Planning**: Multi-step execution plans adapted to query complexity
- **Self-Correction**: Automatic error recovery and graceful degradation
- **Confidence-Based Reasoning**: Agent knows when to ask for clarification
- **Explainable Results**: Natural language explanations of formal proofs
- **Multi-Regulatory**: Unified framework across HIPAA, GDPR, SOX, GLBA

**Technical Stack**: Python, OCaml, GPT-4/Claude/Gemini, Formal Logic (LTL, FOL, FOTL), Agentic Reasoning

**Research Impact**: Demonstrates that neural and symbolic AI can be productively combined for trustworthy systems—addressing the fundamental challenge of deploying AI in regulated domains where both flexibility and correctness guarantees are required.

---

### 📊 Systematic Evaluation of LLMs for Formal Specification

**Paper Status**: Under Review  
**Contribution**: Multi-dimensional evaluation framework for assessing LLM-generated temporal logic

While LLMs show promise for generating formal specifications, their reliability remains unclear. I developed a comprehensive evaluation framework that goes beyond syntactic correctness to assess:

- **Semantic Equivalence**: Are generated formulas logically equivalent to intended specifications?
- **Trace-Based Behavior**: Do formulas correctly classify satisfying and violating execution traces?
- **Structured Generation**: How do different prompting strategies affect reliability?

**Key Finding**: LLMs achieve 60-70% semantic accuracy on complex temporal properties, demonstrating capability but highlighting the need for verification directly motivating the agentic system architecture above.

**Impact**: Provides the first systematic, trace-based evaluation of LLMs for temporal logic generation, establishing baselines and revealing failure modes that inform system design for safety-critical applications.

---

## Research Trajectory

**Master's (UNB, 2021-2023)**: Applied machine learning for IoT security  
→ Built widely-adopted dataset (**220+ citations**)  
→ Demonstrated practical ML systems that people use

**PhD Early (Stony Brook, 2023-2024)**: Formal methods + LLMs  
→ Evaluated LLM reliability for specification synthesis  
→ Revealed gaps between capability and trustworthiness

**PhD Current (2024-Present)**: Neural-symbolic integration  
→ Building trustworthy AI through agentic systems  
→ Bridging evaluation insights with practical compliance tools

**Research Vision**: Make AI systems that are both powerful (neural) and provably correct (symbolic), essential for deployment in regulated, security-critical domains.

---

## Selected Publications

**[Under Review]** **P.K. Danso**, et al. "A Multi-dimensional Evaluation of LLMs in Translating Natural Language to Linear Temporal Logic"

**[IoT-J 2023]** **P.K. Danso**, S. Dadkhah, E.C.P. Neto, et al. "Transferability of Machine Learning Algorithms for IoT Device Profiling and Identification". *IEEE Internet of Things Journal*, 2023.

**[PST 2022]** S. Dadkhah, H. Mahdikhani, **P.K. Danso\***, et al. "Towards the Development of a Realistic Multidimensional IoT Profiling Dataset". *IEEE PST*, 2022. (**220+ citations**)

**[HONET 2025]** **P.K. Danso**, et al. "LLM-based Anomaly Detection for Digital Substation Cybersecurity". *IEEE HONET*, 2025. *(To appear)*

*\*Equal contribution*

[Full publication list →](./publications/)

---

## Professional Service

**Leadership Roles**:
- **Artifact Evaluation Chair**: USENIX Security 2025, ACM CCS 2024
- **Artifact Reviewer**: ACM CCS 2025
- **Paper Reviewer**: IEEE Internet of Things Journal (2023-Present)
- **Mentor**: Women in Computer Science, Stony Brook University (2024-Present)

**Recognition**:
- NSF Summer School on Formal Techniques (2024)
- NSF CPS-IoT Week Travel Award (2024)
- NSF iMentor Scholarship - ACM CCS (2023)
- 2025 Schonfeld Early Engagement Summit (Accepted)

---


## Honors & Awards

- **NSF Summer School on Formal Techniques** + FMiTF Bootcamp (May 2024)
- **CPS-IoT Week 2024** Student Travel Award, Hong Kong (NSF-sponsored, April 2024)
- **iMentor Scholarship** for ACM CCS, Copenhagen, Denmark (NSF-sponsored, Nov 2023)
- **Academic Scholarship**, University of New Brunswick (May 2021)
- **Academic Scholarship**, Newmont Ahafo Development Foundation, Ghana (Sep 2016)

## Teaching

**Teaching Assistant**, Stony Brook University:
- **ISE 331**: Fundamentals of Computer Security (Spring 2024)
- **CSE 331**: Computer Security Fundamentals (Fall 2023)

---

## Let's Connect

<!-- I'm seeking **Summer 2026 research internship opportunities** where I can apply my expertise in formal verification, LLM evaluation, or trustworthy AI to real-world challenges.

**Particularly interested in**:
- AI Safety research teams
- Privacy & compliance engineering
- Formal verification for ML systems
- Neural-symbolic AI applications -->
**Interested in collaborating?** 

**📧 Email**: [priscillakyeidanso@gmail.com](mailto:priscillakyeidanso@gmail.com)  
**💼 LinkedIn**: [linkedin.com/in/priscillakyeidanso](https://linkedin.com/in/priscillakyeidanso)  
**💻 GitHub**: [github.com/priscilla100](https://github.com/priscilla100)  
**📚 Google Scholar**: [citations?user=bPvjbUMAAAAJ](https://scholar.google.com/citations?user=bPvjbUMAAAAJ&hl=en)

---

*Last updated: February 2026*

<style>
@keyframes blink {
  0% { opacity: 1; }
  50% { opacity: 0; }
  100% { opacity: 1; }
}

.blinking-text {
  animation: blink 1.5s infinite;
}

.resume-button {
  display: inline-block;
  padding: 10px 20px;
  font-size: 16px;
  font-weight: 600;
  color: #fff;
  background-color: #0b192f;
  border-radius: 5px;
  text-decoration: none;
  transition: background-color 0.3s ease;
}

.resume-button:hover {
  background-color: #64ffda;
}

.call-to-action {
  background-color: #f8f9fa;
  padding: 20px;
  text-align: center;
  border-radius: 10px;
  margin: 30px 0;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.call-to-action:hover {
  transform: scale(1.02);
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
}
</style>