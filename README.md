# exprep_LLM
LLM fine tuning for text classification with DistilBERT and MiniLM.

This repository contains files for a project on Finte Tuning LLM's for text classification.<br>
The folders GoEmotion and DBPedia 14 contian jupyter notebooks used to train the models distillbert and minilm on the dataset:<br>
https://huggingface.co/datasets/google-research-datasets/go_emotions <br>
https://huggingface.co/datasets/fancyzhx/dbpedia_14 <br>

The models are trained by classical fine tuning on the original layers as well as using LoRa between the Input and Output Layers.<br>
A Description of these techniques can be found in the research folders jupyter notebook called information.<br><br>

## Goal:
The goal of this project was to fine tune LLM's for text classification.<br> In general text classification can be a task of varying difficulty since different categorizations are possible. The datasets used in this projects consisted of 28 classes for GoEmotion and 14 Classes for DBPedia 14.<br><br> While in general any result that is better than guessing by chance is a success LLM's already have an understanding of language. For this reason the expectation was to show results that are much better than guessing.<br><br>
In the case of 28 Classes this was defined as an accuracy above 40% which has been achieved in other projects.<br>
For the DBPedia 14 Dataset I wanted to achieve an accuracy above 80%.<br>

## Models and Training
I trained models both using classical fine tuning of the already existing layers as well as LoRa. The training process consisted in all but one case of less than 20 epochs. 

## Specs
The calculations were made on a Nvidia 4090 GPU.

## Results 
Overall the models achieve very impressive results.
GoEmotion (28 Classes): 58.9% Accuracy with classical fine tuning, ~54% Accuracy with LoRa (r=16, alpha=32, Dropout=0.1) both with DistilBERT.
DBPedia 14 (14 Classes): 99.9% Accuracy with distilBERT LoRa (r=16|8, alpha=32, Dropout=0.1), 85% Accuracy with MiniLM LoRa (r=8, alpha=32, Dropout=0.1) (ended trainig on MiniLM after 20 epochs but it could probably still get a bit better

Confusion Matrix of DBPedia 14 Dataset with distilBERT:![grafik](https://github.com/user-attachments/assets/619004c9-f31b-482d-91e0-77ecfa395d45)



## Key Findings:
- Using LoRa none of the models overfitted but reached almost equal results as the best models by classical fine tuning
- Text classification on 14 classes seems like a task that smaller LLM's can do with very high accuracy
- All expectations for this project have been achieved via LLM fine tuning

## Further Development:
The results on DBPedia 14 are quiet impressive and do not seem to need much more touch. In particular the model based on DistilBERT is a very good option to fullfill this task. Further improvement could go into the are of using less data to produce the same or similar results. <br>
Furthermore, one should try to improve the results on the GoEmotion dataset. There are different possibilties such as: Allowing multi class predictions, using data augmentation to level the sample size of each class in the dataset.

## Resources:
https://www.youtube.com/watch?v=mrKuDK9dGlg  <br>
https://www.youtube.com/watch?v=iOdFUJiB0Zc  <br>
https://www.youtube.com/watch?v=gs-IDg-FoIQ  <br>
https://www.youtube.com/watch?v=eC6Hd1hFvos  <br>
<br>


https://labelyourdata.com/articles/llm-fine-tuning/top-llm-tools-for-fine-tuning
