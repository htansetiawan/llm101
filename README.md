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

## Fine-Tuning

What is LoRA?
LoRA is a parameter-efficient fine-tuning method that introduces low-rank matrices into specific layers of a pre-trained model. It works by:

Freezing the Original Weights: During training, the original model weights remain unchanged.
Injecting Trainable Matrices: Trainable low-rank matrices are added to certain layers (e.g., attention layers) to model the updates.
These trainable matrices (called LoRA adapters) represent the task-specific changes required for fine-tuning.

Why Save LoRA Adapters?
Instead of saving the entire fine-tuned model, which can be massive (e.g., tens or hundreds of GB), you only save the small LoRA adapter weights. This has several benefits:

Efficiency: LoRA adapters are much smaller than full model weights, making them easier to store and share.
Flexibility: You can apply these adapters to the original pre-trained model during inference, effectively "merging" them on the fly.
Cost-effectiveness: Fine-tuning with LoRA reduces training costs as fewer parameters are updated.
Example Use Case
Let’s say you’re fine-tuning a large language model like LLaMA on a healthcare dataset. Instead of saving the entire fine-tuned model:

You save only the LoRA adapters, which might be just a few MB in size.
During inference, you load the original pre-trained LLaMA model and apply the LoRA adapters dynamically to get the fine-tuned behavior.
Saving LoRA Adapters
Here’s how you might save LoRA adapters using the Hugging Face peft library:

```python
from peft import PeftModel

# Assume 'model' is your fine-tuned model with LoRA applied
model.save_pretrained("path_to_save_lora_adapters")
This saves only the LoRA weights, not the entire model.
```

Loading LoRA Adapters
To use the LoRA adapters later, you can load them back with the pre-trained model:

```python
from transformers import AutoModel
from peft import PeftModel

# Load the original model
base_model = AutoModel.from_pretrained("path_to_base_model")

# Load the LoRA adapters
model_with_lora = PeftModel.from_pretrained(base_model, "path_to_save_lora_adapters")
```

This dynamically applies the fine-tuned LoRA adapters to the original model.

Summary
Saving as LoRA adapters is a lightweight and efficient way to capture the changes made during fine-tuning without needing to store the entire model. This approach is particularly beneficial when working with large models or deploying task-specific fine-tuned versions.
