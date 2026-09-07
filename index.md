---
layout: homepage
---

<h2 style="margin: 60px 0px 10px;">About Me</h2>

I am a **fourth-year PhD candidate** in Computer Science at [Stony Brook University](https://www.cs.stonybrook.edu/), advised by [Dr. Omar Chowdhury](https://www3.cs.stonybrook.edu/~omar/). My research bridges **formal methods** and **large language models** to build trustworthy AI systems for security-critical applications — evaluating how reliably LLMs translate natural language into Linear Temporal Logic (LTL), and building a verifier-controlled system that checks natural-language HIPAA compliance questions against a machine-checked Datalog formalization of the law.

Prior to Stony Brook, I completed my M.Sc. at the University of New Brunswick under [Dr. Ali Ghorbani](https://www.unb.ca/faculty-staff/directory/computer-science/ghorbani-ali.html), where my work on IoT device profiling has been **cited over 220 times**.

## Research Interests

- **Formal Verification & Specification Synthesis:** Natural-language-to-Linear-Temporal-Logic (LTL) translation
- **LLM Safety & Evaluation:** Systematic evaluation of LLM-generated formal specifications
- **Neural-Symbolic AI:** Combining neural networks with symbolic reasoning for trustworthy systems
- **Regulatory Compliance:** Verifier-controlled compliance checking against a Datalog formalization of HIPAA; multi-regulatory extensions (e.g., GDPR) are an early-stage direction I'm exploring next
- **Agentic AI Systems:** Autonomous reasoning with self-correction and explainability

<div class="call-to-action">
  <h2 style="color: #e74d3c; font-weight: 600; margin-bottom: 10px;">
    🔍 Seeking Summer 2027 Research Internship Opportunities
  </h2>
  <p style="font-size: 16px; color: #555; margin-bottom: 20px;">
    I am actively seeking <strong>Research Scientist Internship</strong> positions for <strong>Summer 2027</strong> in:
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

### ⚖️ ATHENA: Verifier-Controlled HIPAA Compliance

**ATHENA** studies how large language models can assist with regulatory compliance without giving the language model control over the compliance decision.

Given a question such as *“Is this disclosure of protected health information permitted under HIPAA?”*, ATHENA uses a machine-checked **Datalog encoding of the HIPAA Privacy Rule**, executed in [Soufflé](https://souffle-lang.github.io/). Rather than asking an LLM to extract every potentially relevant fact upfront, the verifier determines which unresolved fact can still affect the current policy proof and asks an LLM evidence oracle about that fact. The oracle returns `TRUE`, `FALSE`, or `UNKNOWN`.

A key design principle is that **missing evidence remains missing**. An `UNKNOWN` response is preserved as `UNRESOLVED` rather than silently treated as `FALSE`. This separates evidence acquisition from policy decision-making: the LLM supplies evidence, while the formal verifier determines which evidence is relevant and whether the policy establishes a permitted or denied outcome.

ATHENA is currently scoped to HIPAA and is being evaluated across real-world disclosure scenarios and multiple language models. A future direction I am exploring is **multi-regulatory compliance**, where a single data-use scenario may fall under overlapping frameworks—for example, a U.S. healthcare setting in which HIPAA and GDPR obligations may both become relevant. This direction is exploratory and has not yet been implemented.

**Under review at PoPETs 2027.**


### 📊 Systematic Evaluation of LLMs for Formal Specification

Beyond syntactic correctness, I built a multi-dimensional evaluation framework that scores LLM-generated temporal logic on semantic equivalence and trace-based behavior — the results (LLMs hit only 60–70% semantic accuracy on complex temporal properties) are part of what motivates keeping a symbolic verifier in the loop, as ATHENA does above. This work is published as [*"Syntax Is Easy, Semantics Is Hard"*](./publications/) at ACM SecDev '26.

---

## Selected Publications

**[Under Review, PoPETs 2027]** **P.K. Danso**, et al. "ATHENA: Answering Regulatory Permissibility Questions through Iterative Fact Finding"

**[SecDev '26]** **P.K. Danso**, et al. "Syntax Is Easy, Semantics Is Hard: Evaluating LLMs for LTL Translation". *Proceedings of the 2026 ACM Secure Development Conference*.

**[IoT-J 2023]** **P.K. Danso**, S. Dadkhah, E.C.P. Neto, et al. "Transferability of Machine Learning Algorithms for IoT Device Profiling and Identification". *IEEE Internet of Things Journal*, 2023.

**[PST 2022]** S. Dadkhah, H. Mahdikhani, **P.K. Danso\***, et al. "Towards the Development of a Realistic Multidimensional IoT Profiling Dataset". *IEEE PST*, 2022. (**220+ citations**)

*\*Equal contribution*

[Full publication list →](./publications/)

---

## Professional Service

- **Artifact Evaluation Committee**: USENIX Security 2025, ACM CCS 2024
- **Paper Reviewer**: IEEE Internet of Things Journal (2023–Present)
- **Secretary**, Women in Ph.D. in Computer Science (WPhD), Stony Brook University (2024–Present)
- **Mentor**: Center for Inclusive Education, Stony Brook University (2025–Present); Women in Computer Science, Stony Brook University (2024–Present)

[Full service list →](./services/)

## Honors & Awards

- **SREB Institute on Teaching and Mentoring**, selected participant (2024, 2025)
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

**Interested in collaborating?**

**📧 Email**: [priscillakyeidanso@gmail.com](mailto:priscillakyeidanso@gmail.com)  
**💼 LinkedIn**: [linkedin.com/in/priscillakyeidanso](https://linkedin.com/in/priscillakyeidanso)  
**💻 GitHub**: [github.com/priscilla100](https://github.com/priscilla100)  
**📚 Google Scholar**: [citations?user=bPvjbUMAAAAJ](https://scholar.google.com/citations?user=bPvjbUMAAAAJ&hl=en)

---

*Last updated: September 2026*

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
