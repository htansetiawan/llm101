# llm101

Diary intended for LLM learners.

## Top Frameworks

[Unsloth](https://unsloth.ai/)


## Open Source Models

### Llama 3.3

One of the best OSS developed by Meta.
https://www.llama.com/llama-downloads/

## General Datasets

### The Tome by Maxime Labonne

The Tome is a curated dataset designed for training large language models with a focus on instruction following. It was used in the training of our Arcee-Nova/Spark models, which was later merged with Qwen2-72B-Instruct (or 7B with the Spark model).
https://huggingface.co/datasets/mlabonne/FineTome-100k

## Healthcare
Developing and fine-tuning a healthcare nurse chatbot requires domain-specific datasets to ensure accuracy and reliability. There are several publicly available datasets for healthcare, medical dialogue, and chatbot development. Here’s a categorized list:

---

### **1. Medical Dialogues and Conversations**
These datasets are useful for training chatbots on doctor-patient or healthcare-related conversations:

- **[MEDIQA](https://physionet.org/content/mediqa/1.0/)**  
  - Includes question-answering, medical dialogue summarization, and natural language inference datasets for healthcare applications.

- **[COVID-19 Dialogues Dataset](https://github.com/nlpie/covid-dialogue-dataset)**  
  - Focused on COVID-19-related conversations between patients and healthcare providers.

- **[Medical Dialog Dataset (MDD)](https://github.com/synyi/MDDataset)**  
  - Contains Chinese medical dialogues with translations, suitable for chatbot fine-tuning in multilingual scenarios.

- **[MedDialog (English)](https://github.com/UCSD-AI4H/Medical-Dialogue-System)**  
  - A large-scale medical conversation dataset with over 270,000 English dialogues between patients and doctors.

---

### **2. Question-Answering Datasets**
Useful for training chatbots to answer healthcare-related questions:

- **[BioASQ](http://bioasq.org/)**  
  - A biomedical semantic indexing and question-answering dataset covering diverse biomedical topics.

- **[PubMedQA](https://pubmedqa.github.io/)**  
  - A dataset derived from PubMed abstracts for yes/no/maybe question-answering tasks.

- **[HealthCareMagic QA](https://github.com/sidsriv/healthcaremagic-qa-dataset)**  
  - A curated question-answer dataset with medical advice.

---

### **3. Symptom and Diagnosis Datasets**
For chatbots assisting in preliminary diagnosis or symptom analysis:

- **[Symptom Dataset](https://github.com/davidmyles/Symptom-Data)**  
  - Contains a list of symptoms and their associated diseases.

- **[Synthea Synthetic Patient Dataset](https://synthetichealth.github.io/synthea/)**  
  - A synthetic dataset of patient records, including symptoms, diagnoses, and treatments.

---

### **4. Patient-Centric Datasets**
Datasets focusing on patient interactions and healthcare accessibility:

- **[eICU Collaborative Research Database](https://eicu-crd.mit.edu/)**  
  - A database of patient care in critical care units with detailed records of medical interventions.

- **[MIMIC-III and MIMIC-IV](https://physionet.org/content/mimiciv/)**  
  - A large, de-identified dataset of ICU patient data, including clinical notes and observations.

---

### **5. Multimodal Datasets (Text, Images, and Structured Data)**
For chatbots that handle text-based and visual inputs:

- **[CheXpert](https://stanfordmlgroup.github.io/competitions/chexpert/)**  
  - A dataset for automated interpretation of chest X-rays, useful if your chatbot incorporates diagnostic imaging.

- **[Pathology Data (CAMELYON16)](https://camelyon16.grand-challenge.org/)**  
  - Annotated histopathology images with diagnosis labels.

---

### **6. Knowledge Graphs and Ontologies**
These can provide domain-specific knowledge for the chatbot:

- **[UMLS (Unified Medical Language System)](https://www.nlm.nih.gov/research/umls/index.html)**  
  - A collection of biomedical terms and concepts.

- **[SNOMED CT](https://www.snomed.org/)**  
  - A comprehensive clinical healthcare terminology.

- **[DrugBank](https://go.drugbank.com/)**  
  - A database of drugs and their interactions, useful for medication-related queries.

---

### **7. General Healthcare FAQs**
These can help the chatbot with general health-related questions:

- **[NHS FAQs](https://www.nhs.uk/conditions/)**  
  - Publicly available FAQs about various health conditions and treatments.

- **[WebMD Symptoms and Treatments](https://www.webmd.com/)**  
  - General health questions and symptom descriptions (requires web scraping).

---

### **8. Sentiment and Emotion Analysis**
To make the chatbot empathetic in its responses:

- **[IEMOCAP](https://sail.usc.edu/iemocap/)**  
  - A dataset for emotion recognition from text and speech, useful for detecting patient emotions.

- **[EmotionLines](http://doraemon.iis.sinica.edu.tw/emotionlines/)**  
  - Contains dialogues annotated with emotions.

---

### **9. Ethics and Bias Considerations**
Make sure to include datasets to minimize bias and ensure ethical chatbot behavior:

- **[Bias in QA (BIAS-QA)](https://github.com/allenai/bias-in-QA)**  
  - Datasets for detecting and reducing bias in question-answering systems.

---

### **Fine-Tuning Tips**
1. **Start with General Models**: Use pre-trained language models like GPT, LLaMA, or BERT and fine-tune them on your healthcare-specific dataset.
2. **Combine Datasets**: Merge multiple datasets for better generalization.
3. **Ethical Compliance**: Ensure compliance with healthcare standards like HIPAA for data privacy.

---

Let me know if you need help with implementation or more specific datasets!
