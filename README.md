# **Japanese JLPT Text Generator** 🎓 📖
Generating text aligned with JLPT levels to aid language learning.
---

<div align="left">
  <a href="https://github.com/katherine-welbourne/jlpt-text-generator/blob/main/jlpt_demo.png">
    <img src="jlpt_demo.png" alt="JLPT Text Generator" width="400">
  </a>
</div>

---

## **Table of Contents** 📚
1. [Overview](#overview)
2. [Dataset](#dataset)
3. [Model](#model)
4. [Installation](#installation)
5. [Usage](#usage)
6. [Example Output](#example-output)
7. [Future Enhancements](#future-enhancements)
8. [License](#license)

---

## **Overview** 📝
The JLPT Text Generator is a machine learning project that generates text based on the Japanese Language Proficiency Test (JLPT) vocabulary levels. The generated sentences focus on vocabulary from a specified JLPT level while allowing the use of lower-level vocabulary for naturalness. Additionally, the tool displays the generated sentences in **Romaji** to aid pronunciation practice.

### Key Features:
- Input JLPT levels: N5, N4, N3, N2, N1. 🛠️
- Emphasizes vocabulary from the target level. ✍️
- Utilizes Hugging Face Transformers for text generation. 🤖
- Color-coded output to indicate JLPT levels of used vocabulary. 🌈
- Displays Romaji for generated sentences. 🗣️

---

## **Dataset** 📊
The dataset used is a custom JLPT vocabulary dataset:
- **Source File**: `/content/drive/MyDrive/ML/Datasets/JAPANESE_JLPT_WORDS.csv`
- **Columns**:
  - `headword`: Japanese word (Kanji/Hiragana).
  - `JLPT`: JLPT level (N5 to N1).

---

## **Model** 🤖
The project uses Hugging Face’s pre-trained GPT-2 model adapted for Japanese text generation:
- **Base Model**: [GPT-2-Japanese](https://huggingface.co/colorfulscoop/gpt2-small-ja) 🚀
- **Fine-Tuned For**: JLPT-constrained text generation.
- **Framework**: Hugging Face Transformers. 🛠️

---

## **Installation** ⚙️
To set up the project locally, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/katherine-welbourne/jlpt-text-generator.git
   cd jlpt-text-generator
   ```

2. Install dependencies:
   ```bash
   pip install transformers torch pandas pykakasi
   ```

---

## **Usage** 🏋️
### Generate Text:
```python
# Example usage
level = "N3"  # Desired JLPT level
prompt = "私は"  # ("I am")
max_length = 50
output_text = generate_text_jlpt(level=level, prompt=prompt, max_length=max_length)
print(output_text)

# Display Romaji
from pykakasi import kakasi
kks = kakasi()
kks.setMode("H", "a")  # Hiragana to ascii
kks.setMode("K", "a")  # Katakana to ascii
kks.setMode("J", "a")  # Japanese to ascii
kks.setMode("r", "Hepburn")  # Use Hepburn Romanization
converter = kks.getConverter()
print(converter.do(output_text))
```

### Visualize JLPT Levels:
Color-code the generated text by JLPT level:
```python
color_text_by_jlpt(output_text, df)
```

---

## **Example Output** 🏆
### Input
- JLPT Level: N3
- Prompt: "私は"  ("I am")

### Output
```plaintext
私は日本の文化に興味があります。
```
### Romaji:
```plaintext
watashi wa nihon no bunka ni kyoumi ga arimasu.
```

### JLPT Distribution:
- N5: 5 words
- N4: 3 words
- N3: 4 words
- N2: 2 words
- N1: 1 word

---

## **Future Enhancements** 🚀
- Add support for generating Furigana annotations.
- Fine-tune models for domain-specific vocabulary.
- Develop an interactive demo using Gradio or Streamlit.

---

## **License** 📜
This project is licensed under the [MIT License](LICENSE). 📖

---

