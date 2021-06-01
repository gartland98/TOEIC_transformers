# TOEIC_transformers

Achieved over 90% Correct rate with ONLY Pre-Trained XLnet model in TOEIC!!

(this is a follow-up research of toeic-bert by graykode, https://github.com/graykode/toeicbert)

I've solved toeic part 5 (cloze test) by using several pretrained transformer models. Biggest difference from former research is fine-tuning pretrained model by changing the objective of algorithm from fill in blanks to select the most natural sentence among several choices. To apply huggingface API, first I filled a blank by using every choices and made 4 full sentences. After that, I trained model to choose the most natural sentence by using 'bert(or other models)formultiplechoice' API. I used 3625 questions (train:3200, test: 425 each) which are collected by crawling websites. Because of copyright, I will not open dataset. I used the same data format as graykode toeic bert. Hyperparameters I used for experiment are as follows: batch:16 or 32, epoch 16, learning rate: 2e-5, 1e-5, 5e-6, 1e-6. 

Result are as follows: 

batch:16, epoch:16, learning rate:1e-5, 

models | Bert-base-uncased | Bert-large-uncased | XLnet-base-uncased | XLnet-large-uncased | Electra-base-discriminator | Electra-large-discriminator
---- | ---- | ---- | ---- | ---- | ---- | ---- 
train accuracy | 99.2 | 99.3 | 96.2 | 98.4 | 뚝배기깹니다 | 98.0
test accuracy | 87.1 | 90.1 | 88.2 | 92.4 | 뚝배기깹니다 | 91.1


models | Albert-base-v1 | Albert-base-v2 | Albert-large-v1 | Albert-large-v2 | Albert-xlarge-v1 | Albert-xlarge-v2 | Albert-xxlarge-v1 | Albert-xxlarge-v2
---- | ---- | ---- | ---- | ---- | ---- | ---- 
train accuracy | 99.2 | 99.3 | 96.2 | 98.4 | 뚝배기깹니다 | 98.0 | 98.0 | 98.0
test accuracy | 87.1 | 90.1 | 88.2 | 92.4 | 뚝배기깹니다 | 91.1 | 98.0 | 98.0

 
