# 🕉️ TukaTranslate: Translating Saint Tukaram's Ovis Using NLP

This project aims to translate the deeply spiritual ovis (verses) of Sant Tukaram, a revered saint of the Bhakti movement, from Marathi to English using modern Natural Language Processing (NLP) techniques.

Sant Tukaram’s poetry is rich in metaphor, devotion, and cultural nuance — making it both a linguistic and spiritual challenge to translate. While traditional machine translation focuses on literal accuracy, this project embraces a meaning-preserving approach by comparing manually translated ovis with outputs from a pretrained MarianMT model

---

## 🔍 Project Objectives

- Translate 100 ovis from Marathi to English using Hugging Face's `MarianMT` model (`opus-mt-mr-en`)
- Evaluate translation quality using the **ROUGE-L metric**, more suited to poetic and paraphrased text
- Highlight the limitations of machine translation for devotional literature
- Encourage human-AI collaboration for culturally significant NLP tasks

---

## ✨ Why This Matters

Preserving Sant Tukaram's spiritual legacy and making it accessible globally through AI enables:

- **Cultural preservation** of Marathi literature.
- **Cross-lingual understanding** of Bhakti-era spirituality.
- A bridge between **ancient wisdom and modern technology**.
- Preserving and sharing Tukaram's verses with a wider, global audience helps bridge **language, culture, and time**. By combining **ancient wisdom** with **modern AI**, this project attempts to digitally honor a saint whose words still inspire millions.


---

## 📚 Dataset

- Contains 100 Ovis with the following columns:
  - `ovi_marathi`: Original Ovi in Marathi (Devanagari script)
  - `ovi_english`: Manual English Translation
  - `translated_by_model`: Output from MarianMT model
  - `rougeL_score`: ROUGE-L F1 score for each model vs. manual translation

---

## 🧠 Model Details

- **Model used**: `Helsinki-NLP/opus-mt-mr-en` (Marathi to English)
- **Library**: Hugging Face Transformers
- **Backend**: PyTorch

```python
from transformers import MarianMTModel, MarianTokenizer

model_name = "Helsinki-NLP/opus-mt-mr-en"
tokenizer = MarianTokenizer.from_pretrained(model_name)
model = MarianMTModel.from_pretrained(model_name)
```

---

## 📈 Evaluation Metric

- Used **ROUGE-L F1 Score** to evaluate translation quality.
- Captures semantic similarity via **longest common subsequence**.
- Chosen over BLEU due to better alignment with poetic structure.

---

## 📊 Key Results

| Metric               | Value     |
|----------------------|-----------|
| Avg. ROUGE-L Score   | 0.0894    |
| Max Score Observed   | ~0.3      |
| Translation Quality  | Modest    |

### Sample Comparison

```
🔸 Marathi Ovi:
तुका म्हणे मागणे देवा । तुझा विसर नको मज ॥

✅ Manual English:
Tuka says, O Lord, all I ask is — never let me forget You.

🤖 Model English:
Don't pay attention to your identity.
```

---

## ⚠️ Observations

- Model struggled with metaphor-rich, emotionally nuanced content.
- Some translations were overly generic or contextually incorrect.
- ROUGE-L was more effective than BLEU for this task.
- Pretrained models require **fine-tuning on devotional data** for better results.

---

## 🚀 Future Scope

- Fine-tune MarianMT on a **larger corpus of Marathi devotional texts**.
- Explore **IndicTrans2** or **human-AI post-editing pipelines**.
- Apply **Named Entity Recognition (NER)** to extract spiritual references.
- Build a **web-based Ovi translator or visualizer** using Streamlit or Flask.

---

## 📂 Folder Structure

```
📁 NLP_Saint_Tukaram/
│
├── tukaram_ovis.xlsx               # Dataset of 100 Ovis
├── NLP_Saint_Tukaram.ipynb         # Translation & evaluation notebook
├── NLP Saint Tukaram.ipynb - Colab.pdf  # Exported notebook (PDF)
├── README.md                       # Project documentation
```

---

## 🙏 Acknowledgements

- Sant Tukaram Maharaj and the Bhakti movement
- HuggingFace Transformers team
- Marathi literary translators and scholars

---

## 📜 License

This project is licensed under the [MIT License](LICENSE).
