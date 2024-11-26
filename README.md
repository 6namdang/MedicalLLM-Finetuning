MedicalLLM-Finetuning

Improvise and fine-tune an LLM model based on GPT-3.5-turbo using a medical dataset.

I started this project to gain a deeper understanding of how Large Language Models (LLMs) work and how fine-tuning them on specialized datasets can improve accuracy. My goal is to compare the performance of different models and explore how fine-tuning on a medical dataset can help improve the model's accuracy in understanding medical terminology and reports.

The dataset includes medical specialties along with related reports. For example, a specialty such as Cardiovascular / Pulmonary might have a report like the following:

2-D M-MODE: 
1. Left atrial enlargement with left atrial diameter of 4.7 cm.
2. Normal size right and left ventricle.
3. Normal LV systolic function with left ventricular ejection fraction of 51%.
4. Normal LV diastolic function.
5. No pericardial effusion.
6. Normal morphology of aortic valve, mitral valve, tricuspid valve, and pulmonary valve.
7. PA systolic pressure is 36 mmHg.

DOPPLER: 
1. Mild mitral and tricuspid regurgitation.
2. Trace aortic and pulmonary regurgitation.

Data preprocessing:
I sample a fixed amount of dataset for my train/test/val instead of using stratified random sample because I do not have enough funds to train via gpt-3.5 model.

Data formatting:
Tokenize the report column annd format data into chatbased which include system, user and assistant. 
![image](https://github.com/user-attachments/assets/632c5ac2-72d6-464c-af43-3088ef7ede99)


Finetuning

I implement gpt-3.5 turbo:
<img width="493" alt="image" src="https://github.com/user-attachments/assets/09a97290-6291-43a5-adc0-4d4ed8dad8f1">


GPT-3.5 Turbo is built upon the transformer model, which consists of the following key components:

Encoder-Decoder Architecture (used in some transformer models):
<img width="272" alt="image" src="https://github.com/user-attachments/assets/ef893e35-2539-450e-9897-c19b51617f8f">

GPT models, including GPT-3.5, are based on a decoder-only transformer architecture, which means they don't use the encoder part of the transformer. Instead, they rely on a stack of decoder layers to process input text.
Each decoder layer contains a multi-head self-attention mechanism and a position-wise feed-forward neural network.
Self-Attention Mechanism:

The self-attention mechanism allows the model to consider all previous words in the input sequence when generating each new word. This mechanism helps the model capture complex relationships and dependencies in the input data.
Positional Encoding:

Since transformers process the entire input at once (instead of sequentially like RNNs or LSTMs), they use positional encodings to inject information about the order of words into the model, allowing it to understand the sequence of tokens.
Feed-Forward Neural Networks:

Each layer of the transformer contains a feed-forward neural network that processes the information output by the attention mechanism, transforming it for use in subsequent layers.
Large-Scale Pretraining:

GPT-3.5 Turbo, like its predecessors, is pretrained on a vast amount of text data. The model learns to predict the next word in a sequence, which allows it to learn language patterns, grammar, reasoning, and factual knowledge.
Autoregressive Language Model:

GPT-3.5 Turbo is an autoregressive model, meaning it generates text one token at a time and uses previously generated tokens as part of the input for generating the next token. This enables it to create coherent, contextually relevant text.

Result:

<img width="365" alt="image" src="https://github.com/user-attachments/assets/2094a2f1-3189-49e6-b44f-41c206b2a595">


Compare to gpt-3.5-turbo, my model perform 20% better:


![image](https://github.com/user-attachments/assets/a4c0342c-faf9-4fd7-bd19-c458dfa72fc3)





