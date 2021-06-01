# TOEIC_transformers

Achieved over 90% Correct rate with ONLY Pre-Trained XLnet model in TOEIC!!

(this is a follow-up research of toeic-bert by graykode, https://github.com/graykode/toeicbert)

I've solved toeic part 5 (cloze test) by using several pretrained transformer models. Biggest difference from former research is fine-tuning pretrained model by changing the objective of algorithm from fill in blanks to select the most natural sentence among several choices. To apply huggingface API, first I filled a blank by using every choices and made 4 full sentences. After that, I trained model to choose the most natural sentence by using 'bert(or other models)formultiplechoice' API. I used 3625 questions (train:3200, test: 425 each) which are collected by crawling websites. Because of copyright, I will not open dataset. I used the same data format as graykode toeic bert. Hyperparameters I used for experiment are as follows: batch:16 or 32, epoch 16, learning rate: 2e-5, 1e-5, 5e-6, 1e-6. 


'''
     {'1': 'suffer', 
     '2': 'suffers', 
     '3': 'suffering', 
     '4': 'suffered',
     'anwser': 'suffered', 
     'question': 'The assets of Marble Faun Publishing Company ___ last quarter when one of their main local distributors went out of business.'} 
 
'''
 
 
 
   2. Results
Best combination: batch:16, epoch:16, learning rate:1e-5, 

models | Bert-base-uncased | Bert-large-uncased | XLnet-base-uncased | XLnet-large-uncased | Electra-base-discriminator | Electra-large-discriminator
---- | ---- | ---- | ---- | ---- | ---- | ---- 
train accuracy | 99.2 | 99.3 | 96.2 | 98.4 | 92.7 | 98.0
test accuracy | 87.1 | 90.1 | 88.2 | 92.4 | 85.9 | 91.1

I also used Roberta, and Albert models but I couldn't fine-tune Roberta models (I assume it's because I use small number (16, 32) as a batch. Roberta paper use batch size of 256, 2k and 8k) and Albert models shows lower performance compare to models above. Albert-xxlarge-v2 with epoch 5, batch 16 and le-5 shows the best accuracy which was 92.9/89 (train/test) by each.



 
