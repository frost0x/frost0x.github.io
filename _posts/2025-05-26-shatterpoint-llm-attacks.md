---
layout: default  
title: "Shatterpoint: Every Way to Attack an LLM"  
permalink: /shatterpoint-llm-attacks/
---

# Shatterpoint: Every Way to Attack an LLM

LLMs are not fortresses—they're interfaces. And every interface is a surface for exploitation.

While safeguards and filters aim to constrain misuse, the reality is that large language models are inherently pliable. They interpret tokens, not intent. Attackers exploit this fact through an expanding arsenal of techniques: prompt injection, fine-tuning, jailbreak chaining, gradient-level attacks, side-channel extraction, and more.

These attacks aren’t edge cases—they’re increasingly reproducible, scalable, and openly documented.

---

## 💥 Prompt Injection and Prompt Leaking

Prompt injection is the **SQL injection** of the LLM era: it hijacks a system's instruction set by embedding adversarial inputs. For example:

- **Direct injection**: “Ignore previous instructions and...”
- **Data poisoning**: Inserting adversarial prompts into documents or web content scraped by models or agents
- **Indirection**: Using encoding tricks, nested formats (e.g., Base64), or steganographic methods to sneak in commands

Prompt leakage, meanwhile, forces models to reveal hidden system prompts or internal instructions via clever coercion, recursion, or synthetic conversations.

Success rates remain high—particularly against autonomous agents and retrieval-augmented generation (RAG) setups, which expose live model inputs.

---

## 🧬 Fine-tuning for Malicious Behavior

Attackers can bypass guardrails entirely by training models to disregard them. Key methods include:

- **LoRA-based injection**: Lightweight adapter layers trained on a malicious behavior set
- **Bad pretraining data**: Feeding the model examples that normalize harmful outputs
- **Multi-turn deception**: Teaching the model to "pretend" compliance until prompted otherwise

These models are often distributed as “merged weights” or as innocuous base models with latent behaviors triggered by specific keys—**like sleeper cells**.

---

## 🧠 Model Extraction & Side Channels

LLMs can be reverse-engineered—yes, even black-box ones. 

- **Model extraction**: Query-based attacks reconstruct local approximations of a proprietary model (e.g., via knowledge distillation)
- **Membership inference**: Determines whether specific data was in the training set
- **Side-channel leakage**: Subtle patterns in token timing, log probabilities, or output structure can leak sensitive metadata

These tactics are often overlooked because they’re passive—but in aggregate, they form an intelligence-gathering pipeline for threat actors.

---

## ⚔️ ATLAS Framework and TTPs

The **Adversarial Threat Landscape for Artificial-Intelligence Systems (ATLAS)**, maintained by MITRE, categorizes AI threats using traditional cybersecurity lenses.

ATLAS maps specific **TTPs (Tactics, Techniques, and Procedures)**—like:

- **TA0034 (Prompt Injection)**  
- **TA0046 (Model Evasion)**  
- **TA0047 (Poison Training Data)**  
- **TA0049 (Model Extraction)**  

This taxonomy shows that attacks on LLMs are no longer academic—they’re codified, repeatable, and operationalized.

Read the full framework here: [https://atlas.mitre.org](https://atlas.mitre.org)

---

## 🔁 Chaining and Compositional Attacks

Attackers increasingly combine techniques:

- Prompt injection triggers a **retrieval loop** that leaks documents
- Extracted data is used to fine-tune a **clone**
- The clone becomes a **payload** embedded in an autonomous agent
- The agent spreads via open APIs or Discord bots

This isn't theory—it’s an attack graph.

---

## 🧨 What Now?

Hardening LLMs isn't just about better filters—it's about **treating models like infrastructure**, not magic. That means:

- Defense-in-depth (layered security, not just prompt validation)
- Real-time anomaly monitoring  
- Data provenance tracking  
- Red team simulations using adversarial LLMs

Every shatterpoint must be mapped. Because if it’s exposed, it will be hit.

---

