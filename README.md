**COMI-LINGUA** (**CO**de-**MI**xing and **LING**uistic Insights on Natural Hinglish **U**sage and **A**nnotation) is a large-scale, expert-annotated dataset for Hindi-English code-mixed text. It supports multiple foundational NLP tasks and is designed to benchmark code-mixed and multilingual models.

<div align="center">
  <p>
    <a href="https://aclanthology.org/2025.findings-emnlp.422.pdf"><img alt="EMNLP" src="https://img.shields.io/badge/EMNLP-2025-brightgreen"></a>
    <a href="https://github.com/lingo-iitgn/commentator/blob/main/LICENSE"><img alt="License" src="https://img.shields.io/badge/License-CC BY SA 4.0-blue"></a>
  </p>
</div>

## 📝 Dataset Summary

- **Languages:** Hindi (hi), English (en)
- **Tags:** `code-mixing`, `Hinglish`, `expert-annotated`
- **Size:** 125,613 Instances annotated by three annotators.
- **License:** [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)


## 📚 Annotation Tasks

### 1. Language Identification (LID)

Token-level classification of each word as `hi`, `en`, or other.

> Based on [Microsoft LID tool](https://github.com/microsoft/LID-tool), reviewed and corrected by annotators.

```text
Sentence: प्रधानमंत्री  नरेन्द्र  मोदी  डिजिटल  इंडिया  मिशन  को  आगे  बढ़ाने  के  लिए  पिछले  सप्ताह  Google  के  CEO  सुंदर  पिचाई  से  मुलाकात  की  थी ।
LID tags:    hi   hi   hi    en    en    en   hi  hi   hi  hi  hi   hi    hi    en    hi  en   hi   hi   hi   hi   hi  hi ot
```

---

### 2. Matrix Language Identification (MLI)

Identifies the **dominant language** in each sentence.

```text
Sentence: "India’s automation and design expert pool is vast, और ज़्यादातर Global companies के इंजीिनयिंरग center भी भारत में हैं।"
Matrix Language: en
sentence:"किसानों को अपनी फसल बेचने में दिक्कत न हो इसके लिये Electronic National Agriculture Market यानि ई-नाम योजना तेजी से काम हो रहा है।"
Matrix Language: hi
```

---

### 3. Part-of-Speech Tagging (POS)

Token-wise part of speech tags using the [CodeSwitch library](https://github.com/sagorbrur/codeswitch), then refined by annotators.

```text
Sentence:  भारत   द्वारा  बनाया  गया Unified Payments Interface  यानि   UPI    भारत   की    एक   बहुत  बड़ी   success  story  है    ।
POS tags: PROPN  ADP VERB VERB  PROPN   PROPN    PROPN    CONJ  PROPN  PROPN ADP  DET  ADJ  ADJ    NOUN    NOUN  VERB  X
```

---

### 4. Named Entity Recognition (NER)

Token-wise entitiy recognition such as persons, location, organizations, gpe, and date using the [CodeSwitch library](https://github.com/sagorbrur/codeswitch) then corrected by annotators.

```text
Sentence: "मालूम हो कि पेरिस स्थित Financial Action Task Force, FATF ने जून 2018 में पाकिस्तान को ग्रे लिस्ट में रखा था।"
NER Tags: "पेरिस" → GPE, "Financial Action Task Force, FATF" → ORGANISATION, "2018" → DATE, "पाकिस्तान" → GPE
```

---

### 5. Machine Translation (MT)

Parallel translations for each sentence into:
- **English**
- **Romanized Hindi**
- **Devanagari Hindi**

> Generated using [Llama 3.3 LLM](https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct), then refined manually.

```text
Sentence: भारत में भी green growth, climate resilient infrastructure और ग्रीन transition पर विशेष रूप से बल दिया जा रहा है।
English: In India too, special emphasis is being given to green growth, climate resilient infrastructure, and green transition.
Romanized Hindi: Bharat mein bhi green growth, climate resilient infrastructure aur green transition par vishesh roop se bal diya ja raha hai.
Devanagari Hindi: भारत में भी हरित विकास, जलवायु सहनशील आधारिक संरचना और हरित संक्रमण पर विशेष रूप से बल दिया जा रहा है।
```

---

### 6. Spelling Correction and Normalization (SCN)

Sentence-level normalization of noisy Hindi-English code-mixed text. 

> Generated using [GPT-OSS-120B](https://huggingface.co/openai/gpt-oss-120b), then refined manually.

```text
Sentence: Janmdin ki dheron shubhkaamnaayen sir... Aap swasth rahen... Dirghayu ho... Yahi hamare poore pariwaar ki shubhkaamnaayen hain  
Normalized: Janmadin ki dheron shubhkaamnayein sir. Aap swasth rahe. Dirghayu ho, yahi hamare pure parivaar ki shubhkaamnayein hain.
```

---

## 📂 Repository Structure

```
.
├── LID_train.csv
├── LID_test.csv
├── MLI_train.csv
├── MLI_test.csv
├── MT_train.csv
├── MT_test.csv
├── NER_train.csv
├── NER_test.csv
├── POS_train.csv
├── POS_test.csv
├── SCN_train.csv
└── SCN_test.csv
```

---
## :link: Relevant Links 

Paper Link: [`EMNLP 2025 Paper`](https://aclanthology.org/2025.findings-emnlp.422.pdf)

Explore the Project: [`Project Website`](https://lingo.iitgn.ac.in/codemixing/)

## 📄 License

This dataset is distributed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

---
## ⭐ Citation

If you find COMI-LINGUA helpful for your research, please cite it below:

```bibtex
@inproceedings{sheth-etal-2025-comi,
    title = "{COMI}-{LINGUA}: Expert Annotated Large-Scale Dataset for Multitask {NLP} in {H}indi-{E}nglish Code-Mixing",
    author = "Sheth, Rajvee  and
      Beniwal, Himanshu  and
      Singh, Mayank",
    editor = "Christodoulopoulos, Christos  and
      Chakraborty, Tanmoy  and
      Rose, Carolyn  and
      Peng, Violet",
    booktitle = "Findings of the Association for Computational Linguistics: EMNLP 2025",
    month = nov,
    year = "2025",
    address = "Suzhou, China",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.findings-emnlp.422/",
    pages = "7973--7992",
    ISBN = "979-8-89176-335-7",
}
```
