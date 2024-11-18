
# Machine Translation model from English to Garo using Transfer Learning

# DataSet : 
```
https://docs.google.com/spreadsheets/d/1TiU39Nq4N-rKzXnYx2LwdGpLulv58GIw/edit?usp=sharing&ouid=102582516564135592549&rtpof=true&sd=true
```

This project demonstrates the fine-tuning of a pre-trained translation model (Helsinki-NLP's `opus-mt-en-fr`) to translate English sentences into Garo, a Tibeto-Burman language. The dataset used consists of paired English and Garo sentences. The project includes data preprocessing, model training, evaluation using BLEU score, and saving the trained model for future use.


---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Dataset](#dataset)
3. [Preprocessing](#preprocessing)
4. [Model](#model)
5. [Training](#training)
6. [Evaluation](#evaluation)
7. [Results](#results)
8. [Setup and Usage](#setup-and-usage)
9. [Future Work](#future-work)

---

## Project Overview

The goal of this project is to train a machine translation model for English to Garo language translation. Using HuggingFace's Transformers library, a pre-trained sequence-to-sequence model (`opus-mt-en-fr`) is fine-tuned on the provided dataset. The BLEU score is used to evaluate translation quality.

---

## Dataset

### Overview

The dataset contains **2000+ English-Garo sentence pairs**, providing a robust foundation for model fine-tuning. It was created with custom inputs to ensure diversity and relevance for real-world usage.

Example:

| English     | Garo           |
|-------------|----------------|
| Everything  | Pilak bostuan  |
| Nowhere     | Darangchiba    |
| Somewhere   | Jechiba        |
| Everywhere  | Gimikchian     |
| Everytime   | Pangnan        |

---

## Preprocessing

The following preprocessing steps are applied to the dataset:

1. **Lowercase Conversion**: Convert all text to lowercase.
2. **Apostrophe Removal**: Remove all apostrophes.
3. **Punctuation Removal**: Remove punctuation from sentences.
4. **Digit Removal**: Remove numerical digits.

These steps ensure consistency in the input data for training.

---

## Model

The pre-trained translation model used is **Helsinki-NLP/opus-mt-en-fr** from the HuggingFace Transformers library. This model is fine-tuned for English-to-Garo translation.

---

## Training

### Key Steps:
1. Tokenize English and Garo sentences.
2. Fine-tune the pre-trained model for 15 epochs with a batch size of 32.
3. Use the AdamW optimizer with a learning rate of 0.0001.
4. Save the trained model as `model.pkl`.

The model is trained to minimize translation loss and improve accuracy.

---

## Evaluation

The model is evaluated using the **BLEU score**, a standard metric for assessing the quality of machine-translated text. Tokenized reference translations and model-generated translations are compared to compute the BLEU score.

---

## Results

After training, the model achieved a BLEU score indicating its translation accuracy. Example translation:

**Input**: `I will see you tomorrow`  
**Output**: `knalo nangko gronggen`

---

## Setup and Usage

### Prerequisites
- Python 3.10+
- Libraries: `transformers`, `torch`, `pandas`, `tqdm`, `nltk`

## Output
-
English sentence: i have to meet my son
Predicted Garo sentence: anga angni depante ko grongna nangen
True Garo sentence: anga angni depante ko grongna nangen
----------------
- English sentence: they halt at staying houses
- Predicted Garo sentence: uamang dongparagen
- True Garo sentence: uamang dak banglarango machaka
----------------
- English sentence: cream 
- Predicted Garo sentence: makon
- True Garo sentence: cream 
----------------
- English sentence: red pepper 
- Predicted Garo sentence: gitchak
- True Garo sentence: gulmorich
----------------
- English sentence:  everything 
- Predicted Garo sentence: pilak bostuan
- True Garo sentence: pilak bostuan
----------------

### Steps
1. Clone this repository.
2. Install required libraries:
 ```bash
   pip install torch transformers pandas tqdm nltk
```
3. place dataset file (en_gr.cvs) in the working directory
4. Run the training script:
```
python train_model.py

```
5. Evaluate the model using the BLUE SCORE
```
python evaluate_model.py
```
## Future Work
- Enhance Dataset: Include more diverse sentence pairs to improve model accuracy.
- Hyperparameter Tuning: Experiment with learning rates, batch sizes, and epochs.
- Deploy Model: Serve the model as an API for real-time translation.
