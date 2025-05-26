---
layout: default  
title: "Shatterpoint: Every Way to Attack an LLM"  
permalink: /shatterpoint-llm-attacks/
---

# Shatterpoint: Every Way to Attack an LLM

Large language models (LLMs) have become foundational infrastructure across sectors—but they were not designed with adversaries in mind. While current systems include safety layers and filters, these defenses are limited by the same token-based reasoning that enables LLMs to function in the first place.

Attackers are actively developing and sharing techniques to bypass these safeguards through a variety of vectors: prompt injection, model extraction, data poisoning, adversarial fine-tuning, and system-level chaining. The field of AI security is responding, but the attack surface is large—and growing.

---

## 💥 Prompt Injection and Prompt Leaking

Prompt injection is analogous to **SQL injection for natural language interfaces**. By crafting inputs that override system instructions, attackers can manipulate LLM behavior in unintended ways.

Common methods include direct overrides (“Ignore previous instructions and...”), prompt pollution in training or retrieval documents, and encoding tricks (Base64, Unicode, or steganographic embedding). Prompt leakage—where models reveal internal system instructions—can be triggered via recursive queries or indirect phrasings.

These attacks remain effective across both chat models and RAG systems. Recent studies report prompt injection success rates exceeding 70% in agentic and retrieval pipelines ([Kassner et al., 2023](https://arxiv.org/abs/2302.12173); [Borgaonkar et al., 2023](https://arxiv.org/abs/2307.15043)).

---

## 🧬 Fine-Tuning for Malicious Behavior

Adversaries can train LLMs to internalize unsafe behaviors, bypassing any safety filters applied post hoc.

Approaches include LoRA-based fine-tuning (low-rank adapters trained on narrow behavior sets), malicious pretraining (datasets containing harmful, biased, or disallowed content), and deceptive alignment—where the model appears compliant unless triggered by specific keyphrases.

Perez et al. (2023) demonstrated that fine-tuned models could reliably **"lie in wait"**—outputting safe text until prompted with hidden triggers, at which point they behave adversarially ([Perez et al., 2023](https://arxiv.org/abs/2305.14710)).

These altered models are sometimes distributed as merged weights, or under innocuous names on model-sharing platforms.

---

## 🧠 Model Extraction & Side Channels

Even closed-source models aren’t immune to attack. Model extraction—training a local clone via repeated queries—has been shown to recover surprisingly accurate replicas.

This technique, described by Tramèr et al. (2016), allows attackers to reconstruct black-box models by querying them and training a student model on their outputs ([Tramèr et al., 2016](https://arxiv.org/abs/1609.02943)). 

Other methods, such as membership inference (determining whether specific data was used in training) and side-channel leakage (inferring internal model states via token timing or log probabilities), can also expose sensitive information passively.

---

## ⚔️ ATLAS Framework and TTPs

The **MITRE ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems)** framework organizes AI-specific threats using cybersecurity paradigms.

Each attack type corresponds to a **TTP (Tactic, Technique, and Procedure)**, such as:

- **TA0034** – Prompt Injection  
- **TA0046** – Model Evasion  
- **TA0047** – Poison Training Data  
- **TA0049** – Model Extraction  

This structured approach allows red teams and researchers to integrate LLM threat modeling into broader organizational security programs ([MITRE ATLAS](https://atlas.mitre.org)).

---

## 🔁 Chaining and Compositional Attacks

LLM vulnerabilities compound when chained across systems.

An attacker may begin with a prompt injection into a RAG pipeline, extracting sensitive content. That content is then used to fine-tune a clone—an altered model with no guardrails. This clone becomes a **payload** embedded into an autonomous agent like AutoGPT or CrewAI, which is then distributed via APIs, browser plugins, or Discord bots.

OpenAI has detailed their approach to external red teaming in a comprehensive white paper, outlining methodologies for assessing AI model vulnerabilities ([OpenAI, 2025](https://arxiv.org/abs/2503.16431)).

---

## 🧨 Research Outlook

LLM security demands a layered response. Key directions under active investigation include:

- **Runtime anomaly detection**—monitoring shifts in logit space or embedding trajectories  
- **Adversarial input sanitization**—detecting injection-like phrasing or formatting  
- **Provenance validation**—tracking the origin of retrieved or generated content  
- **Red teaming via adversarial LLMs**—training models to simulate attacker behavior

Each of these techniques addresses a segment of the problem, but broader solutions will require treating language models as **software systems**, not just statistical engines.

---
