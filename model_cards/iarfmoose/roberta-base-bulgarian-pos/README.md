# Roberta-Base Bulgarian Part-Of-Speech Tagger

## Model description

This model is based on [roberta-base](https://huggingface.co/roberta-base) but pretrained and fine-tuned on Bulgarian text.

## Training data

The model was pretrained on [bul_newscrawl_2017_1M and bul_wikipedia_2016_1M](https://wortschatz.uni-leipzig.de/en/download/bulgarian) from Leipzig Corpora Collection and [bg_dedup](https://oscar-corpus.com/) from OSCAR. It was then fine-tuned on [UD_Bulgarian-BTB](https://universaldependencies.org/) from Universal Dependencies and BulTreeBank.

## Training procedure

For pretraining, the data was tokenized and packed into 512 token chunks before being passed into the model. The model was trained with a batch size of 8 (due to the limitations of training on Google Colab), AdamW and a linear schedule with a linearly decreasing learning rate starting from 5e-5.

For fine-tuning, the model was trained over 5 epochs on the Part-Of-Speech tags from the UD_Bulgarian-BTB dataset. The model uses a BPE tokenizer and predicts the part of speech based on the first token from each word. The model achieves 97.75% accuracy on the test set.
