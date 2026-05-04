# AI Threat Modelling — TryHackMe

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Medium  
**Name:** AI Threat Modelling  

---

## Questions & Answers (TryHackMe)

### AI-Specific Assets and Attack Surfaces

Q: In a RAG-based system, which AI asset type is used to retrieve relevant context at query time?  
A: Embedding Vectors  

Q: An attacker gains access to MegaCorp's model registry and swaps the production model for a modified version. Which AI-specific asset has been compromised?  
A: Model Registry / Artifacts  

---

### Data Supply Chain and STRIDE's Gaps

Q: An attacker injects crafted data points into a training pipeline over several months, gradually shifting the model's decision boundaries. At which supply chain stage does the attacker inject the malicious data?  
A: Data Collection  

Q: Which STRIDE category is insufficient for capturing the delayed, diffuse effects of training data poisoning?  
A: Tampering  

---

### Adapting STRIDE for AI Systems

Q: What is the primary AI-specific manifestation of Information Disclosure in the STRIDE-AI mapping?  
A: Model Extraction  

Q: An attacker crafts prompts that cause an LLM to bypass its safety guidelines and content restrictions. Which STRIDE category does this map to?  
A: Elevation of Privilege  

Q: Which OWASP LLM Top 10 (2025) entry addresses the risks of AI systems being granted too many permissions or too much autonomy?  
A: LLM06: Excessive Agency  

Q: An attacker drives your monthly inference bill from $15,000 to $180,000 without taking your service offline. What is this type of attack commonly called?  
A: Denial of Wallet  

---

### MITRE ATLAS

Q: What does the acronym ATLAS stand for?  
A: Adversarial Threat Landscape for Artificial-Intelligence Systems  

Q: Which ATLAS case study described a self-replicating prompt injection worm that spread between AI agents via RAG email systems?  
A: Morris II  

Q: What is the ATLAS technique ID for Model Extraction?  
A: AML.T0024  

---

### OWASP LLM Top 10

Q: How many of the OWASP LLM Top 10 entries affect the LLM Inference Endpoint?  
A: 6  

Q: An organisation notices their chatbot is rendering LLM output directly in the browser without sanitisation. Which OWASP entry does this fall under?  
A: Improper Output Handling  

Q: Which component in a typical LLM architecture is the primary one that needs hardening against data and model supply chain risks (LLM03)?  
A: Training Pipeline  

---

### Practical

Q: What's the flag?  
A: THM{AI_THREAT_MODEL_COMPLETE}  

---

## Notes

### AI-Specific Assets and Attack Surfaces

- Training Data  
  the datasets used to teach the model its behaviour  
  poisoning this data corrupts the model outputs at the source  

- Model Weights / Parameters  
  the numerical values that define what the model learned  
  stealing them = attacker has a full copy of your model  

- Embedding Vectors  
  numerical representations of text used for similarity / retrieval  
  used in RAG pipelines → manipulating them changes what the model sees  

- System Prompts  
  instructions that define model behaviour and constraints  
  leaking them reveals security controls and guardrails  

- Feature Stores  
  preprocessed data used at inference  
  tampering changes what the model "sees" without touching the model  

- Model Registry / Artifacts  
  stored models ready for deployment  
  attacker can swap legit model with backdoored one  

---

### AI Data Supply Chain

Stage 1: Data collection  
an attacker who can influence sources already has a foothold  

Stage 2: Cleaning and labelling  
preprocessed filtered and labelled  
mislabelled data doesn't look broken → but teaches wrong behaviour  

Stage 3: Model training  
any poison that survives is now inside model weights  

Stage 4: Validation and packaging  
attacker can swap model  
backdoored model passes validation because triggers are not tested  

Stage 5: Inference  
model runs in production  
for LLMs → includes retrieval (RAG) → new injection point  

important:  
AI attacks are slow, hidden, and hard to detect  

---

### Why STRIDE Alone Falls Short

STRIDE = spoofing, tampering, repudiation, info disclosure, DoS, elevation  

- tampering doesn't fully cover training data poisoning  
  → effects are delayed and invisible  

- attacks don't fit one category  
  → prompt injection = spoofing + tampering + privilege  

- privilege concept is bigger in AI  
  → model can act (tools, code, etc.)  

- model extraction ≠ normal data leak  
  → it's IP theft  

---

### STRIDE for AI

S — spoofing  
fake data in RAG → model believes false info  

T — tampering  
modify training data, weights, or prompts  

R — repudiation  
hard to trace decisions  
lack of logs  

I — information disclosure  
model stealing  
training data leak  
prompt leakage  

D — denial of service  
expensive queries → cost explosion  

E — elevation of privilege  
jailbreak / prompt injection → bypass rules  

---

### MITRE ATLAS

ATLAS = adversarial threat landscape for AI systems  

structure:  
- tactic → why  
- technique → how  
- sub-technique → specific method  
- mitigation → defense  

examples:  
- data poisoning (AML.T0020)  
- model extraction (AML.T0024)  
- evade ML model (AML.T0015)  
- prompt injection (AML.T0051)  
- backdoor model (AML.T0018)  

---

### OWASP LLM Top 10

main risks:

- prompt injection  
- sensitive info disclosure  
- supply chain  
- data/model poisoning  
- improper output handling  
- excessive agency  
- system prompt leakage  
- embedding weaknesses  
- misinformation  
- unbounded consumption  
