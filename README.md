# 🧠 Legal Brief Argument–Counterargument Linker

This project analyzes legal briefs by automatically linking argument sections from a **moving brief** with corresponding counter-arguments in a **response brief**. It supports legal professionals in faster legal research and more effective drafting.

---

## 📌 Objective

Given a set of legal brief pairs, the task is to:

- Identify **argument sections** in each brief.
- Match each **argument in the moving brief** with its **counter-arguments in the response brief**.
- Evaluate the quality of predicted links using known ground-truth on a training subset.

This process automates part of legal analysis and drafting, helping attorneys trace how each argument is contested in court filings.

---

## 📂 Dataset Format

Each brief pair is represented as a JSON object:

```json
{
  "moving_brief": {
    "brief_id": "string",
    "brief_arguments": [
      {
        "heading": "string",
        "content": "string"
      }
    ]
  },
  "response_brief": {
    "brief_id": "string",
    "brief_arguments": [
      {
        "heading": "string",
        "content": "string"
      }
    ]
  },
  "true_links": [
    ["moving_heading_1", "response_heading_A"],
    ["moving_heading_2", "response_heading_B"]
  ],
  "split": "train" | "test"
}
```

- ✅ 8 brief pairs include labeled \`true_links\` for training and validation.
- 🔍 2 brief pairs are held out for testing and final evaluation.

---

## 🛠️ Approach

We implement a **pairwise classification approach** using transformer models to determine whether a pair of arguments (one from the moving brief, one from the response) forms a valid argumentative link.

### 🔑 Key Components

- **Preprocessing:** Generate all possible argument pairs across briefs.
- **Modeling:** Use transformer-based models (\`LegalBERT\`, \`BERT\`, etc.) to encode argument pairs.
- **Classification:** Train a binary classifier to predict links.
- **Evaluation:** Measure how well the model identifies correct links.

---

## 🧪 Evaluation

- Predictions are compared against \`true_links\` for the test split.
- Manual inspection and automatic metrics (Precision, Recall, F1) are used for evaluation.
- Matching quality is reviewed during final pitch/demo.

---

## 💻 Features

- ✅ Dynamic upload and parsing of brief pair datasets.
- ✅ Pairwise argument–counterargument generation and encoding.
- ✅ Model training using transformer-based embeddings.
- ✅ Streamlit-based interactive interface for exploring results.


## 🧱 Tech Stack

- Python 3.11+
- Transformers (HuggingFace)
- Streamlit
- Scikit-learn
- JSON-based dataset

---

## 🏁 Future Enhancements

- Clause-level linking across multiple briefs  
- Citation-aware linking  
- Integrate document-level context (precedents, judge rulings)

---

## 🤝 Sponsorship & Credits

Built for the **Stanford Legal AI Hackathon**  
Sponsored by **Bloomberg**  
Developed by Chandini, Amrutha, Bharathi, Rutuja – AI Security & NLP Enthusiasts 🛡️🧠

