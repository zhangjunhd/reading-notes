# Voice User Interface Projects
![cover](https://www.safaribooksonline.com/library/cover/9781788473354/)

    by Henry Lee
    Publisher: Packt Publishing
    Release Date: July 2018
    ISBN: 9781788473354
    Topic: Chatbots

[safaribooks](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/)

<!-- TOC -->

- [Voice User Interface Projects](#voice-user-interface-projects)
    - [Building an FAQs Chatbot](#building-an-faqs-chatbot)
        - [What are intents?](#what-are-intents)
            - [Creating your first intent](#creating-your-first-intent)
        - [What are entities?](#what-are-entities)
            - [Using entities](#using-entities)

<!-- /TOC -->

## Building an FAQs Chatbot
### What are intents?
Dialogflow is a platform with complicated machine learning and artificial intelligence capabilities that matches what the user said to the `intent`. You can think of intents as questions that users will be asking about U.S. Presidents. When you first start with the FaqChatBot agent in Dialogflow, you will see two default intents: the `Welcome Intent` and the `Fallback Intent`, as shown in the following flowchart.

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/9bd95b24-d1a5-4a3f-9526-b30ab07c9550.png)

#### Creating your first intent
The following screenshot shows the `First-President` intent that was created in Dialogflow:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/1c41dcfd-7879-491f-9d75-13a813800720.png)

First, notice that when you enter _Who is the first president of USA?_ into the User says input box, the words `first` and `USA` are highlighted in yellow and orange, respectively. Dialogflow automatically identifies the word first as the type `ordinal (@sys.ordinal)` and the word USA as the type `geo-country (@sys.geo-country)` and basically creates a templatized question. The FaqChatBot agent will use those parameters to match against the user's question. 

When you type _who is the first president of USA?_, it shows the matching intent name `First-President`, and two parameters, `geo-country` as `United States of America` and `ordinal 1`, which are used to match the intent. 

### What are entities?
`Entities` are like keywords that are used to extract values from voice input. As seen in the previous section, Creating your first intent, the intent used the Dialogflow system entities `@sys.ordinal` and `@sys.geo-county` to extract the values **1** and **USA** from the voice input. The entities also help to create templatized questions so that you do not have to enter multiple variations of questions that result in the same answer. 

#### Using entities
In the `First-President` intent, you noticed that the intent had a problem answering the question _who is the second president of USA?_ because the response was static, only replying with the first president, George Washington, and not the second president, John Adams, regardless of which ordinal positions were given by the user. Let's address this issue by dynamically creating the response using an entity:

1. Let's start by creating an entity called `president-number`. In the first column, add the presidents' names, and in the second column, add the ordinals that match the president. The following screenshot shows the `president-number` entity:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/1d083ebc-3504-4bd4-bb57-5174f8f462e6.png)

Creating a president-number entity

2. Now, create a new intent called `Find President`. Enter _who is the first president of USA?_ in the User says textbox and then highlight the words `first president` and you will see that a drop-down pops out, where you can search and select the entity that you created, called `president-number`. The following screenshot shows the process of mapping the entity to the highlighted word:![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/1fdb1e43-a5f8-4643-9e2b-706bda26cf64.png)

Mapping an entity to a word

By accessing the entity value within the response, you have the ability to create a dynamic response that can map the ordinal value to the president's name. $president-number.original refers to the user's ordinal input, first president, and $president-number refers to the ordinal value mapped to the name George Washington in the president-name entity. The response The $president-number.original of $geo-country is $president-number creates a proper answer to the user's question about who was the first or second President of the USA. When you test this in Google Assistant in Dialogflow, you will see that the proper response gets returned: The second president of USA is John Adams.

3. Now, create a second question that does not have a geo-country, USA: _Who is first president?_, and create an equivalent response `The $president-number.original is $president-number`. The `FaqChatBot` agent will be smart enough to figure out that if the geo-country is omitted in the question, the agent will use the response that does not have `$geo-country`. The following screenshot shows the completed Find President intent:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/ff4b0c47-6ad7-44e9-9441-57fbfb0e54fc.png)

Find President intent
































