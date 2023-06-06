# Final solution to RuCode 7

 # 🚀 What is RuCode?

RuCode is an AI competition among students which is held by MIPT university, Yandex, Sber and Ministry of science and higher education of the Russian Federation.

## ✍️ What was the task this year?

The popularity of the 🤖 chat-GPT has also affected this competition. The task was to classify the dialogues in order to find which were conducted by AI system and which were conducted by people (**Text Generation Detection**).

# 🏆 What is our result?

🥉 3 place, ~ 0.9 F1 score.

# 💾Data

We had about 6k dialogues for training and about 1k for prediction on public leaderbord and 1k on private dataset and all teams had only one attempt to load sumbit on private dataset. As we found out, the public liderboard containded mostly dialogues with people and that's why most of overfitted models of other participants were quite good for public submissions but weren't as good for private lidearboard.

## How the data were presented?
![image](https://github.com/MaksKhan/RuCode_6.5/assets/72515541/274d8000-c244-455a-832e-857ac3327f4e)

### Typical sample:

Context:

1 (👱): Спасибо большое)).
Какую музыку слушаешь?

2 (🤖 or 👱): русский рэп в основном.
ну там, фейс, элджей знаешь же?
или что ты слушаешь?).

1 (👱): Эм..нет😱.

Answer:

2 (🤖 or 👱): Ой, ну тогда давай я тебе порекомендую что-нибудь послушать? Я недавно открыл для себя классический рок, например, Queen, Led Zeppelin, Pink Floyd - это просто космос!


## ❔ What did we have to predict?

First interlocutor  was a man always. However the other one could be an AI. So the task was to understand who the second interlocutor is.



# 💻 Our solution

## 😼 Baseline
💀Firstly we have choisen logistic regression & tf-idf. However, it was always overfitting.

😺 CatBoost was a good choice for the baseline as it can be trained just on texts and it wasn't overfitting.

The F1-score was around 0,84.

## 🎖️ The best model

✔️ Of course we immediately started to use BERT models in order to get high score.

### Results
![image](https://github.com/MaksKhan/RuCode_6.5/assets/72515541/cd6a3dd8-856b-4ce5-b8c0-4243502a74e5)

🏆	 As you can see, **DeepPavlov** model was the best for our task as it was trained on russian dialogues from social networks. Furthemore, it had the most balanced results on validation.

## 🤔 Different ideas 

### ⚜️ BERT embeddings & CatBoost
We trained CatBoost on Bert embeddings. The score was about 0.87 on validation. Unfortunately we didn't have enough time to improve this idea.

### 🔱 BERT embeddings & NN

This unorthodox approach was new for us and we were wondering if it is possible to get a good result. So, it was and we got about 0,86 on validation.

### 🔆 BERT embeddings & CatBoost & Sentimental analysis

As we know, BERT models and CatBoost are really different models. So what if we unite them? 

#### 💚 Sentimental analysis
We have used another model from DeepPavlov in order to make sentimental analysis. As expected, only people's responses were negative and most of positive answers were received from AI system). It was really good feature for CatBoost

Unfortunately, we checked this idea on the last day of competition so we didn't have time to make a submission(

### 💀 Training our own Dialogue System

We had an idea of traning our own dialogue system. We wanted to generate answers and then compare them to original answers. If answers are similar enough, that means that interlocutor was an AI.

# 📖 Result

🥉 **3 Place**

We have sent only predictions of **DeepPavlov**. Literally a couple of minutes was not enough to upload the result of the stacking of the best models)

