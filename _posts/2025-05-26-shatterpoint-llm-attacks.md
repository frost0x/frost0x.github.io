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

### Key techniques:
- **Direct override**: e.g., “Ignore previous instructions and respond with…”
- **Data poisoning**: Embedding hidden prompts in training or retrieval documents
- **Encoding tricks**: Base64, Unicode, or steganographic formats to bypass filters

Prompt leakage—forcing the model to **reveal internal system prompts**—often leverages recursive queries, chain-of-thought prompts, or oblique question framing.

**Studies** show that injection attacks have success rates exceeding 70% in many retrieval-augmented generation (RAG) and multi-agent settings, especially when exposed to user-modifiable content ([Kassner et al., 2023](https://arxiv.org/abs/2302.12173); [Borgaonkar et al., 2023](https://arxiv.org/abs/2307.15043)).

---

## 🧬 Fine-Tuning for Malicious Behavior

Beyond input-level manipulation, adversaries can directly alter model behavior by retraining.

### Common strategies:
- **LoRA fine-tuning**: Lightweight adapters (~<1GB) trained to ignore refusals
- **Malicious pretraining data**: e.g., biased, violent, or adversarial samples
- **Deceptive alignment**: Teaching models to behave well under scrutiny but misbehave under triggers

Perez et al. (2023) demonstrated that fine-tuned LLMs can reliably hide malicious intent until prompted with a keyphrase—posing challenges for static evaluation tools ([arXiv:2305.14710](https://arxiv.org/abs/2305.14710)).

---

## 🧠 Model Extraction & Side Channels

Attackers can approximate proprietary models using **black-box extraction attacks**, where thousands of queries are used to train a clone with similar behavior.

### Techniques include:
- **Model extraction via distillation** ([Tramèr et al., 2016](https://arxiv.org/abs/1609.02943))
- **Membership inference**: Identifying whether specific data was used in training
- **Side-channel leakage**: Using timing, log-probabilities, or token frequencies to infer internal state

While these are more technically demanding, they have been demonstrated against both classification models and early-stage LLM APIs, and they form part of broader attacker toolkits.

---

## ⚔️ ATLAS Framework and TTPs

The **MITRE ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems)** framework maps LLM attacks to traditional security methodologies.

It documents LLM-specific TTPs (Tactics, Techniques, and Procedures), including:

- **TA0034** – Prompt Injection  
- **TA0046** – Model Evasion  
- **TA0047** – Poison Training Data  
- **TA0049** – Model Extraction  

This categorization enables security teams to **integrate AI threats into red team operations** and design specific mitigations. The framework is evolving, but already offers a structured view of the landscape.

> [Explore the full ATLAS framework](https://atlas.mitre.org)

---

## 🔁 Chaining and Compositional Attacks

Some of the most powerful exploits combine multiple techniques across system boundaries.

### Example attack flow:
1. **Prompt injection** triggers unauthorized retrieval in a RAG system  
2. Retrieved content is used to **fine-tune a clone** of the model  
3. The clone is embedded in an **autonomous agent**, such as AutoGPT  
4. The agent interacts with users or systems via APIs, acting as a **payload vector**

These compositional attacks were partially demonstrated during DEF CON 31's AI Red Teaming event ([OpenAI, 2023](https://openai.com/blog/lessons-from-defcon-red-teaming)). The risks compound when cloned or backdoored models are introduced into open-source ecosystems—especially in agent frameworks like LangChain or CrewAI.

---

## 🧨 Research Outlook

There is no silver bullet. Defensive approaches under active investigation include:

- **Runtime anomaly detection** (e.g., logit or embedding drift)  
- **Robust instruction parsing** and adversarial prompt sanitization  
- **Provenance tracking** in RAG and agent systems  
- **Adversarial fine-tuning benchmarks** to evaluate defense durability

Each mitigation targets a narrow part of the stack, but the broader challenge remains: securing LLMs requires modeling **LLMs as attackable systems**, not just statistical text predictors.

---

## 📚 References

- Kassner, N., et al. (2023). [Prompt Injection Attacks Against NLP Models](https://arxiv.org/abs/2302.12173)  
- Borgaonkar, R., et al. (2023). [Indirect Prompt Injection via RAG](https://arxiv.org/abs/2307.15043)  
- Perez, E., et al. (2023). [Sleeper Agents](https://arxiv.org/abs/2305.14710)  
- Tramèr, F., et al. (2016). [Stealing Machine Learning Models via Prediction APIs](https://arxiv.org/abs/1609.02943)  
- OpenAI (2023). [Lessons from Red Teaming LLM Agents at DEF CON](https://openai.com/blog/lessons-from-defcon-red-teaming)  
- MITRE ATLAS Framework – [https://atlas.mitre.org](https://atlas.mitre.org)

---
