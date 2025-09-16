	
# TeamQuals

#Quick Start ⚡
Click the badge below to open the notebook in Google Colab.  

[![ Click to Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/oloriafin/TeamQuals/blob/main/Project-Del-3-TeamQuals.ipynb)


# Dataset  
This project uses the [GitBugs dataset](https://www.kaggle.com/datasets/av9ash/gitbugs) (hosted on Kaggle). 
Navigate to the firefox folder and download Firefox_bugs_csv
- Download the dataset from Kaggle and place it in your working directory (Colab or local). 



# Text Preprocessing: Tokenization, Stopword Removal & Stemming

This project demonstrates a basic **NLP preprocessing pipeline** using Python, Pandas, and NLTK.  
It covers:
- Text cleaning (punctuation removal, lowercasing)
- Tokenization
- Stopword removal
- Stemming

---



### 1. Create environment & install dependencies
```bash
python -m venv .venv
source .venv/bin/activate     # Windows: .venv\Scripts\activate
pip install --upgrade pip
pip install pandas nltk
````

### 2. Download NLTK data (only once)

```bash
python -c "import nltk; nltk.download('punkt'); nltk.download('punkt_tab'); nltk.download('stopwords')"
```

### 3. Install & launch Jupyter Notebook

```bash
pip install notebook
jupyter notebook
```

### 4. Run notebook cells in order

Make sure your dataframe has a column named **`Notes`** (or update the code to match your column name).

```python
import re, pandas as pd
from nltk.tokenize import word_tokenize
from nltk.corpus import stopwords
from nltk.stem import PorterStemmer

# Load your data
dt = pd.read_csv("data.csv")  # <-- replace with your file

# Cleaned text
dt["Cleaned"] = dt["Notes"].str.replace(r"[^a-zA-Z\s]", "", regex=True).str.lower()
print("Cleaned Text:\n", dt["Cleaned"])

# Tokenization
dt["Tokens"] = dt["Cleaned"].apply(word_tokenize)
print("\nTokenized Words:\n", dt["Tokens"])

# Stopword removal
stop_words = set(stopwords.words("english"))
dt["Filtered"] = dt["Tokens"].apply(lambda t: [w for w in t if w not in stop_words])
print("\nFiltered Tokens (No Stopwords):\n", dt["Filtered"])

# Stemming
ps = PorterStemmer()
dt["Stemmed"] = dt["Filtered"].apply(lambda t: [ps.stem(w) for w in t])
print("\nStemmed Tokens:\n", dt["Stemmed"])

# (Optional) Save results
dt.to_csv("processed.csv", index=False)
```

---

## 📂 Example Input

**data.csv**

```csv
Notes
"Hello! This is an example sentence, demonstrating Text Processing."
"NLTK is widely used for text analysis in Python."
```

---

## 📊 Example Output

```
Cleaned Text:
0    hello this is an example sentence demonstrati...
1                nltk is widely used for text analy...

Tokenized Words:
0    [hello, this, is, an, example, sentence, demo...
1    [nltk, is, widely, used, for, text, analysis,...

Filtered Tokens (No Stopwords):
0    [hello, example, sentence, demonstrating, tex...
1             [nltk, widely, used, text, analysis,...

Stemmed Tokens:
0    [hello, exampl, sentenc, demonstr, text, proc...
1           [nltk, wide, use, text, analysi, python]
```

---

## 📌 Notes

* If you see an error about `punkt_tab` not found, run:

  ```bash
  python -c "import nltk; nltk.download('punkt'); nltk.download('punkt_tab')"
  ```
* Update the column name in the script if your CSV doesn’t use `"Notes"`.


