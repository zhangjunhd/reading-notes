![cover](https://www.safaribooksonline.com/library/cover/9781788473354/)

    Voice User Interface Projects
    
    by Henry Lee
    Publisher: Packt Publishing
    Release Date: July 2018
    ISBN: 9781788473354
    Topic: Chatbots

[safaribooks](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/)

<!-- TOC -->

- [Building an FAQs Chatbot](#building-an-faqs-chatbot)
    - [What are intents?](#what-are-intents)
        - [Creating your first intent](#creating-your-first-intent)
    - [What are entities?](#what-are-entities)
        - [Using entities](#using-entities)
    - [About action](#about-action)
    - [What is context?](#what-is-context)
        - [Creating your first context](#creating-your-first-context)
        - [No context](#no-context)
        - [Testing context and no context scenarios](#testing-context-and-no-context-scenarios)
    - [Machine learning classification threshold](#machine-learning-classification-threshold)
    - [Training data](#training-data)
- [Building a Fortune Cookie Application](#building-a-fortune-cookie-application)
    - [About the Fortune Cookie project](#about-the-fortune-cookie-project)
    - [About webhook](#about-webhook)
    - [Setting up an agent](#setting-up-an-agent)
    - [Enabling webhook](#enabling-webhook)
    - [Building a Get Quote intent](#building-a-get-quote-intent)
    - [Handling the Get Quote intent from the Webhook](#handling-the-get-quote-intent-from-the-webhook)
    - [Building a Get Quote based on the user feelings](#building-a-get-quote-based-on-the-user-feelings)
        - [Building a Feeling entity](#building-a-feeling-entity)
        - [Building events to get Feeling-based quotes](#building-events-to-get-feeling-based-quotes)
        - [Building a Custom Welcome intent](#building-a-custom-welcome-intent)
        - [Building a get feeling custom follow-up intent](#building-a-get-feeling-custom-follow-up-intent)
        - [Writing code for a feeling custom follow-up intent](#writing-code-for-a-feeling-custom-follow-up-intent)
- [Building a Get Fortune Cookie by an author](#building-a-get-fortune-cookie-by-an-author)
    - [Building an Author entity](#building-an-author-entity)
    - [About rich response](#about-rich-response)
    - [Creating a text response](#creating-a-text-response)
    - [Creating an image response](#creating-an-image-response)
    - [Creating quick replies](#creating-quick-replies)
    - [Creating a card response](#creating-a-card-response)
    - [Creating a listSelect response](#creating-a-listselect-response)
    - [Building a Get Authors intent](#building-a-get-authors-intent)
        - [Building a listSelect response in code](#building-a-listselect-response-in-code)
    - [Building a Get Author Quote intent](#building-a-get-author-quote-intent)
        - [Building a Get Author Quote intent's webhook](#building-a-get-author-quote-intents-webhook)
    - [Integrating SSML and audio to Default Welcome intent](#integrating-ssml-and-audio-to-default-welcome-intent)
    - [Using Analytics](#using-analytics)

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

9. You can create the text response using the `$username` variable, making the response more personable by using `$username $president-birthday.original's birthday is on $president-birthday`.

#### No context
In the previous section, we used the context from the external intent Get Name to get the data needed for the Get President Birthday intent. What if you do not always want to use the context, but simply want to ask the user for the missing data?

1. In the User says section, add  `I want to know @president-birthday:president-birthday`. Notice that the `president-birthday` parameter in the Action section is automatically added.
2. Have a REQUIRED checkbox checked for `president-birthday`.
3. Click on the Define prompts link that appears in the PROMPTS column.
4. Enter the prompt that asks, Which president's birthday would you like to know?.

The following screenshot shows steps 2 to 4 with the required parameter, `president-birthday`:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/8d7252a8-4061-4b03-af92-02c09b3eb1a9.png)

No context

The following screenshot shows the default prompt if the required parameter, president name, is not given:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/d6932084-0581-49b5-b67b-b7e5d280febb.png)

Default prompt for the required parameter

When the user asks `what is his birthday?`, the Get President Birthday intent will get triggered, but since no `president-birthday` entity is captured from the user's request, the intent will prompt the user with Which president's birthday would you like to know? As soon as the user gives the answer, the intent will provide a response.

#### Testing context and no context scenarios
Let's test the context using Google Assistant simulator from the Dialogflow console. In the Try it now textbox, enter `my name is Henry` and you will see the response, Henry you can ask me anything about the president of America. Notice that, in the Contexts section, it shows that the `GET_NAME` context is set and also has the username parameter value of `Henry`.

The following screenshot shows us testing the `get_name` context:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/36f763aa-8f15-4c9a-9f67-f9e5633768f1.png)

Testing the get_name context

If you enter the next question, `I want to know John Adams' birthday`, you will see that the response contains the username when responding about the president's birthday.

The following screenshot shows the debugger showing the Get President Birthday intent with the `get_name` context:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/144bd266-8689-4c02-abf2-24b357bfb38d.png)

Testing the Get President Birthday intent with the get_name context

Test out the no context scenario by typing in, `What is his birthday?`. The intent will trigger the prompt, asking Which president's birthday would you like to know? When you respond with `George Washington`, the response returns George Washington's birthday.

The following screenshot shows the intent triggering the prompt, asking the user which president's birthday they would like to know about:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/f5de98fb-3e3f-49d8-bee8-bd5efd4ed8ac.png)

Testing no context

The following screenshot shows the chatbot providing the president's name as a response to Get President Birthday:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/af3872d0-9b48-4675-a901-d73c9a9b8b55.png)

Providing the president's name as a response

### Machine learning classification threshold
The machine learning classification threshold basically defines the confidence level percentage that the user request matches the intent. In Dialogflow, you can find this by clicking on the FaqChatBot agent setting and going to ML Settings.

The following screenshot shows the ML Settings section of the `FaqChatBot` agent:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/e7df0d0a-c0bb-4d37-8f08-41f8f3e03e79.png)

Machine learning classification threshold

### Training data
So, what do you do with those that did not have any intents to match? Rather than ignoring unknown requests, send them back into the system to train the Dialogflow agent.

Let's see this in the following example. Go to the simulator and say `I am Henry`, and the returned response will show that the intent is unknown. The following screenshot shows the unknown input:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/3260408c-3d00-401d-b5f1-44a1aa2090b1.png)

Unknown input

In Dialogflow, click Training, and you will notice that it lists unknown inputs where no matching intents are found.

The following screenshot shows the training data list, where you can find unknown inputs:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/c8d1cd7e-61e7-4e23-9d61-1c4fff48fc3a.png)

Training data list

One of the inputs is i am henry. If you click on i am henry, you will see that it requires approval and also requires the proper intent to be assigned. So, go ahead and assign the Get Name intent and approve it. Once approved, you will see a green checkmark.

The following screenshot shows the window where you can approve and assign an unknown input to an existing intent:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/20859757-ae10-4328-883a-be20a8093c1e.png)

Approving and assigning the "I am Henry" input to the Get Name intent

Now, go to the Get name intent and you will notice that I am henry is matched with the proper entity applied. Over time, you can monitor the Training section data and learn what users are asking, and then you can create or update intents.  Over time, the Dialogflow agent will become smart enough to handle multiple variations of questions, but asked differently. Having to anticipate every possible combination is not humanly possible. Although it is difficult, the ability to train a machine to learn and anticipate the future is as simple as being a few mouse clicks away in Dialogflow. The following screenshot shows an unknown input assigned to the Get Name intent:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/2297f755-db2a-4b49-a574-58ed41511fe2.png)

Unknown input assigned to Get Name intent

## Building a Fortune Cookie Application
### About the Fortune Cookie project
The Fortune Cookie application will be able to respond to the following set of remarks:

- Tell me a quote
- Give me a fortune cookie
- I feel sad/happy
- Show me authors

### About webhook
In Dialogflow, the concept of allowing your middle-tier server to serve responses dynamically is called `fulfilling intents through webhook`. Dialogflow provides a built-in Node.js server to handle simple requests dynamically.

The following flowchart shows a simple webhook architecture:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/ac623626-0008-4c7f-9da4-bbe1e9356f59.png)

Webhook architecture

### Setting up an agent                                    
First, log in to the Dialogflow website and a create new agent called `FortuneCookie`. Make sure to enable Dialogflow V2 API and leave the rest of the settings leave as their defaults.                 

The following screenshot shows the `FortuneCookie` agent creation settings:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/c33752b0-21b9-439b-a36e-0b76f7743c9c.png)

Creating a FortuneCookie agent

### Enabling webhook
Before we start to build the Fortune Cookie application, let's enable the webhook feature of Dialogflow so that all intents can be routed to the Dialogflow Node.js server.

1. In Dialogflow, go to Fulfillment and enable Inline Editor. This will allow you to enter Node.js code into the editor.

The following screenshot shows enabling webhook in the Dialogflow fulfillment:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/61a7dfa1-27bb-4477-bae2-fb470c607829.png)

The text in this screenshot is not important. This image gives you an idea of how to enable webhook

2. Notice that there are default codes. First, let's replace those codes by declaring Google Cloud Functions for Firebase.

```js
'use strict';

const firebase = require('firebase-functions');
```

Dialogflow's built-in Node.js server uses Google Cloud Functions for Firebase, which allows you to write code that intercepts HTTPS events. For example, when an intent is triggered, Dialogflow will send a HTTPS request to Firebase and allows Google Cloud Functions to execute. In this case, the Google Cloud Function triggered is the code that you will be writing in the Dialogflow Inline Editor.

3. Next, capture the HTTPS request and response. The request object will contain a Dialogflow request (http://bit.ly/2Gnj31K) and send back the response (http://bit.ly/2rNf0Zn) to Dialogflow so that it can properly answer the user's intent.

The following code intercepts the HTTPS request initiated by Dialogflow when the intent is triggered and the Firebase event is notified firebase.https.onRequest:

```js
var request, response;
exports.dialogflowFirebaseFulfillment = firebase.https.onRequest((req, res) => {  
    request = req;  
    response = res;    
    console.log('Fortune Cookie Request headers: ' + JSON.stringify(request.headers));  
    console.log('Fortune Cookie Request body: ' + JSON.stringify(request.body));  
    if (request.body.queryResult) {    
        processV2Request();
    } else {
        console.log('Invalid Request');    
        return response.status(400).end('Invalid Webhook Request');  
    }
});
```

4. Now let's create intent handlers that will create proper responses to Dialogflow requesting that the server handles the user's intents. By default, two intents will always be created when the agent is created: Default Fallback Intent and Default Welcome Intent. 

The following code shows handlers that respond to the fallback (input.unknown) and the welcome intent (input.welcome):

```js
const intentHandlers = {  
    'input.welcome': () => {    
        sendResponse('Hello, Welcome to Henry\'s Fortune Cookie!');   
    },  
    'input.unknown': () => {    
        sendResponse('I\'m having trouble, can you try that again?');   
    },  
    'default': () => {    
        sendResponse('This is Henry\'s Fortune Cookie!');  
    }
};
```

An intent in Dialogflow is associated with an action and when Dialogflow sends a request to the Node.js server, the request body will contain `queryResult.action`, which will map to the `intentHandlers` functions, where the proper text response will be sent to the user. For the welcome intent, the _Hello, Welcome to Henry's Fortune Cookie!_ response will be sent to Dialogflow and then to the user. For `input.unknown`, which is the fallback intent, the _I'm having trouble, can you try that again?_ response will be sent back. If for some reason, the action is never sent by Dialogflow, the default intent handler will send the _This is Henry's Fortune Cookie!_ response.

The following image shows the Default Welcome Intent with the Action name `input.welcome` used in the code and also, in the Fulfillment section, Use webhook is checked, which will allow the intent to be handled in the code:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/d27daa1a-dd9b-4a13-af14-14f3dfd49a84.png)

Default Welcome Intent with Action name and Enabling Webhook

5. Let's create a `sendResponse` function that will respond with a simple response. First, we need to build the Dialogflow response object that contains the `fulfillmentText` property. Finally, the response object will be logged and the response will be sent to Dialogflow. `fullfilmentText` will be used by Dialogflow to translate text into the voice and the response will be spoken to the user.

The following code describes the `sendResponse` function, which will build Dialogflow's simple text response, which will be translated into voice and sent to the user:

```js
function sendResponse (responseToUser) { 
    let responseJson = { fulfillmentText: responseToUser };
    console.log('Response to Fortune Cookie: ' + JSON.stringify(responseJson)); 
    response.json(responseJson);
}
```

The following code stitches together everything we've built so far and processes the request by extracting the action from `request.body.queryResult.action` and sending the response back to Dialogflow by executing the intent handler:

```js
function processV2Request () {  
    let action = (request.body.queryResult.action) ? request.body.queryResult.action : 'default';  
    if (intentHandlers[action]) {     
        intentHandlers[action]();  
    } else {    
        intentHandlers['default']();     
    }
}
```

### Building a Get Quote intent                             
First, let's build an entity that contains the keywords `Fortune Cookie` and `Quote`.  The following code shows the `Fortune` entity, which contains two keywords that will be used to match the user's request to the fortune cookie or the quote:

```json
[    
    {        
        "value": "Fortune Cookie",        
        "synonyms": [            
            "Fortune Cookie",            
            "Quote"        
        ]    
    }
]
```

Using the `Fortune` entity, create templatized questions for the Get Quote intent, as follows:

- @ Tell me a @Fortune.Fortune
- @ Give me @Fortune.Fortune

Now, a user will be able to ask a combination of questions using `Tell me` and the `Fortune` entity. For example, the user can say _Tell me a fortune cookie_ or _Tell me a quote_. Now, give it an Action name, `input.fortune`, which will capture the HTTPS request event and map it to the `intentHandler`. Finally, in Fulfillment, enable the Use webhook option.

The following image shows the Get Quote intent settings:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/2e5765db-19e6-486e-9d9d-9f2ea30d188e.png)

Get Quote intent

Note that the Get Quote intent has an empty text response. From here on, all intents will be routed to the webhook and the response will be programmatically created in the middle-tier server.

### Handling the Get Quote intent from the Webhook
You will be adding quotes to the Inline Editor that you just worked on. Go to Fulfillment in Dialogflow and add an array of nine quotes to the code. Notice here that there is author information and tags, which you will use to build the Get Author Quote intent.

The following variable array, named quotes, contains nine quotes, from which you will randomly select one and respond to the user when the Get Quote intent is triggered:

```js
const quotes = [  
    {    
        "author": "T. S. Eliot", 
        "tags": "happy",    
        "quote": "Do not stop to ask what is it;  Let us go and make our visit."  
    },  
    {    
        "author": "J. B. White", 
        "tags": "happy",    
        "quote": "at least I thought I was dancing, til somebody stepped on my hand."  
    }, 
    {    
        "author": "Dave Stutman", 
        "tags": "happy",    
        "quote": "Complacency is the enemy of progress."   
    }, 
    {    
        "author": "Winston Churchill", 
        "tags": "happy",    
        "quote": "Success is the ability to go from one failure to another with no loss of enthusiasm."  
    },  
    {    
        "author": "Woody Allen", 
        "tags": "happy",    "quote": "There's more to life than sitting around in the sun in your underwear playing the clarinet."
    },  
    {    
        "author": "Confucius", 
        "tags": "sad",    
        "quote": "It does not matter how slowly you go so long as you do not stop."  
    },  
    {    
        "author": "Mark Twain", 
        "tags": "sad",    
        "quote": "It usually takes me more than three weeks to prepare a good impromptu speech."      
    },  
    {    
        "author": "Albert Einstein", 
        "tags": "sad",    
        "quote": "Imagination is more important than knowledge."  
    },  
    {    
        "author": "Steven Wright", 
        "tags": "sad",    
        "quote": "You can't have everything. Where would you put it?"      
    }
];
```

Now, in `intentHandler`, you will need to add the `input.fortune` action in order to handle the Get Quote intent.

The following code shows `input.fortune` added to `intentHandlers`, which calls the `sendQuote` function:

```js
const intentHandlers = {  
    'input.welcome': () => {    
        sendResponse('Hello, Welcome to Henry\'s Fortune Cookie!');   
    },  
    'input.unknown': () => {    
        sendResponse('I\'m having trouble, can you try that again?');   
    },  
    'input.fortune': () => {    
        sendQuote();   
    },  
    'default': () => {    
        sendResponse('This is Henry\'s Fortune Cookie!' ); 
    }
};
```

In the `sendQuote` function, a number between 0 and 9 will be randomly generated using `Math.random()`, and then that randomly generated number will be used to select a quote from the array of quotes. The Dialogflow fulfillmentText response will be assigned with `quotes[randomNumber].quote.`

The following code shows the `sendQuote` function, where the Dialogflow response will be generated and sent using one of the quotes:

```js
function sendQuote () {  
    var randomNumber = Math.floor(Math.random() * 9);  
    let responseJson = { 
        fulfillmentText: quotes[randomNumber].quote };   
        console.log('sendQuote: ' + JSON.stringify(responseJson));  response.json(responseJson);}
```

### Building a Get Quote based on the user feelings
In this section, you will learn how to build a Feeling intent, where you will take the user's current feelings as input and properly display appropriate quotes that will go with the user's feelings. 

The following flowchart shows the flow of getting a quote based on the user's feeling:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/56db53ad-de23-4d09-b9b3-a73fdf8e7a5f.png)

Get Quote based on Feeling flow

#### Building a Feeling entity
In order to create an intent template to match the user's feeling, create a Feeling entity with `happy` and `sad`. The Feeling entity can be expanded to handle more diverse ranges of emotions such as anger, frustration, and fear. For the purpose of keeping the project simple, only two emotions will be added.

The following code shows the Feeling entity in JSON format, which can be imported into Dialogflow:

```json
[    
    {        
        "value": "happy",        
        "synonyms": [ "happy" ]    
    },    
    {        
        "value": "sad",        
        "synonyms": [ "sad" ]    
    }
]
```

#### Building events to get Feeling-based quotes
So far, you have learned about triggering intents by matching user requests. You have also used entities to create `templatized patterns` for what the user will be saying in order to create the intent. Another way to trigger an intent is to use an `event`. In an intent, there is a section called Events, where you can enter your own custom events and then, in the code, you can trigger the intent by simply referencing the event name you entered for the intent.

#### Building a Custom Welcome intent
The Custom Welcome intent does not contain any `User says` properties because it will be triggered by the Default Welcome intent. There will be a 50/50 chance that the Default Welcome intent will proceed normally by greeting the user and will wait for the user request or the Default Welcome intent will trigger the Custom Welcome intent, which will greet the user and ask them how they feel today. Create a Custom Welcome intent and, in the Events box, enter `custom_welcome_event`. Then, in Text response, add `Welcome to Henry's fortune cookie. How are you feeling today?`

The following image shows the Custom Welcome intent settings:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/26046a0b-fa86-40aa-962a-9d4d62d2c45b.png)

Custom Welcome intent

#### Building a get feeling custom follow-up intent
A follow-up intent is like any other intent you have created, the only difference being that a follow-up intent is chained after another intent as part of the follow-up conversation or to provide the user with confirmation. When creating a follow-up intent, you have the option to create a custom follow-up intent or use existing follow-up intents. Here are the pre-built follow-up intents that you can use (more information can be found at http://bit.ly/2Gwr98h)):

- yes: Used for affirmation (yes, do it, sure, exactly, of course)
- no: Used for negation (no, don't do it, definitely not, I disagree)
- later: Doing something later (later, not yet, ask me later, next time)
- cancel: Used for canceling an action (cancel, stop, dismiss, skip)
- more: Asking for more information (more, more results, anything else, what else)
- next: Moving to the next item in a list (next, next page, show me next)
- previous: Moving to the previous item in a list (back, go back, previous page)
- repeat: Asking to do something again (repeat, come again, do it again)
- select.number: Selecting items from a list (third, I choose number 3, select the first one)

Let's now build a follow-up intent called `Get Feeling`. On the intent list screen, if you hover over the Custom Welcome intent, you will see the Add follow-up intent link.

The following screenshot shows the Add follow-up intent link when hovering over the Custom Welcome intent:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/637eb6c0-2901-4a26-befd-9027322593bd.png)

Add follow-up intent

1. Click Add follow-up intent and select custom intent. Name the follow-up intent `Get Feeling` and, in the User says section, add the following two templates, which utilize the Feeling entity:
    1. I am feeling `@Feeling:Feeling`
    2. I feel `@Feeling:Feeling`
2. In the Action section, enter `input.feeling`, which will be used to identify which intent got triggered in the code in order to respond properly by selecting the `FortuneCookie` based on the user's emotion. Finally, enable the Use webhook in the Fulfillment section.

The following screenshot shows the `Get Feeling` follow-up intent settings:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/a21bb144-776c-4200-8ccf-b2919fbae67b.png)

Get Feeling follow-up intent

#### Writing code for a feeling custom follow-up intent     
1. Let's first add and modify `intentHandlers`. Modify `sendWelcome` so that it does not take any arguments and add the `input.feeling` action in order to handle the `Get Feeling` custom follow-up intent.

The following code shows the modified `sendWelcome` and a new intent handler, called `input.feeling`:

```js
const intentHandlers = {  
    'input.welcome': () => {    
        sendWelcome();   
    },  
    'input.unknown': () => {    
        sendResponse('I\'m having trouble, can you try that again?');   
    },  
    'input.fortune': () => {    
        sendQuote();   
    },  
    'input.feeling': () => {    
        sendQuoteWithFeeling();   
    },  
    'default': () => {    
        sendResponse('This is Henry\'s Fortune Cookie!' );  
    }
};
```

2. Modify the `sendWelcome` intent such that it will randomly redirect the user to `custom_welcome_event`, which is determined by `executeCustomWelcome = Math.random()  > = 0.5`. Otherwise, the user will be greeted normally with _Hello, Welcome to Henry's Fortune Cookie!_. Notice that `followupEventInput` will be populated in the response with the name of the event to be executed.

The following code modifies the previously written `sendWelcome` method, triggering `custom_welcome_event` 50% of the time:

```js
function sendWelcome () {  
    let responseJson;  
    let executeCustomWelcome = Math.random() >= 0.5;  
    if(executeCustomWelcome) {     
        responseJson = {      
            followupEventInput: {        
                name: "custom_welcome_event"      
            }    
        };  
    } else {    
        responseJson = { fulfillmentText: 'Hello, Welcome to Henry\'s Fortune Cookie!' };   
    }  
    console.log('sendWelcome: ' + JSON.stringify(responseJson));  response.json(responseJson);
}
```

3. Now let's write code to handle the `input.feeling` action, where a quote based on the user's feeling will be sent as a response. First, you need to capture parameters from the request, so add it to the global variable.

The following code declares the global variable parameters:

```js
var request, response, parameters;
```

The following code captures the parameters from the request:

```js
parameters = request.body.queryResult.parameters || {};
```

The following code shows the entire modified processV2Request function, which includes capturing the parameters value:

```js
function processV2Request () {  
    let action = (request.body.queryResult.action) ? request.body.queryResult.action : 'default';  parameters = request.body.queryResult.parameters || {};  
    if (intentHandlers[action]) {     
        intentHandlers[action]();  
    } else {    
        intentHandlers['default']();     
    }
}
```

4. Since the parameters value containing the user's feeling is captured, you can go ahead and write the `sendQuoteWithFeeling` function, which will be executed when the request action is `input.feeling`. The `Get Feeling Custom` follow-up intent will contain the parameter called `Feeling`, which will come through the `parameters.Feeling` Dialogflow request object. After comparing `parameters.Feeling` to `happy`, if true, a random number will be selected from 0 to 5, or if not, a random number will be selected from 6 to 9 and then an appropriate quote corresponding to the feeling will be selected using `quotes[randomNumber].quote`.

The following code describes the `sendQuoteWithFeeling` function, which creates a Dialogflow response that sends the quote based on the user's feeling:

```js
function sendQuoteWithFeeling () {  
    let responseJson, randomNumber;  
    if(parameters.Feeling === "happy"){    
        randomNumber = Math.floor(Math.random() * 5)  
    } else {    
        randomNumber = Math.floor(Math.random() * 4) + 6  
    }  
    responseJson = { fulfillmentText: quotes[randomNumber].quote };   
    console.log('sendQuoteWithFeeling: ' + JSON.stringify(responseJson));  
    response.json(responseJson);}
```

## Building a Get Fortune Cookie by an author
### Building an Author entity
Start by building the `Author` entity, which will be used by the Get Author Quote intent that matches the author's name in order to send a quote by that author. The following JSON data shows multiple ways to identify the author:

```json
[    
    { "value": "T. S. Eliot", "synonyms": [ "T. S. Eliot", "Eliot" ] },    
    { "value": "J. B. White", "synonyms": [ "J. B. White", "White" ] },    
    { "value": "Dave Stutman", "synonyms": [ "Dave Stutman", "Dave", "Stutman" ] },    
    { "value": "Winston Churchill", "synonyms": [ "Winston Churchill", "Winston", "Churchill" ] },    
    { "value": "Woody Allen", "synonyms": [ "Woody Allen", "Woody", "Allen" ] },    
    { "value": "Confucius", "synonyms": [ "Confucius" ] },    { "value": "Mark Twain", "synonyms": [ "Mark Twain", "Mark", "Twain" ] },    
    { "value": "Albert Einstein", "synonyms": [ "Albert Einstein", "Albert", "Einstein" ] },    
    { "value": "Steven Wright", "synonyms": [ "Steven Wright", "Steven", "Wright" ] }
]
```

### About rich response                                     
Normally, when you send a response to the user, you create a response object with the `fulfillmentText` property set with what your user will hear. But rich response allows you to send hyperlinks, images, a list of items, and cards, where the user can not only see, but can also interact with the response. In order to send a rich response, create a response object with the `fulfillmentMessages` object that contains the rich message objects.

### Creating a text response
A text message is similar to the response the intent will send to the user.

The following code shows a text message object that displays text to the user:

```json
"text": {
    "text": [ "hi", "hello" ] 
},
```

### Creating an image response
If the user asks what a cat looks like, you can send an image of a cat, which will get displayed on the user's phone.

The following code shows an image message object:

```json
"image": { "imageUri": "http://myweb.com/cat.png" }
```

### Creating quick replies                                  
Quick replies display a list of replies displayed on the screen that the user can click.

The following code shows a quickReplies object:

```json
"quickReplies": { "title": "Select an option", "quickReplies": [ "option1", "option2" ] }
```

### Creating a card response                                
The card contains an image, a title, a subtitle, and a button that the user can click, which will open a web link. Ask Google Assistant on your phone where good Chinese restaurants near you are and it will display cards.

The following image shows card responses:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/81ad5540-cae8-4911-a801-77bfe11f4ff6.png)

The following code shows how to build a card response:

```json
"card": {
    "title": "My Restaurant",
    "subtitle": "Chinese Food",
    "imageUri": "http://myweb.com/image.png",
    "buttons": [
    {
        "text": "my button",
        "postback": "text send to Dialogflow",
    }
    ]
}
```

### Creating a listSelect response                          
A listSelect response allows you to respond to the user by displaying a list of items that the user can click. The clicked item will send to the Dialogflow. In this section, you will use this to list authors so that the user can choose an author, which will trigger an intent.

The following code shows how to build a listSelect  response:

```json
"listSelect": {  
    "title": "Select an Author",  
    "items": [    
        { "info": { "key": "Eliot" }, "title": "T. S. Eliot"},    
        { "info": { "key": "White" }, "title": "J. B. White"},  
    ]
}
```

### Building a Get Authors intent
A `Get Authors` intent will be used to capture the user's request to display a list of authors. You will learn how to build a `listSelect` response, where the user can click the name of the author from the list. First, build a `Get Authors` intent by adding `show me authors` and `list authors` to the User says section. Name the Action `input.authors` so that you can identify the request from server. Finally, enable `Use webhook` in the Fulfillment section.

The following screenshot shows the `Get Authors` settings:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/83c67f65-531c-42e1-8845-0a2e7657a304.png)

Get Authors intent

#### Building a listSelect response in code
1. First, add to the `intentHandler`, which captures the Action named `input.authors`, which executes the `sendAuthors` function. The following code, which captures the `input.authors` action, is added to `intentHandler`:

```js
'input.authors': () => {
    sendAuthors(); 
}
```

2. The next thing do is to create the `sendAuthors` function, where the `listSelect` response will be created. Setting `fulfillmentText` with `defaultText`, asking the user to say the author's name is important because not every device has capability to display response on the screen. For example, on Google Home there is no way to display a list of authors so it will default to simply saying `fulfillmentText`.

The following code shows the completed `sendAuthors` function, which will send the `listSelect` response to the user:

```js
function sendAuthors () {
  let defaultText = "Choose an author. T S Eliot, J B White, Dave Stutman, Winston Churchill, ";
  defaultText = defaultText + "Woody Allen, Confucius, Mark Twain, Albert Einstein, Steven Wright";
  let responseJson = { 
    fulfillmentText: defaultText,
    fulfillmentMessages: [
      {
        platform: "ACTIONS_ON_GOOGLE",
        listSelect: {
          title: "Select an Author",
          items: [
            { info: { key: "Eliot" }, title: "T. S. Eliot"},
            { info: { key: "White" }, title: "J. B. White"},
            { info: { key: "Stutman" }, title: "Dave Stutman"},
            { info: { key: "Churchill" }, title: "Winston  
            Churchill"},
            { info: { key: "Allen" }, title: "Woody Allen"},
            { info: { key: "Confucius" }, title: "Confucius"},
            { info: { key: "Twain" }, title: "Mark Twain"},
            { info: { key: "Einstein" }, title: "Albert Einstein"},
            { info: { key: "Wright" }, title: "Steven Wright"}
          ]
        }
      }
    ] 
  }; 
  console.log('sendAuthors: ' + JSON.stringify(responseJson));
  response.json(responseJson);  
}
```

3. Deploy the code and test the `list authors` command in the simulator and you will see that the list of authors will be displayed.

The following screenshot shows the displayed `listSelect` response, containing the author names:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/59abc0ad-de9f-4f90-a7bb-383b75437072.png)

### Building a Get Author Quote intent
When the user selects the author from the list, the author's name will be sent back to Dialogflow and you will want to build an intent that captures the authors and then selects a quote by that selected author. Using the `Author` entity, build an intent that gets triggered when the user says the author's name or the author's name is selected from the list. Create `Get Author Quote` and add `@Author:Author` to User says and enable Use webhook.

The following screenshot shows the `Get Author Quote` intent settings:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/d37a4e3b-82a5-4d86-8a51-f3527fa8ef63.png)

Get Author Quote intent

#### Building a Get Author Quote intent's webhook
1. When the `Get Author Quote` intent is triggered, the request will come into the webhook with the Action name `input.author.quote`, and `input.author.quote` needs to be added to `intentHandler`, which will execute the `sendAuthorQuote` function.

The following code handles the request with the Action name input.author.quote triggered by the Get Author Quote intent and will execute the sendAuthorQuote function:

```js
'input.author.quote': () => {
    sendAuthorQuote(); 
},
```

2. Now create a `sendAuthorQuote` function, which will build a response with the request author. When `Get Author Quote` is triggered, either by the user saying the author's name or by selecting from the list of the authors, the request will be sent with `parameters.Author`.

The following line of code uses `parameters.Author` to search the quotes array and extract the author's quote:

```js
quotes.find(x => x.author.toLowerCase().indexOf(parameters.Author.toLowerCase())>=0).quote
```

3. Finally, the author's quote is set to `fulfillmentText` and sent as a response and the user will hear the author's quote.

The following code shows the completed version of the `sendAuthorQuote` function:

```js
function sendAuthorQuote () {  
    let authorQuote = quotes.find(x => x.author.toLowerCase().indexOf(parameters.Author.toLowerCase())>=0).quote;  
    let responseJson = { fulfillmentText: authorQuote };   
    console.log('sendAuthorQuote: ' + JSON.stringify(responseJson));  
    response.json(responseJson);  
}
```

### Integrating SSML and audio to Default Welcome intent
Previously, Default Welcome intent simply greeted the user with _Hello, Welcome to Henry's Fortune Cookie!_ by setting `fulfillmentText` in the response object. Let's enhance this by using the `simpleResponses` object in the `fulfillmentMessages` property of the response object. The `simpleResponses` object contains properties called `ssml` and `displayText`. The `ssml` property contains SSML speech and also part of SSML speech the audio sound can be incorporated. `displayText` is displayed if the device does not have the audio capability.

In `ssml`, the speech will start with the thunder sound `<audio src="https://actions.google.com/sounds/v1/weather/thunder_crack.ogg" />` and then there will be a pause of 200 ms, `<break time="200ms"/>`. Finally, _Hello Welcome to Henry's Fortune Cookie!_ will be inside `<prosody rate="medium" pitch="+2st">`, where the speech rate is set to medium with a slightly higher pitch, set at `+2st`.

>Setting a high pitch with a medium speech rate will give the effect of being excited and happy.

The following code shows the `simpleResponse` object set with the SSML speech, which contains the audio in the `sendWelcome` function:

```js
responseJson = {       
    fulfillmentText: 'Hello, Welcome to Henry\'s Fortune Cookie!',      
    fulfillmentMessages: [        
        {          
            platform: "ACTIONS_ON_GOOGLE",          simpleResponses: {            
                simpleResponses: [              
                    {                
                        ssml: `<speak><audio src="https://actions.google.com/sounds/v1/weather/thunder_crack.ogg" />                        
                        <break time="200ms"/>               
                        <prosody rate="medium" pitch="+2st">                          
                            Hello Welcome to Henry's Fortune Cookie!          
                        </prosody>
                        </speak>`,                
                        displayText: "Hello, Welcome to Henry\'s Fortune Cookie!"         
                    } 
                ] 
            } 
        } 
    ] 
 };
```

### Using Analytics
In Dialogflow, there is an Analytics section, where you can see the performance of the agent. The following data metrics are collected:

- The number of queries per user session
- The number of times the intent was called
- The percentage of where user exited
- The average response time to user requests

One of the important metrics is the number of times the intent was called, because it gives us an insight into the most popular intent in your VUIs. Once you know which intent is popular, you can continue to improve it. Also, knowing the average response time to user requests provides important information, as you would not want your user to wait a long time for a response.

The following image shows you the all the metrics collected by Dialogflow Analytics:

![](https://www.safaribooksonline.com/library/view/voice-user-interface/9781788473354/assets/6f3185cc-97d6-43c4-b279-9e842e060faf.png)

Dialogflow Analytics