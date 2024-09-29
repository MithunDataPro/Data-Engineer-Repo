## What’s common between Machine Learning and us?

Machine Learning is an art. It is an art in which the computer learns. We start learning since we were infants and continue to grow and develop ourselves. Similarly, we have models in Machine Learning which are like infants. They do not know anything by themselves. They have to learn from the data similar to the way we humans learn. To make these infant models learn we need to take a closer look at how humans learn. Then we can try to simulate this idea of learning to our models.

Human learning is highly accurate and very reliable. It is very logical to have mechanisms for a computer to learn very similar to the way humans learn.

Let us understand “The Art” of how humans learn and relate it back to Machine Learning.

### The Three Arts of Learning:

## Supervised Learning:
The first art is supervised learning. Most of the things that we learn are taught by others, that is someone else supervises our task. Suppose you are learning football, the coach might have shown you a video of dribbling, you now try to simulate the same thing. This is called learning under supervision or guided training, also technically called supervised learning.

### How does this link back to Machine Learning?

In Machine Learning we need to train models. These models try to simulate what we do in our brains. They simulate the way we learn and try to understand the given data the way we do.

Let’s take an example to get our heads clear.
How do we recognize if the given animal is a dog or cat and classify accordingly?

![image](https://github.com/user-attachments/assets/661dbb20-fa48-4809-8d47-cfd1f2b6f251)


Your mother (your first teacher) might have shown you a labelled image of a cat and told you this is a cat. Also, she would have shown you a labelled image of a dog and said that this is a dog. Eventually, with multiple real-world examples, your brain learnt to distinguish between dog and cat.

Similarly, it would make sense if we give our model some kind of labelled data to learn i.e. we would give it multiple images saying this is a dog and multiple images saying this is a cat. The model will have to learn from this data and in the end, be correctly able to distinguish dog and cat.

This art of learning is called supervised learning. Supervised learning is used when we have labelled data, that is data with some input and well-known output.

But wait……

You learnt how to distinguish between dog and cat by seeing the images and training your brain.

How will the model “learn” to distinguish between dog and cat?

For this, we need a learning algorithm which I will tell you soon.
(Hold on guys 😁 I can’t tell all the story at once)

Let us move to the second art.


## Unsupervised Learning

Imagine I gave you this data.

![image](https://github.com/user-attachments/assets/4f931628-0d32-4800-8ef0-51046dcae906)


And now asked you to naively group these data points (the blue dots) into three different zones, or regions.

How would you group?

Let us make this a bit tricky.

I have a certain grouping in my mind, can you too group this in the same way?

Sounds tricky, right??  
Think about this for a while…

![image](https://github.com/user-attachments/assets/4722e0ec-94d4-471f-8466-563a093bcdbc)


Probably you might have thought of this grouping. It may not be the same grouping as I have in my mind though.  
Think about this way of learning in real life.  
E.g. You learnt to group cats and dogs into a single class called animals. When shown another animal say horse, you again add that to your group of animals.  
In some sense, you learn to group the objects based on some similarity measure that you have seen before and then add some more objects to the group that satisfy the property.

### How is this art of learning different from supervised learning?

In this art of learning, I never told you how to group the data. I never supervised over how you are grouping, or rather never even guided you while you were grouping.  
But I know one thing, the correct groups which I had in my mind. I can use them to say whether you are doing right or wrong.  
This is the trick in unsupervised learning, we call this situation as having data without labels, (unlike the previous case where I gave you cat and dog as labels) this is a tricky situation where you do not know the relationships within the data.  
Your job is to find the relation between the data. In this case, it was grouping; you could try different ways of grouping, and in the end, arrive at some relationships within the groups.

### How does a Machine Learning model learn this data?

You need a model which will work for unlabelled data. You need a different approach where the model inherently tries to find some relationships within data itself.  
This again requires a different learning mechanism which I will introduce to you soon. Just remember that this isn’t the same as supervised learning.

