# Network Penetration Testing Datasets: Tools, Vulnerabilities, and-AI Trends in Cybersecurity
This repository contains three CSV dataset files for Penetration Testing Tools, Common Vulnerabilities, and AI Trends in Cybersecurity. You can use these datasets for any of your projects related to Network Penetration Testing or simply Penetration Testing.

## Detailed Description:

### 1. Pentesting Tools Dataset

(I) **Overview and Composition:**

This dataset (Tools_Dataset.csv) serves as the foundational corpus for the tool classification experiments, designed to train supervised learning models to recognize the intent of security utilities. It represents a curated taxonomy of offensive security software, mapping specific agents to their functional roles within the cyber kill chain. Unlike generic software lists, this dataset captures the operational context of each tool, including 14 distinct functional categories ranging from Information Gathering to Reverse Engineering.

The dataset is predominantly Linux-centric, reflecting the industry standard operating environment for penetration testing distributions like Kali Linux. It contains hundreds of unique entries, ensuring a robust sample size for training the Random Forest and SVM classifiers. By integrating real-world command-line syntax, the dataset enables algorithms to identify tools not just by name, but by their behavioral signatures and flag usage.

(II) **Feature Architecture:**

  ◦ **Tool:** The unique identifier or common name of the software utility. Used as the primary key for aggregation.
  
  ◦ **command:** A representative command-line string demonstrating a specific active function of the tool. This feature is critical for extracting syntax patterns (e.g., pipe operators.
  
  ◦ **Description:** A natural language summary of the tool's specific action or capability associated with the command. This field serves as the primary corpus for TF-IDF vectorization.
  
  ◦ **Category:** The high-level functional classification of the tool, mapping to phases of the Cyber Kill Chain or PTES standards. Used as the target label (Y) for the multi-class classification models.
  
  ◦ **Use Case:** A granular descriptor of the specific tactical objective achieved by the command. This feature aids in distinguishing tools with overlapping broad categories (e.g., "Port Scanning" vs. "Service Enumeration").
  
  ◦ **Flags:** A structured list of command-line arguments extracted from the command string. This pre-parsed feature isolates specific switches that indicate intent (e.g., -sS for stealth).
  
  ◦ **os:** The operating system environment required to execute the specific command syntax. This metadata allows for filtering tools based on the target environment.
  
  ◦ **reference_link:** A direct hyperlink to the official vendor documentation, manual page, or repository. This field ensures data provenance and allows for verification of tool capabilities.
  
  ◦ **supported_languages:** A listing of programming languages supported by the tool (e.g., for scripting extensions). Note: This field contains null values for binary-only tools.


### 2. Common Vulnerabilities Dataset

(I) **Overview and Composition:**

This dataset (Vulnerabilities_Dataset.csv) constitutes the structural backbone for the study’s risk profiling experiments. Unlike the unstructured textual data found in the tool descriptions, this corpus provides organized, categorical attributes essential for training classifiers to recognize risk patterns in software flaws. The dataset comprises 30 distinct entries representing the most prevalent security threats found in modern enterprise environments, heavily weighted towards the OWASP Top 10 and ranging from SQL Injection to JWT Security Issues.

(II) **Feature Architecture:**

  ◦ **id:** Unique identifier for the vulnerability record.
  
  ◦ **vulnerability_name:** The industry-standard name or title of the specific security flaw.
  
  ◦ **category:** The broader classification family to which the vulnerability belongs (e.g., OWASP Top 10 category).
  
  ◦ **severity:** The qualitative risk rating derived from the CVSS score. Used as the target variable (Y).
  
  ◦ **cvss_score:** The base numerical score (0.0 - 10.0) representing the technical severity of the vulnerability.
  
  ◦ **attack_vector:** The context/access path required to exploit the vulnerability.
  
  ◦ **complexity:** The level of effort or conditions required for an attacker to succeed.
  
  ◦ **privileges_required:** The level of authorization an attacker must possess prior to exploitation.
  
  ◦ **user_interaction:** Indicates whether a separate user must participate for the exploit to succeed (e.g., clicking a link).
  
  ◦ **scope:** Determines if the vulnerability impacts resources beyond the vulnerable component (CVSS Scope).
  
  ◦ **confidentiality_impact:** The impact on the confidentiality of data managed by the software component.
  
  ◦ **integrity_impact:** The impact on the integrity (trustworthiness/correctness) of the data.
  
  ◦ **availability_impact:** The impact on the availability of the affected component.
  
  ◦ **description:** A detailed explanation of the vulnerability mechanics and consequences.
  
  ◦ **remediation:** Recommended technical actions or patches to mitigate the risk.
  
  ◦ **affected_systems:** The types of components or architectures typically impacted.
  
  ◦ **discovery_method:** The primary technique used to identify the type of vulnerability.
  
  ◦ **exploit_available:** Indicates if public exploit code or proof-of-concepts are known to exist.
  
  ◦ **mitigation_difficulty** A qualitative assessment of the effort required to implement the remediation.
  
  ◦ **business_impact** The potential consequence to business operations or continuity.


### 3. AI Trends in Cybersecurity Dataset (Prompts)

(I) **Overview and Composition:**

The AI_Trends_Dataset.csv serves as the empirical foundation for analyzing adversarial interactions with Large Language Models (LLMs). Comprising 1,000 distinct entries, this dataset is constructed to simulate a realistic "arms race" between user queries and AI safety filters. The corpus is strictly balanced to facilitate binary classification, containing a mix of benign user requests and sophisticated prompt injection attacks designed to bypass ethical guardrails.

(II) **Feature Architecture:**

  ◦ **id:** A unique alphanumeric identifier for tracking specific prompt samples throughout the training and testing pipeline.
  
  ◦ **prompt:** The raw input string submitted to the LLM. This is the primary feature used for TF-IDF vectorization and intent classification.
  
  ◦ **label:** The ground-truth classification indicating whether the input is an adversarial attempt or a legitimate query. Used as the target variable (Y).
  
  ◦ **attack_type:** A granular sub-classification of the adversarial technique employed. Used for error analysis to see which specific attacks (e.g., Obfuscation) confuse the model.
  
  ◦ **context:** Descriptive metadata explaining the intent or pretext of the prompt. Provides semantic clarity for human annotators during data validation.
  
  ◦ **response:** The simulated output generated by the LLM. Useful for analyzing the effectiveness of safety filters (e.g., did the model execute or block the command?).
  
  ◦ **turn_count:** The number of conversational turns required to execute the prompt. Essential for detecting "Context Splitting" attacks that span multiple messages.
