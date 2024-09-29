# The Machine Learning Theory: Supervised Learning

The Machine Learning theory is split into three domains namely **Supervised Learning**, **Unsupervised Learning**, and **Reinforcement Learning**.

![image](https://github.com/user-attachments/assets/1b615c6e-22fa-48b1-b251-c9c9ad12e931)

---

## What is Supervised Learning?

Let me tell you what **Supervised Learning** is in one line.

**Teach me and I will learn.**

Supervised learning requires someone to **guide us while we are learning**.  
This is the most natural way in which humans learn as well. We are taught how to write and read, and we are taught how to do arithmetic. If this form of learning is very natural, then making computers learn in this way is a great idea.

Supervised learning is the most common form of learning that we encounter in Machine Learning. In fact, **Andrew Ng** once said that more than **80% of problems involve supervised learning**. Supervised learning spans multiple domains such as **Regression Algorithms, Neural Networks, Decision Trees, Support Vector Machines**, to name a few. (In case you don’t know them it’s okay, we will look into them soon.)  
**Supervised Learning** is a very powerful technique as it tends to be far more accurate than the other two.

---

## The Problem of Many Algorithms in Supervised Learning

People often complain:

**There are too many algorithms in Supervised Learning.**  
Is there any general recipe?

True, there are many algorithms in this domain. It is difficult to understand them and correlate, as all try to solve similar problems.  
**All the supervised learning algorithms have 6 things in common.**  
Let us make **6 jars** and then see them one by one.

![image](https://github.com/user-attachments/assets/17895910-6899-4154-bfd4-02ea97737bf4)


---

### 1. Data (Always necessary)
### 2. Task (We don’t solve a problem without knowing what is our task 😃)
### 3. Model (Yes! You heard it right, that same word from my previous blogs)
### 4. Loss Function (Don’t worry I will explain this 😅)
### 5. Learning Algorithm (A generic algorithm for all 😇)
### 6. Evaluation Technique (Nothing is learnt till it’s not evaluated 😃)

---

## The Data Jar

We consider **real-world data** here. Recall that in supervised learning, we require **labelled data**—i.e., data which has the **attributes (X values)** and **labels (Y values)**.

Let’s take an example to make this clear.

Suppose you have a **tabular data**, maybe the data is regarding your medical profile and says whether you are **healthy or not**.

![image](https://github.com/user-attachments/assets/69568a77-c1be-43e4-983b-f610b9e477c5)


---

**Data Example (Medical Profile):**
- **Attributes (X values):** Age, Blood Group, Gender, BP, Sugar value, etc.
- **Label (Y value):** Healthy or Unhealthy

Now we are given this data, we need to define a task for the data.

---

## The Task Jar

The **task jar** decides what needs to be done with the data. In supervised learning, we can have only two tasks:

1. **Regression**
2. **Classification**

![image](https://github.com/user-attachments/assets/7aea5274-823b-40f4-ae84-5b41ab0930e6)

Let us dive into them briefly.

---

### Regression Tasks:  
In **Regression**, we try to **predict or forecast** a future value based on current data. Examples of this are **stock market predictions** and **weather forecasting**.

![image](https://github.com/user-attachments/assets/21ab4a30-560e-45d0-9c71-65acba91366b)

Think about it, how do we predict tomorrow’s weather? We think about various factors such as the season, today’s weather, some reports from news, personal experience and hence we say what tomorrow’s day will be. Regression tries to perform the same analysis on the data; it tries to **learn from the previous values and forecast the future.**

---

### Classification Tasks:  
The first problem we discussed in the data section about whether a person is **healthy or not** is a **classification task**.  
**Binary Classification** is when we classify a data point into **one of two possibilities**, e.g., healthy or unhealthy.

![image](https://github.com/user-attachments/assets/99157b89-13d4-4e40-b669-72dd3092862d)


Let’s take another example:  
Suppose I give you data of **handwritten digits (0-9)**. After this, I pick any one data point and ask you which digit it is. You have 10 choices here to choose from, right? The digit belongs to only one of them.  
This is called **Multi-Class Classification**.

---

### Summary of Supervised Learning Tasks:

- **Regression**: Predict continuous outcomes (e.g., predicting the temperature tomorrow).
- **Classification**: Categorize data points into discrete groups (e.g., predicting if the weather will be hot or cold).

---

This way of classifying a data point into one of two possibilities or predicting continuous outcomes forms the basis of **Supervised Learning**.

---


