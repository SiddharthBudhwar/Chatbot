# Chatbot

## Introduction
Chatbots are extremely helpful for business organizations and also the customers. The majority of people prefer to talk directly from a chatbox instead of calling service centers. Facebook released data that proved the value of bots. More than 2 billion messages are sent between people and companies monthly. The HubSpot research tells us that 71% of people want to get customer support from messaging apps. It is a quick way to get their problems solved so chatbots have a bright future in organizations.

Today we are going to build an exciting project on Chatbot. We will implement a chatbot from scratch that will be able to understand what the user is talking about and give an appropriate response.

## Prerequisites
To implement the chatbot, we will be using Keras, which is a Deep Learning library, NLTK, which is a Natural Language Processing toolkit, and some helpful libraries. Run the below command to make sure all the libraries are installed:

pip install tensorflow keras pickle nltk

## How do Chatbots Work?
Chatbots are nothing but an intelligent piece of software that can interact and communicate with people just like humans. Interesting, isn’t it? So now let's see how they actually work.

All chatbots come under the NLP (Natural Language Processing) concepts. NLP is composed of two things:

NLU (Natural Language Understanding): The ability of machines to understand human language like English.

NLG (Natural Language Generation): The ability of a machine to generate text similar to human written sentences.

Imagine a user asking a question to a chatbot: “Hey, what’s on the news today?”

The chatbot will break down the user sentence into two things: intent and an entity. The intent for this sentence could be get_news as it refers to an action the user wants to perform. The entity tells specific details about the intent, so "today" will be the entity. So this way, a machine learning model is used to recognize the intents and entities of the chat.

## Project File Structure
After the project is complete, you will be left with all these files. Lets quickly go through each of them. It will give you an idea of how the project will be implemented.

->Train_chatbot.py — In this file, we will build and train the deep learning model that can classify and identify what the user is asking to the bot.

->Gui_Chatbot.py — This file is where we will build a graphical user interface to chat with our trained chatbot.

->Intents.json — The intents file has all the data that we will use to train the model. It contains a collection of tags with their corresponding patterns and responses.

->Chatbot_model.h5 — This is a hierarchical data format file in which we have stored the weights and the architecture of our trained model.

->Classes.pkl — The pickle file can be used to store all the tag names to classify when we are predicting the message.

->Words.pkl — The words.pkl pickle file contains all the unique words that are the vocabulary of our model.

## Methodology

### Step 1 :- Import Libraries and Load the Data
Create a new python file and name it as train_chatbot and then we are going to import all the required modules. After that, we will read the JSON data file in our Python program.

### Step 2. Preprocessing the Data
The model cannot take the raw data. It has to go through a lot of pre-processing for the machine to easily understand. For textual data, there are many preprocessing techniques available. The first technique is tokenizing, in which we break the sentences into words.

By observing the intents file, we can see that each tag contains a list of patterns and responses. We tokenize each pattern and add the words in a list. Also, we create a list of classes and documents to add all the intents associated with patterns.

Another technique is Lemmatization. We can convert words into the lemma form so that we can reduce all the canonical words. For example, the words play, playing, plays, played, etc. will all be replaced with play. This way, we can reduce the number of total words in our vocabulary. So now we lemmatize each word and remove the duplicate words.

In the end, the words contain the vocabulary of our project and classes contain the total entities to classify. To save the python object in a file, we used the pickle.dump() method. These files will be helpful after the training is done and we predict the chats.

### Step 3. Create Training and Testing Data

To train the model, we will convert each input pattern into numbers. First, we will lemmatize each word of the pattern and create a list of zeroes of the same length as the total number of words. We will set value 1 to only those indexes that contain the word in the patterns. In the same way, we will create the output by setting 1 to the class input the pattern belongs to.

### Step 4. Training the Model
The architecture of our model will be a neural network consisting of 3 dense layers. The first layer has 128 neurons, the second one has 64 and the last layer will have the same neurons as the number of classes. The dropout layers are introduced to reduce overfitting of the model. We have used the SGD optimizer and fit the data to start the training of the model. After the training of 200 epochs is completed, we then save the trained model using the Keras model.save(“chatbot_model.h5”) function.

### Step 5. Interacting With the Chatbot
Our model is ready to chat, so now let’s create a nice graphical user interface for our chatbot in a new file. You can name the file as gui_chatbot.py

In our GUI file, we will be using the Tkinter module to build the structure of the desktop application and then we will capture the user message and again perform some preprocessing before we input the message into our trained model.

The model will then predict the tag of the user’s message, and we will randomly select the response from the list of responses in our intents file.

### Chatbot working 
![Screenshot 2021-10-24 152440](https://user-images.githubusercontent.com/74424623/138589073-92a92a9b-feb2-44be-9789-58ecbf4454ab.png)





