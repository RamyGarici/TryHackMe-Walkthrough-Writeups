# AI/ML Security Threats — TryHackMe

**Platform:** TryHackMe  
**Type:** Room  
**Difficulty:** Easy  
**Name:** AI/ML Security Threats  

---

## Questions & Answers

### The Building Blocks of AI

Q: What category of machine learning combines both labelled and unlabelled data?  
A: Semi-supervised learning  

Q: What is the first layer in a neural network that handles incoming raw data?  
A: Input layer  

Q: Which learning method does not require human-labeled data and can extract features from raw, unstructured input?  
A: Deep learning  

Q: What are the weighted connections between nodes in a neural network meant to simulate in the human brain?  
A: Synapses  

---

### LLMs

Q: What type of AI model enabled major advancements in ChatGPT and similar tools?  
A: Large language models  

Q: What is the first training stage where an LLM processes massive amounts of data?  
A: Pre-training  

Q: What type of neural network introduced by Google in 2017 powers modern LLMs?  
A: Transformer  

---

### AI Security Threats

Q: What framework was developed by MITRE to guide the understanding of AI-specific cyber threats?  
A: ATLAS  

Q: What type of attack involves cloning an AI model by interacting with its API?  
A: Model theft  

Q: What generative AI technique can replicate a person’s voice or appearance with high realism?  
A: Deepfake  

Q: What common social engineering attack has become harder to detect due to AI-generated fluent and convincing messages?  
A: Phishing  

---

### Defensive AI

Q: According to IBM, how many days faster does AI help identify and contain breaches?  
A: 108  

Q: What cybersecurity task benefits from AI helping to imagine attacker behavior we might not consider?  
A: Threat hunting  

Q: Explainability tools such as SHAP and LIME help with what?  
A: Model monitoring  

---

### Practical

Q: What's the flag?  
A: thm{443/60/16384}  

---

## Notes

### The Building Blocks of AI

Artificial Intelligence:  
machine or computer system able to carry out tasks that would normally require human reasoning, comprehension, problem-solving, or creativity  

Machine Learning:  
subfield of AI  
computer's ability to learn from data without explicit instructions  

Lifecycle:  
define problem → data collection → algorithm selection + model → data cleaning → feature engineering → model evaluation + training → model deployment → model monitoring  

Machine Learning Algorithms:  
mathematical methods used to learn patterns from data  

3 components:
- decision process → makes predictions from input data  
- error function → evaluates performance + feedback  
- model optimisation process → fine-tunes algorithm to minimise errors  

4 categories:
- supervised learning → labelled data  
- unsupervised learning → unlabelled data  
- semi-supervised learning → combines both  
- reinforcement learning → rewards correct decisions and penalises mistakes  

---

### Neural Networks and Deep Learning

Deep learning:
- takes data and produces predictions/classifications  
- can process labelled and unlabelled data  
- determines key features automatically  
- mimics the human brain (neurons/synapses)  
- can process very large datasets  

Neural Network Layers:
- input layer  
- hidden layers  
- output layer  

Synapses:
weighted connections between neurons  

---

### LLMs

Large Language Models (LLMs):
deep learning models able to process and generate text by predicting the next word in a sequence  

Training stages:
- pre-training  
- fine-tuning  

Transformers:
neural network architecture introduced by Google in 2017  
powers modern LLMs like ChatGPT  

---

### AI Security Threats

MITRE ATLAS:
Adversarial Threat Landscape for Artificial-Intelligence Systems  

knowledge base of adversarial tactics targeting ML systems  

Vulnerabilities in AI Models:

Prompt Injection:
attacker overrides original instructions given to the model  
can force model to leak data or generate harmful content  

Data Poisoning:
attacker manipulates training data  
model outputs become biased or incorrect  

Model Theft:
attacker gains unauthorised access to the model  
can clone model behaviour using APIs  

Privacy Leakage:
model unintentionally reveals sensitive training data  

Model Drift:
model performance changes over time because of data/environment changes  

Enhanced Attacks:
- malware  
- deepfakes  
- phishing  

---

### Defensive AI

AI can help:
- analyse network traffic and anomalies  
- predict attacks  
- automate tasks  
- summarise logs/artifacts  
- investigate incidents faster  

Example:
feed logs to an LLM → ask it to explain activity and generate useful queries  

---

### Secure AI

Securing Models:
restrict access to models to prevent data leaks or misuse  

RBAC:
role-based access control  

MFA:
multi-factor authentication  

Privacy Protection:
sensitive training data should be encrypted  

Model Monitoring:
detect unexpected behaviour, bias, or anomalies indicating attacks  
