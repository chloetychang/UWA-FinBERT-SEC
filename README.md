# UWA-FinBert-SEC-Press-Releases
Finetuning FinBert on SEC Press Releases
- Starting Point: https://github.com/Incredible88/FinBERT-FOMC

## Introduction to this Model
This model aims to analyze the sentiment of SEC press releases, particularly enforcement-related documents, using a fine-tuned version of FinBERT.

To examine the model, as well as all code associated, run `Finbert-finetuned.ipynb` in Google Colab or your local environment by cloning this repository. 

---

## Notes on Model Training
- The model is trained using a dataset full of predictions generated from the original SEC press release parquet file using FinBERT.  
- Only high-confidence predictions (> 95) are retained to improve data reliability.

---

## Files Included in This Repository
- **Finbert-finetuned.ipynb:** Jupyter notebook used to train FinBERT and produce the required datasets.  
- **environment.yml:** Conda environment file for replicating the environment used in training.  
- **sec_press_release_with_avg_sentiment.csv:** Contains `unique_id`, `text_pr`, `avg_score`, and `avg_label`.
    - unique_id (index)
    - text_pr (the original press release text)
    - avg_score (the average of all numerical scores obtained from the sentences in the same row of the original dataframe)
    - avg_label (the sentiment label assigned based on the avg_score) 
- **sec_press_release_with_avg_sentiment.parquet:** Parquet version of the above CSV.  
- **sec_sentences_with_ids.csv:** Contains `unique_id` and `sentence` for each press release. 
    - unique_id (index)
    - sentence (the original press release text, divided into sentences)
- **sec_sentences_with_labels.csv:** Contains `unique_id`, `sentence`, `label`, and `score`. 
    - unique_id (index)
    - sentence (the original press release text, divided into sentences)
    - label (Neutral, Positive, Negative)
    - score (confidence level that tuned FinBert has regarding its analysis)
- **sec.parquet:** Original parquet file containing the SEC press release data.
