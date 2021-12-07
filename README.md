
 <p align="center"><img src="https://cliply.co/wp-content/uploads/2021/09/CLIPLY_372109260_TWITTER_LOGO_400.gif" alt="books" width="50"/></p>
 
# `"What is in a Tweet?"`
I compare the performance of three SOTA pre-trained abstractive text summarization models on the TweetSum (He et al., 2020) dataset. Final project for CIS6390: Special Topics in Computing.  

## Getting Started
What can you find in this repository? 
```
├── data                        
│    ├── Kaggle Files  
│            ├── get_kaggle_files.txt  
│    ├── Raw Dataset  
│            ├── .jsonl files for raw dataset
│    ├── tweetsum_train.csv
│    ├── tweetsum_valid.csv
│    ├── tweetsum_test.csv
├── pre-processing     
│    ├── preprocess_tweetsum.ipynb 
│    ├── tweet_sum_preprocessor.py
│    ├── EDA.ipynb 
├── fine-tuning
│    ├── pegasus_model.ipynb
│    ├── bart_model.ipynb
│    ├── t5_model.ipynb
├── post-processing  
│    ├── selecting_summaries_for_HEv.ipynb
├── LICENSE
└── README.md
```
## Motivation
The aim of automatic text summarization is to condense the most crucial information in a document into a shorter form. This is fundamentally a difficult task; even humans struggle to adequately summarize documents. (There is, after all, a reason that literature students are often asked to summarize texts as homework.) Producing concise coherent summaries helps people glean the highlights of a document without having to dedicate too much time to the task, saving hours both in the summarization process itself and for the reader. There are two common approaches to summarizing a text: abstractive summarization, where the model uses the input document to generate novel text, and extractive summarization, where the model selects key sentences from the original document and assembles these into a summary. The success of Transformer Encoder-Decoder models on the text summarization task has led to rapid development in the field, and there are many models that achieve high performance on abstractive text summarization benchmarks. However, most research efforts have focused on summarizing single-speaker documents. With the still-rising popularity of social media apps, and rapidly improving speech-to-text algorithms that can transcribe conversations, it is efficacious to explore methods for summarizing dialogues – multiple-speaker texts – as well. 

The motivation behind this project is to gauge the performance of three state-of-the-art text summarization models on a dialogue dataset. One of these models – PEGASUS, developed by Google AI in 2020 – has a pre-training self-supervised objective designed to be relevant to the abstractive text summarization task. Because the pre-training objective is close to the down-stream task, it is hypothesized that the fine-tuned model will perform better on this down-stream task than models with more general pre-training objectives. PEGASUS has indeed out-performed, or achieved equivalent state-of-the-art results as, other Transformer Encoder-Decoder models on many benchmark abstractive text summarization datasets. However, it has never been fine-tuned on the TweetSum dataset (or, at least, the results were not made public). Furthermore, it does not seem as if the results of any abstractive text summarization using the TweetSum dataset have been made public. The performance of PEGASUS is compared to two other state-of-the-art pre-trained models used for abstractive text summarization -- T5 and BART.

## Try it yourself!
To fine-tune the three models yourself, you can either clone this repository or run the fine-tuning notebooks in Google Colab! 

* [PEGASUS](https://colab.research.google.com/drive/1yE2WK6aRYAdhqcwJ6bj34mKulJGAouy3?usp=sharing)
* [BART](https://colab.research.google.com/drive/1cmAiuB14NrEjA2nENNPpPpgfU_jkTBMA?usp=sharing)
* [T5](https://colab.research.google.com/drive/1rNOFq9cLZseMm33n6jVDnokcARvivx5N?usp=sharing)

Make a copy of each of the notebooks in order to edit and run them. In order to run these notebooks, you must also download the [train, validation, and test set csvs](https://github.com/sarahaman/CIS6930_TweetSum_Summarization/tree/main/data) and adjust the file paths with the notebooks. 

If you would like to reproduce my entire process -- from cleaning and pre-processing the data to post-processing -- you can clone this repository and follow along with the annotations in `preprocess_tweetsum.py`. You just need to change the file paths to match those on your local machine.

## References
This project was my introduction to both text summarization and fine-tuning models with Huggingface! I referenced the fantastic huggingface text summarization tutorial during the process to help me figure out what I was supossed to be doing. Code snippets that reference this tutorial are noted in the notebooks themselves.

* [Huggingface Summarization Tutorial](https://colab.research.google.com/github/huggingface/notebooks/blob/master/examples/summarization.ipynb)
* [TweetSum](https://github.com/guyfe/Tweetsumm)

**Papers**
