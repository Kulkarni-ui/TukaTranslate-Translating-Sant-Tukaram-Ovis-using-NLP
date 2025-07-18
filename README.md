
# 🕉️ TukaTranslate: Translating Sant Tukaram’s Ovis Using Meta’s NLLB Model

This project focuses on translating the devotional ovis (verses) of **Sant Tukaram**, a revered saint-poet from the Bhakti movement, using modern NLP techniques. Unlike typical translation tasks, Tukaram's verses are metaphorical and spiritually intense — demanding a meaning-preserving translation approach.

---

## 📌 Objectives

- Translate 100 ovis from Marathi (Devanagari) to English using **Meta’s NLLB model**
- Assess the translation quality via sample comparisons and qualitative evaluation
- Highlight challenges of translating **devotional, poetic texts** using machine models

---

## 📚 Dataset

- Input file: `Sant Tukaram Gatha.xlsx`
- Contains original Marathi ovis in Devanagari script and human/manual English translations

---

## 🤖 Model Details

- **Model Used**: `facebook/nllb-200-distilled-600M`
- **Library**: Hugging Face Transformers
- **Backend**: PyTorch

```python
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM

model_name = "facebook/nllb-200-distilled-600M"
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSeq2SeqLM.from_pretrained(model_name)

tokenizer.src_lang = "mar_Deva"
tokenizer.tgt_lang = "eng_Latn"
```

---

## 🔍 Sample Flow

```python
inputs = tokenizer(text, return_tensors="pt", padding=True)
translated_tokens = model.generate(**inputs, forced_bos_token_id=tokenizer.lang_code_to_id["eng_Latn"])
translated_text = tokenizer.batch_decode(translated_tokens, skip_special_tokens=True)
```

---

## 🔎 Sample Translation Comparisons (from NLLB)

### 1️⃣  
📝 **Marathi Ovi**:  
`तुका म्हणे मागणे देवा । तुझा विसर नको मज ॥`

✅ **Manual Translation**:  
*Tuka says: My only prayer, O Lord, is that I never forget You.*

🤖 **Model Translation**:  
*"Thou hast said, 'Pray, O God; forget not thy heart.' "*

---

### 2️⃣  
📝 **Marathi Ovi**:  
`दुःख सुखाचे काही नाही । जो तुजविण काही नाही ॥`

✅ **Manual Translation**:  
*There is neither pain nor pleasure for the one who has none but You.*

🤖 **Model Translation**:  
*There is no happiness in sorrow, there is no happiness in tears.*

---

### 3️⃣  
📝 **Marathi Ovi**:  
`नाम घेतले जिवी लाभे । शांती लाभे अंतःकरणा ॥`

✅ **Manual Translation**:  
*When I take Your name, my soul finds peace in my heart.*

🤖 **Model Translation**:  
*"Take your name and live your life. Peace be to your heart".*

---

### 4️⃣  
📝 **Marathi Ovi**:  
`उपकार देईन आयुष्य । पण नाव तुझे न विसरे ॥`

✅ **Manual Translation**:  
*I will spend my life for You, but I will never forget Your name.*

🤖 **Model Translation**:  
*I will give up my life, but your name will never be forgotten.*

---


## 📈 Evaluation Metrics

| Metric         | Average Score |
|----------------|---------------|
| **ROUGE-L**    | ~0.2313      |
| **BLEU**       | ~0.0249        |
| **METEOR**     | ~0.1827       |

These metrics reveal that while the model can produce fluent sentences, it struggles with the **contextual depth and spiritual fidelity** of Tukaram’s poetry.

---

## 🔮 Future Directions

- Fine-tune NLLB on a corpus of **Marathi devotional texts**
- Compare performance with **IndicTrans2**
- Use **NER** for better handling of divine and cultural references
- Build an **interactive Ovi translator** using Streamlit

---

## 📁 Folder Structure

```
NLP_Saint_Tukaram/
│
├── Sant Tukaram Gatha.xlsx                   # Dataset of 100 ovis
├── Final_Tukaram_Gatha.ipynb       # Notebook using NLLB model
├── README.md                       # Project documentation
```

---

## 🙏 Acknowledgements

- Sant Tukaram and the Bhakti tradition
- Meta AI for open-sourcing the NLLB model
- Hugging Face Transformers
- Marathi translation experts

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).

