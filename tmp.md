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
        - [About action](#about-action)
        - [What is context?](#what-is-context)
            - [Creating your first context](#creating-your-first-context)

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

By accessing the entity value within the response, you have the ability to create a dynamic response that can map the ordinal value to the president's name. `$president-number.original` refers to the user's ordinal input, first president, and `$president-number` refers to the ordinal value mapped to the name George Washington in the president-name entity. The response The `$president-number.original` of `$geo-country` is `$president-number` creates a proper answer to the user's question about who was the first or second President of the USA. When you test this in Google Assistant in Dialogflow, you will see that the proper response gets returned: The second president of USA is John Adams.

3. Now, create a second question that does not have a geo-country, USA: _Who is first president?_, and create an equivalent response `The $president-number.original is $president-number`. The `FaqChatBot` agent will be smart enough to figure out that if the geo-country is omitted in the question, the agent will use the response that does not have `$geo-country`. The following screenshot shows the completed Find President intent:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/ff4b0c47-6ad7-44e9-9441-57fbfb0e54fc.png)

Find President intent

### About action
`Action` in Dialogflow is a rather simple concept. In the previous section, you created an intent using the template _who is the first president?_. Action in the FaqChatbot agent is responsible for extracting parameters such as `@president-number` and `@sys.geo-country` from the intent. Typically, you do not have to define the name of the action, as Dialogflow will automatically add the action name, but you can also give the action name manually, `president_number`, as shown:The following screenshot shows the action:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/8fe4b4eb-d2a5-4c25-b884-e6e0f6b78a18.png)

Action

### What is context?
`Context` is like a session, where previous session information is maintained so that the next context can have access to that session information. For example, upon meeting a stranger in a bar, you initiate a conversation, asking the name of the person you are speaking with. From that point on, you know his or her name and you might use his or her name during the conversation. Another example is during a conversation, where you are asked the ambiguous question, "When is his birthday?" by a friend, but you do not know who "he" refers to, in which case, you might ask your friend who he or she is referring to. When your friend explains that they are asking about John Doe's birthday, you have successfully established the context that "he" refers to John Doe.

In Dialogflow, contexts can also be used to establish and control conversational flow, allowing only a specific intent to be triggered if specific contextual requirements are met. For example, during the checkout process in an e-commerce store, you only allow the user to buy an item if all the necessary requirements are gathered, such as credit card information and a shipping address.

#### Creating your first context
The following flowchart shows the conversational flow that you will learn to build for `FaqChatBot`, which is asking about the Presidents' birthdays:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/2d02d9b4-2482-413a-9c97-b7823c097e88.png)

President Birthday Context flow diagram

1. In `FaqChatBot`, you will find the list of intents created by Dialogflow: Default Fallback Intent and Default Welcome Intent. The following screenshot shows the default welcome and fallback intents:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/b9433e5a-6f80-496e-b7a4-3ba78b2e7188.png)

Default welcome and fallback intents

2. The Default Welcome Intent is triggered the very first time the user uses `FaqChatBot`. Modify the Default Welcome Intent by changing the text response to _Hi! Welcome to FAQ Chatbot. What is your name?_ so that the user will be greeted and asked what his or her name is. The following screenshot shows the modified Default Welcome Intent text response:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/52120448-da88-469d-a613-333fa0887a2b.png)

Modified default welcome intent text response

3. Create Get Name and, in the Contexts section, type in `GET_NAME` in the Add output context textbox. `GET_NAME` can now be used as the input context in other intents, allowing other intents to access all the parameters captured by the Get Name intent.
4. From the `@sys.given-name:username` template or `my name is @sys.given-name:username`, the intent will extract the username `@sys.given-name:username` and store it in the `$username` variable.
5. Create a personalized text response using the user's name stored in the `$username` variable, `$username` you can ask me anything about the president of America. The following image shows the Get Name intent, which gets triggered when the user responds with his or her name: 

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/de2f0be8-0256-4892-b41d-5611dcbcf2b8.png)

Get name intent context and user says

The following screenshot shows the username variable, which contains the captured username found in the Action section of the Get Name intent:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/a40af000-fe6f-41f7-882d-8ce70ed01d56.png)

Get name intent action and response

Notice that there is a number 5 next to the GET_NAME context. This number defines the lifespan of the context. The number 5 means that the context will be available for the next 5 requests or for the next 10 minutes after the time context is activated. You can simply increase the lifespan number by editing the number to something greater. This will all depend on the use cases for the context.

6. Before we can start creating the intent that can use the `GET_NAME` context, let's create a new entity for the Presidents' birthdays, called `president-birthday`, using JSON. The following code shows the `president-birthday` entity:

```json
[
    {
        "value": "December 14, 1799",
        "synonyms": [ "George Washington" ]
    },
    {
        "value": "October 30, 1735",
        "synonyms": [ "John Adams" ]
    }
]
```

7. Once the `president-birthday` entity has been created, you can create the Get President Birthday intent, as shown in the following screenshot. Notice that, in the Contexts section, there is the `GET_NAME` context as the input context, which comes from the output context of the Get Name intent. By adding the `GET_NAME` context as the input, the Get President Birthday intent has access to all the parameters in the `Get_Name` intent.
8. In the Action section, you can add the parameter called username, which maps to the parameter from the Get Name intent, `#GET_NAME.username`. The following screenshot shows the get President Birthday intent, which shows the username variable mapping to `#GET_NAME.username`:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/591cc099-592c-4d54-9dc0-b0380cfaf2a0.png)

Get President Birthday intent