![cover](https://img1.doubanio.com/view/subject/l/public/s29230098.jpg)

    作者: Kirupa Chinnathambi
    出版社: Addison-Wesley Professional
    出版年: 2016-11-25
    页数: 240
    定价: USD 39.99
    装帧: Paperback
    ISBN: 9780134546315

[豆瓣链接](https://book.douban.com/subject/26938529/)

- [Introducing React](#introducing-react)
  - [NEW SCHOOL SINGLE-PAGE APPS](#new-school-single-page-apps)
  - [AUTOMATIC UI STATE MANAGEMENT](#automatic-ui-state-management)
    - [Lightning-fast DOM Manipulation](#lightning-fast-dom-manipulation)
    - [APIs to Create Truly Composable UIs](#apis-to-create-truly-composable-uis)
    - [Visuals Defined Entirely in JavaScript](#visuals-defined-entirely-in-javascript)
    - [Just the V in an MVC Architecture](#just-the-v-in-an-mvc-architecture)
- [Components in React](#components-in-react)
  - [MEET THE REACT COMPONENT](#meet-the-react-component)
    - [Creating a Hello, World! Component](#creating-a-hello-world-component)
    - [Specifying Properties](#specifying-properties)
    - [Dealing with Children](#dealing-with-children)
- [Styling in React](#styling-in-react)
  - [DISPLAYING SOME VOWELS](#displaying-some-vowels)
  - [STYLING CONTENT THE REACT WAY](#styling-content-the-react-way)
    - [Creating a Style Object](#creating-a-style-object)
    - [Actually Styling Our Content](#actually-styling-our-content)
    - [Making the Background Color Customizable](#making-the-background-color-customizable)
- [Creating Complex Components](#creating-complex-components)
  - [FROM VISUALS TO COMPONENTS](#from-visuals-to-components)
    - [Identifying the Major Visual Elements](#identifying-the-major-visual-elements)
    - [Identifying the Components](#identifying-the-components)
    - [The Card Component](#the-card-component)
    - [The Square Component](#the-square-component)
    - [The Label Component](#the-label-component)
    - [Passing Properties, Again!](#passing-properties-again)
- [Transferring Properties (Props)](#transferring-properties-props)
  - [PROBLEM OVERVIEW](#problem-overview)
  - [DETAILED LOOK AT THE PROBLEM](#detailed-look-at-the-problem)
  - [PROPERLY TRANSFERRING PROPERTIES](#properly-transferring-properties)
- [Meet JSX—Again!](#meet-jsxagain)
  - [WHAT HAPPENS WITH JSX?](#what-happens-with-jsx)
  - [JSX QUIRKS TO REMEMBER](#jsx-quirks-to-remember)
    - [You Can Only Return A Single Root Node](#you-can-only-return-a-single-root-node)
    - [You Can’t Specify CSS Inline](#you-cant-specify-css-inline)
    - [Reserved Keywords and className](#reserved-keywords-and-classname)
- [Dealing with State](#dealing-with-state)
  - [USING STATE](#using-state)
  - [GETTING OUR COUNTER ON](#getting-our-counter-on)
  - [OPTIONAL: THE FULL CODE](#optional-the-full-code)
- [Going from Data to UI](#going-from-data-to-ui)
  - [THE EXAMPLE](#the-example)
  - [YOUR JSX CAN BE ANYWHERE—PART II](#your-jsx-can-be-anywherepart-ii)
  - [DEALING WITH ARRAYS IN THE CONTEXT OF JSX](#dealing-with-arrays-in-the-context-of-jsx)
- [Working with Events](#working-with-events)
  - [LISTENING AND REACTING TO EVENTS](#listening-and-reacting-to-events)
    - [Starting Point](#starting-point)
    - [Making the Button Click Do Something](#making-the-button-click-do-something)
    - [Meet Synthetic Events](#meet-synthetic-events)
    - [You Can’t Directly Listen to Events on Components](#you-cant-directly-listen-to-events-on-components)
    - [Listening to Regular DOM Events](#listening-to-regular-dom-events)
    - [The Meaning of this Inside the Event Handler](#the-meaning-of-this-inside-the-event-handler)
- [The Component Lifecycle](#the-component-lifecycle)
  - [MEET THE LIFECYCLE METHODS](#meet-the-lifecycle-methods)
    - [See the Lifecycle Methods in Action](#see-the-lifecycle-methods-in-action)
    - [The Initial Rendering Phase](#the-initial-rendering-phase)
    - [The Updating Phase](#the-updating-phase)
      - [Dealing with State Changes](#dealing-with-state-changes)
      - [Dealing with Prop Changes](#dealing-with-prop-changes)
      - [The Unmounting Phase](#the-unmounting-phase)
- [Accessing DOM Elements](#accessing-dom-elements)
    - [Simplifying Further with ES6 Arrow Functions](#simplifying-further-with-es6-arrow-functions)

# Introducing React
## NEW SCHOOL SINGLE-PAGE APPS
When building single-page apps, there are three major issues that you’ll encounter:
- In a single-page application, the bulk of your time will be spent keeping your data in sync with your UI.
  - For example, if a user loads new content, do we explicitly clear out the search field? Do we keep the active tab on a navigation element still visible? Which elements do we keep on the page, and which do we destroy?
  - These are all problems unique to single-page apps. When navigating between pages in the old model, we just assumed everything in our UI would be destroyed and just built back up again. This was never a problem.
- Manipulating the DOM is really REALLY slow.
  - Manually querying elements, adding children (see Figure 1-5 below), removing subtrees, and performing other DOM operations are some of the slowest things you can do in your browser.
  - ![1](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/01fig05.jpg)
- Working with HTML templates can be a pain.
  - Navigation in a single-page app is nothing more than you dealing with fragments of HTML to represent whatever it is you wish to display. These fragments of HTML are often known as `templates`, and using JavaScript to manipulate them and fill them out with data gets really complicated really quickly.

For example, this is what using a template in Mustache looks like:
```js
var view = {
  title: "Joe",
  calc: function () {
    return 2 + 4;
  }
};

var output = Mustache.render("{{title}} spends {{calc}}", view);
```

## AUTOMATIC UI STATE MANAGEMENT
### Lightning-fast DOM Manipulation
Because DOM modifications are really slow, you never modify the DOM directly using React. Instead, you modify an in-memory `virtual DOM` instead.

Manipulating this virtual DOM is extremely fast, and React takes care of updating the real DOM when the time is right. It does so by comparing the changes between your virtual DOM and the real DOM, figuring out which changes actually matter, and making the least amount of DOM changes needed to keep everything up-to-date in a process called `reconciliation`.

### APIs to Create Truly Composable UIs
Instead of treating the visual elements in your app as one monolithic chunk, React encourages you to break your visual elements into smaller and smaller components.

Just like everything else in programming, it is a good idea to have things be modular, compact, and self-contained.

### Visuals Defined Entirely in JavaScript
React gives you the option to specify your visuals using an HTML-like syntax known as `JSX` that lives fully alongside your JavaScript.

```js
ReactDOM.render(
  <div>
    <h1>Batman</h1>
    <h1>Iron Man</h1>
    <h1>Nicolas Cage</h1>
    <h1>Mega Man</h1>
  </div>,
  destination
);
```

This same code defined in JavaScript would look like this:

```js
ReactDOM.render(React.createElement(
  "div",
  null,

  React.createElement(
    "h1",
    null,
    "Batman"
  ),

  React.createElement(
    "h1",
    null,
    "Iron Man"
  ),

  React.createElement(
    "h1",
    null,
    "Nicolas Cage"
  ),

  React.createElement(
    "h1",
    null,
    "Mega Man"
  )
), destination);
```

By using JSX, you are able to define your visuals very easily using a syntax that is very familiar, while still getting all the power and flexibility that JavaScript provides.

### Just the V in an MVC Architecture
React works primarily in the View layer where all of its worries and concerns revolve around your visual elements and keeping them up to date.

# Components in React
![3-1](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/03fig01.jpg)

Figure 3-1 Your hypothetical finished app.

Almost every part of this app’s visuals would be wrapped inside a self-contained module known as a `component`. To highlight what “almost every” means here, take a look at the diagram in Figure 3-2.

![3-2](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/03fig02.jpg)

Figure 3-2 Diagrammatic representation of the app components.

## MEET THE REACT COMPONENT
React components are reusable chunks of JavaScript that output (via JSX) HTML elements.

Start with a blank React document:

```html
<!DOCTYPE html>
<html>
<head>
  <title>React Components</title>
  <script src="https://unpkg.com/react@15.3.2/dist/react.js"></script>
  <script src="https://unpkg.com/react-dom@15.3.2/dist/react-dom.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.
js"></script>
</head>

<body>
  <div id="container"></div>
  <script type="text/babel">
  </script>
</body>
</html>
```

### Creating a Hello, World! Component
What we want to do is use a component to help us print the famous “Hello, world!” text to the screen. As we already know, by using just the render method of ReactDOM, the code would look as follows:

```js
ReactDOM.render(
  <div>
    <p>Hello, world!</p>
  </div>,
  document.querySelector("#container")
);
```

Just like the render method of we saw a few moments earlier as part of ReactDOM.render, the render method inside a component is also responsible for dealing with JSX. Let’s modify our render method to return Hello, componentized world!, so go ahead and add the following highlighted lines:

```js
var HelloWorld = React.createClass({
  render: function() {
    return (
      <p>Hello, componentized world!</p>
    );
  }
});
```

All that remains is to actually use this component. The way you use a component once you’ve defined it is by `calling` it, and we are going to call it from our old friend, the ReactDOM.render method:

```js
ReactDOM.render(
  <HelloWorld/>,
  document.querySelector("#container")
);
```

Go ahead and modify our ReactDOM.render method to look as follows:

```js
ReactDOM.render(
  <div>
    <HelloWorld/>
  </div>,
  document.querySelector("#container")
);
```

Modify our ReactDOM.render method to now look as follows:

```js
ReactDOM.render(
  <div>
    <HelloWorld/>
    <HelloWorld/>
    <HelloWorld/>
    <HelloWorld/>
    <HelloWorld/>
    <HelloWorld/>
  </div>,
  document.querySelector("#container")
);
```

### Specifying Properties
What we call `arguments` in the function world are going to be known as `properties` in the component world.

```js
var HelloWorld = React.createClass({
  render: function() {
    return (
      <p>Hello, {this.props.greetTarget}!</p>
    );
  }
});
```

Go ahead and modify our HelloWorld calls as follows:

```js
ReactDOM.render(
  <div>
    <HelloWorld greetTarget="Batman"/>
    <HelloWorld greetTarget="Iron Man"/>
    <HelloWorld greetTarget="Nicolas Cage"/>
    <HelloWorld greetTarget="Mega Man"/>
    <HelloWorld greetTarget="Bono"/>
    <HelloWorld greetTarget="Catwoman"/>
  </div>,
  document.querySelector("#container")
);
```

### Dealing with Children
Your components can have children.What this means is that you can do something like this:

```js
<CleverComponent foo="bar">
  <p>Something!</p>
</CleverComponent>
```

You have a component very cleverly called CleverComponent, and it has a p element as a child. From within CleverComponent, you have the capability to access the p child element (and any children it may have) via the children property accessed by `this.props.children`.

This time around, we have a component called Buttonify that wraps its children inside a button. The component looks like this:

```js
var Buttonify = React.createClass({
  render: function() {
    return (
      <div>
        <button type={this.props.behavior}>{this.props.children}</button>
      </div>
    );
  }
});
```

The way you can use this component is by just calling it via the ReactDOM.render method as shown here:

```js
ReactDOM.render(
  <div>
    <Buttonify behavior="Submit">SEND DATA</Buttonify>
  </div>,
  document.querySelector("#container")
);
```

![3-4](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/03fig04.jpg)

Figure 3-4 A large send data button.

# Styling in React
## DISPLAYING SOME VOWELS
First, you’ll need a blank HTML page that will host our React content. If you don’t have one, feel free to use the following markup:

```js
<!DOCTYPE html>
<html>
<head>
  <title>Styling in React</title>
  <script src="https://unpkg.com/react@15.3.2/dist/react.js"></script>
  <script src="https://unpkg.com/react-dom@15.3.2/dist/react-dom.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>

  <style>
    #container {
      padding: 50px;
      background-color: #FFF;
    }
  </style>
</head>

<body>
  <div id="container"></div>
</body>
</html>
```

Just below the container div element, add the following:

```js
<script type="text/babel">
  var Letter = React.createClass({
    render: function() {
        return (
          <div>
            {this.props.children}
          </div>
        );
      }
  });

  var destination = document.querySelector("#container");
  ReactDOM.render(
    <div>
      <Letter>A</Letter>
      <Letter>E</Letter>
      <Letter>I</Letter>
      <Letter>O</Letter>
      <Letter>U</Letter>
    </div>,
    destination
  );
</script>
```

![4-2](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/04fig02.jpg)

Figure 4-2 The letters arranged horizontally and with a yellow background.

## STYLING CONTENT THE REACT WAY
Right now, our Letter component is back to its original state:

```js
var Letter = React.createClass({
  render: function() {
      return (
        <div>
          {this.props.children}
        </div>
      );
    }
});
```

### Creating a Style Object
Let’s get right to it by defining our object that contains the styles we wish to apply:

```js
var Letter = React.createClass({
  render: function() {
      var letterStyle = {
        padding: 10,
        margin: 10,
        backgroundColor: "#ffde00",
        color: "#333",
        display: "inline-block",
        fontFamily: "monospace",
        fontSize: 32,
        textAlign: "center"
      };

      return (
        <div>
          {this.props.children}
        </div>
      );
    }
});
```

We have an object called `letterStyle`, and the properties inside it are just CSS property names and their value.

### Actually Styling Our Content
```js
var Letter = React.createClass({
  render: function() {
      var letterStyle = {
        padding: 10,
        margin: 10,
        backgroundColor: "#ffde00",
        color: "#333",
        display: "inline-block",
        fontFamily: "monospace",
        fontSize: "32",
        textAlign: "center"
      };

      return (
        <div style={letterStyle}>
          {this.props.children}
        </div>
      );
    }
});
```

Our object is called letterStyle, so that is what we specify inside the curly brackets to let React know to evaluate the expression.

![4-4](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/04fig04.jpg)

Figure 4-4 The styles are applied inline.

### Making the Background Color Customizable
```js
ReactDOM.render(
  <div>
    <Letter bgcolor="#58B3FF">A</Letter>
    <Letter bgcolor="#FF605F">E</Letter>
    <Letter bgcolor="#FFD52E">I</Letter>
    <Letter bgcolor="#49DD8E">O</Letter>
    <Letter bgcolor="#AE99FF">U</Letter>
  </div>,
  destination
);
```

Next, we need to use this property. In our letterStyle object, set the value of backgroundColor to this.props.bgColor:

```js
var letterStyle = {
  padding: 10,
  margin: 10,
  backgroundColor: this.props.bgcolor,
  color: "#333",
  display: "inline-block",
  fontFamily: "monospace",
  fontSize: "32",
  textAlign: "center"
};
```

![4-5](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/04fig05.jpg)

Figure 4-5 Our vowels with background colors!

# Creating Complex Components
## FROM VISUALS TO COMPONENTS
What we are going to do is build a simple color palette card (see Figure 5-2).

![5-2](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig02.jpg)

Figure 5-2 A simple color palette card.

 I am going to show you a very systematic approach that will help you simplify and make sense of even the most complex user interfaces. This approach involves two steps:

1. Identify the major visual elements
2. Figure out what the components will be

### Identifying the Major Visual Elements
The first thing you will see in our example is the card itself (see Figure 5.3).

![5-3](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig03.jpg)

Figure 5-3 The card.

Let’s call out these two visual elements and arrange them into a tree-like structure as shown in Figure 5-4.

![5-4](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig04.jpg)

Figure 5-4 Tree-like structure.

Arranging your visuals into this tree-like structure (aka a `visual hierarchy`) is a good way to get a better feel for how your visual elements are grouped. The goal of this exercise is to identify the important visual elements and break them into a parent/child arrangement until you can divide them no further.

We can further divide the label from the white region that surrounds it. Right now, our visual hierarchy looks as shown in Figure 5-5 with our label and white region occupying a separate spot in our tree.

![5-5](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig05.jpg)

Figure 5-5 Dividing things further into the label and the white region that surrounds it.

### Identifying the Components
Not every visual element will need to be turned into a component, and we certainly don’t want to create only a few extremely complex components either. There needs to be a balance (see Figure 5-6).

![5-6](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig06.jpg)

Figure 5-6 Not too few and not too many components.

**The general rule is that our components should do just one thing.** If you find that your potential component will end up doing too many things, you probably want to break your component into multiple components. On the flip side, if your potential component does too little, you probably want to skip making that visual element a component altogether.

That just puts a question mark around our label and the white region it is surrounded by though (see Figure 5-7).

![5-7](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig07.jpg)

Figure 5-7 Question mark around the label and the white space around it.

The important part here is the label itself. Without it, we can’t see the hex value. That leaves just the white region. The purpose it serves is negligible. It is simply empty space, and the responsibility for that can easily be handed off to our label itself. Brace yourself for what I am about to say next. Sadly, our white rectangular region will not be turned into a component.

At this point, we have identified our three components, and the `component hierarchy` looks as in Figure 5-8.

![5-8](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig08.jpg)

Figure 5-8 The three components.

CREATING THE COMPONENTS
```js
<!DOCTYPE html>
<html>
<head>
  <title>More Components!</title>
  <script src="https://unpkg.com/react@15.3.2/dist/react.js"></script>
  <script src="https://unpkg.com/react-dom@15.3.2/dist/react-dom.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>
  <style>
    #container {
      padding: 50px;
      background-color: #FFF;
    }
  </style>
</head>
<body>
  <div id="container"></div>
  <script type="text/babel">

    ReactDOM.render(
      <div>
      </div>,
      document.querySelector("#container")
    );
  </script>
</body>
</html>
```

The names we will go with for our components will be `Card`, `Label`, and `Square`.

```js
var Square = React.createClass({
  render: function() {
    return(
      <p>Nothing</p>
    );
  }
});

var Label = React.createClass({
  render: function() {
    return (
      <p>Nothing</p>
    );
  }
});

var Card = React.createClass({
  render: function() {
      return (
      );
    }
});
ReactDOM.render(
  <div>
  </div>,
  document.querySelector("#container")
);
```

### The Card Component
```js
var Card = React.createClass({
    render: function() {
        var cardStyle = {
            height: 200,
            width: 150,
            padding: 0,
            backgroundColor: "#FFF",
            WebkitFilter: "drop-shadow(0px 0px 5px #666)",
            filter: "drop-shadow(0px 0px 5px #666)"
        };

        return (
            <div style={cardStyle}>
            </div>
     );
  }
});
```

Now, to see our Card component in action, we need to display it in our DOM as part of the ReactDOM.render function.

```js
ReactDOM.render(
  <div>
    <Card/>
  </div>,
  document.querySelector("#container")
 );
```

![5-9](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig09.jpg)

Figure 5-9 The result of your test—the outline of the color palette card.

### The Square Component
```js
var Square = React.createClass({
      render: function() {
        var squareStyle = {
          height: 150,
          backgroundColor: "#FF6663"
        };
        return(
          <div style={squareStyle}>
          </div>
      );
    }
});
```

Go back to our Card component’s render function, and make the following change:

```js
var Card = React.createClass({
  render: function() {
      var cardStyle = {
        height: 200,
        width: 150,
        padding: 0,
        backgroundColor: "#FFF",
        WebkitFilter: "drop-shadow(0px 0px 5px #666)",
        filter: "drop-shadow(0px 0px 5px #666)"
      };

      return (
        <div style={cardStyle}>
          <Square/>
        </div>
      );
    }
});
```

![5-10](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig10.jpg)

Figure 5-10 The red portion appears.

This is an example of `component composability` where one component relies on the output of another component.

### The Label Component
```js
var Label = React.createClass({
      render: function() {
        var labelStyle = {
          fontFamily: "sans-serif",
          fontWeight: "bold",
          padding: 13,
          margin: 0
       };

      return (
        <p style={labelStyle}>#FF6663</p>
    );
  }
});
```

Go ahead and make the following highlighted change:

```js
var Card = React.createClass({
    render: function() {
      var cardStyle = {
        height: 200,
        width: 150,
        padding: 0,
        backgroundColor: "#FFF",
        WebkitFilter: "drop-shadow(0px 0px 5px #666)",
        filter: "drop-shadow(0px 0px 5px #666)"
      };

      return (
        <div style={cardStyle}>
          <Square/>
          <Label/>
        </div>
      );
    }
});
```

![5-11](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig11.jpg)

Figure 5-11 The label appears.

### Passing Properties, Again!
```js
var Square = React.createClass({
    render: function() {
        var squareStyle = {
          height: 150,
          backgroundColor: this.props.color
        };

        return(
          <div style={squareStyle}>
          </div>
        );
      }
    });

var Label = React.createClass({
    render: function() {
      var labelStyle = {
        fontFamily: "sans-serif",
        fontWeight: "bold",
        padding: 13,
        margin: 0
      };

      return (
        <p style={labelStyle}>{this.props.color}</p>
      );
    }
});

  var Card = React.createClass({
    render: function() {
      var cardStyle = {
          height: 200,
          width: 150,
          padding: 0,
          backgroundColor: "#FFF",
          WebkitFilter: "drop-shadow(0px 0px 5px #666)",
          filter: "drop-shadow(0px 0px 5px #666)"
        };

      return (
        <div style={cardStyle}>
          <Square color={this.props.color}/>
          <Label color={this.props.color}/>
        </div>
      );
    }
  });

ReactDOM.render(
  <div>
    <Card color="#FF6663"/>
  </div>,
  document.querySelector("#container")
);
```

Once you have made this change, you can specify any hex color you want as part of calling the Card component:

```js
ReactDOM.render(
  <div>
    <Card color="#FFA737"/>
  </div>,
  document.querySelector("#container")
);
```

![5-12](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/05fig12.jpg)

Figure 5-12 The color for hex value #FFA737.

# Transferring Properties (Props)
## PROBLEM OVERVIEW
Let’s say that you have a deeply nested component, and its hierarchy (modeled as awesomely colored circles) looks like Figure 6-1.

![6-1](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/06fig01.jpg)

Figure 6-1 The component hierarchy.

What you want to do is pass a property from your red circle all the way down to our purple circles where it will be used. What we can’t do is the very obvious and straightforward thing shown in Figure 6-2.

![6-2](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/06fig02.jpg)

Figure 6-2 Can’t do this.

You can’t pass a property directly to the component or components that you wish to target. The reason has to do with how React works. **React enforces a chain of command where properties have to flow down from a parent component to an immediate child component.**

Under these guidelines, passing a property from our red circle to our purple circle looks a little bit like Figure 6-3.

![6-3](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/06fig03.jpg)

Figure 6-3 The property is passed from parent to child.

If we had to send a property called color from the component representing our red circle to the component representing our purple circle, its path to the destination would look something like Figure 6-4.

![6-4](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/06fig04.jpg)

Figure 6-4 Sending the color property.

Now, imagine we have two properties that we need to send, as in Figure 6-5.

![6-5](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/06fig05.jpg)

Figure 6-5 Sending two properties.

What if we wanted to send three properties? Or four?

## DETAILED LOOK AT THE PROBLEM
```js
var Display = React.createClass({
  render: function() {
    return(
      <div>
        <p>{this.props.color}</p>
        <p>{this.props.num}</p>
        <p>{this.props.size}</p>
      </div>
    );
  }
});

var Label = React.createClass({
  render: function() {
    return (
      <Display color={this.props.color}
              num={this.props.num}
              size={this.props.size}/>
    );
  }
});

var Shirt = React.createClass({
  render: function() {
      return (
        <div>
          <Label color={this.props.color}
                 num={this.props.num}
                 size={this.props.size}/>
        </div>
      );
    }
});

ReactDOM.render(
  <div>
    <Shirt color="steelblue" num="3.14" size="medium"/>
  </div>,
  document.querySelector("#container")
);
```

The component hierarchy can be seen in Figure 6-6.

![6-6](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/06fig06.jpg)

Figure 6-6 The component hierarchy.

When you run this code, what gets output is nothing special. It is just three lines of text (see Figure 6-7).

![6-7](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/06fig07.jpg)

Figure 6-7 The three lines of text.

## PROPERLY TRANSFERRING PROPERTIES
The solution to all of our problems lies in something new to JavaScript known as the `spread operator`.

```js
var items = ["1", "2", "3"];
function printStuff(a, b, c) {
  console.log("Printing: " + a + " " + b + " " + c);
}

// using the spread operator
printStuff(...items);

// without using the spread operator
printStuff(items[0], items[1], items[2]);
```

Inside a component, our props object looks as follows:
```js
var props = {
  color: "steelblue",
  num: "3.14",
  size: "medium"
}
```

As part of passing these property values to a child component, we manually access each item from our props object:
```js
<Display color={this.props.color}
        num={this.props.num}
        size={this.props.size}/>
```

We can call our Display component by using ...props:
```js
<Display {...props}/>
```

This means our earlier example can be simplified as follows:
```js
var Display = React.createClass({
  render: function() {
    return(
      <div>
        <p>{this.props.color}</p>
        <p>{this.props.num}</p>
        <p>{this.props.size}</p>
      </div>
    );
  }
});

var Label = React.createClass({
  render: function() {
    return (
      <Display {...this.props}/>
    );
  }
});

var Shirt = React.createClass({
  render: function() {
      return (
        <div>
          <Label {...this.props}/>
        </div>
      );
    }
});

ReactDOM.render(
  <div>
    <Shirt color="steelblue" num="3.14" size="medium"/>
  </div>,
  document.querySelector("#container")
);
```

# Meet JSX—Again!
## WHAT HAPPENS WITH JSX?
Take a look at the following example where we define a component called Card:

```js
var Card = React.createClass({
  render: function() {
      var cardStyle = {
        height: 200,
        width: 150,
        padding: 0,
        backgroundColor: "#FFF",
        WebkitFilter: "drop-shadow(0px 0px 5px #666)",
        filter: "drop-shadow(0px 0px 5px #666)"
      };

      return (
        <div style={cardStyle}>
          <Square color={this.props.color}/>
          <Label color={this.props.color}/>
        </div>
      );
    }
});
```

We can quickly spot the JSX here. It is the following four lines:

```js
<div style={cardStyle}>
  <Square color={this.props.color}/>
  <Label color={this.props.color}/>
</div>
```

When this JSX reaches our browser, it ends up getting turned into pure JavaScript:

```js
return React.createElement(
  "div",
  { style: cardStyle },
  React.createElement(Square, { color: this.props.color }),
  React.createElement(Label, { color: this.props.color })
);
```

All of those neatly nested HTML-like elements, their attributes, and their children all get turned into a series of `createElement` calls with default initialization values. Here is what our entire Card component looks like when it gets turned into JavaScript:

```js
var Card = React.createClass({
  displayName: "Card",

  render: function render() {
    var cardStyle = {
      height: 200,
      width: 150,
      padding: 0,
      backgroundColor: "#FFF",
      WebkitFilter: "drop-shadow(0px 0px 5px #666)",
      filter: "drop-shadow(0px 0px 5px #666)"
    };

    return React.createElement(
      "div",
      { style: cardStyle },
      React.createElement(Square, { color: this.props.color }),
      React.createElement(Label, { color: this.props.color })
    );
  }
});
```

## JSX QUIRKS TO REMEMBER
### You Can Only Return A Single Root Node
This is probably the first quirk we ran into. In JSX, what you return or render can’t be made up of multiple root elements:
```js
ReactDOM.render(
  <Letter>B</Letter>
  <Letter>E</Letter>
  <Letter>I</Letter>
  <Letter>O</Letter>
  <Letter>U</Letter>,
  document.querySelector("#container")
);
```

If you want to do something like this, you need to wrap all of your elements into a single parent element first:
```js
ReactDOM.render(
  <div>
    <Letter>A</Letter>
    <Letter>E</Letter>
    <Letter>I</Letter>
    <Letter>O</Letter>
    <Letter>U</Letter>
  </div>,
  document.querySelector("#container")
);
```

### You Can’t Specify CSS Inline
In HTML, you can specify CSS properties directly as values on your style attribute:
```html
<div style="font-family:Arial;font-size:24px">
    <p>Blah!</p>
</div>
```

In JSX, the style attribute can’t contain CSS inside it. Instead, it needs to refer to an object that contains styling information instead:
```js
var Letter = React.createClass({
  render: function() {
      var letterStyle = {
        padding: 10,
        margin: 10,
        backgroundColor: this.props.bgcolor,
        color: "#333",
        display: "inline-block",
        fontFamily: "monospace",
        fontSize: "32",
        textAlign: "center"
      };

      return (
        <div style={letterStyle}>
          {this.props.children}
        </div>
      );
    }
});
```

### Reserved Keywords and className
JavaScript has a bunch of keywords and values that you can’t use as identifiers. Those keywords currently (as of ES2016) are:

![es2016](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/085pro02.jpg)

# Dealing with State
## USING STATE
What we are going to is create a simple lightning counter example as shown in Figure 8-1.

![8-1](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/08fig01.jpg)

## GETTING OUR COUNTER ON
To make this all work, we are going to be relying on three APIs that our React Component exposes:

- getInitialState—This method runs just before your component gets mounted, and it allows you to modify a component’s state object.
- componentDidMount—This method gets called just after our component gets rendered (or mounted as React calls it).
- setState—This method allows you to update the value of the state object.

## OPTIONAL: THE FULL CODE
```js
var LightningCounter = React.createClass({
  getInitialState: function() {
    return {
      strikes: 0
    };
  },

  timerTick: function() {
    this.setState({
      strikes: this.state.strikes + 100
    });
  },

  componentDidMount: function() {
    setInterval(this.timerTick, 1000);
  },

  render: function() {
    var counterStyle = {
      color: "#66FFFF",
      fontSize: 50
    };

    var count = this.state.strikes.toLocaleString();
    return (
      <h1 style={counterStyle}>{count}</h1>
    );
  }
});

var LightningCounterDisplay = React.createClass({
    render: function() {
      var commonStyle = {
        margin: 0,
        padding: 0
      }

      var divStyle = {
        width: 250,
        textAlign: "center",
        backgroundColor: "#020202",
        padding: 40,
        fontFamily: "sans-serif",
        color: "#999999",
        borderRadius: 10
      };

      var textStyles = {
        emphasis: {
          fontSize: 38,
          ...commonStyle
        },
        smallEmphasis: {
          ...commonStyle
        },
        small: {
          fontSize: 17,
          opacity: 0.5,
          ...commonStyle
        }
      }

      return(
        <div style={divStyle}>
          <LightningCounter/>
          <h2 style={textStyles.smallEmphasis}>LIGHTNING STRIKES</h2>
          <h2 style={textStyles.emphasis}>WORLDWIDE</h2>
          <p style={textStyles.small}>(since you loaded this example)</p>
        </div>
      );
    }
});

ReactDOM.render(
  <LightningCounterDisplay/>,
  document.querySelector("#container")
);
```

# Going from Data to UI
## THE EXAMPLE
```js
<!DOCTYPE html>
<html>
<head>
  <title>React! React! React!</title>
  <script src="https://unpkg.com/react@15.3.2/dist/react.js"></script>
  <script src="https://unpkg.com/react-dom@15.3.2/dist/react-dom.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>

  <style>
    #container {
      padding: 50px;
      background-color: #FFF;
    }
  </style>
</head>
<body>
  <div id="container"></div>
  <script type="text/babel">

    var Circle = React.createClass({
      render: function() {
          var circleStyle = {
            padding: 10,
            margin: 20,
            display: "inline-block",
            backgroundColor: this.props.bgColor,
            borderRadius: "50%",
            width: 100,
            height: 100,
          };

          return (
            <div style={circleStyle}>
            </div>
          );
        }
    });
    var destination = document.querySelector("#container");

    ReactDOM.render(
      <div>
        <Circle bgColor="#F9C240"/>
      </div>,
      destination
    );
  </script>
</body>
</html>
```

![9-1](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/09fig01.jpg)

Figure 9-1 If everything went well, you will get this yellow circle.

The bulk of what you see comes from the Circle component:

```js
var Circle = React.createClass({
  render: function() {
      var circleStyle = {
        padding: 10,
        margin: 20,
        display: "inline-block",
        backgroundColor: this.props.bgColor,
        borderRadius: "50%",
        width: 100,
        height: 100,
      };

      return (
        <div style={circleStyle}>
        </div>
      );
    }
});
```

Going beyond our component, the way we ultimately display our circle is via our usual ReactDOM.render method:

```js
ReactDOM.render(
  <div>
    <Circle bgColor="#F9C240"/>
  </div>,
  destination
);
```

## YOUR JSX CAN BE ANYWHERE—PART II
For example, we can fearlessly do something like this:

```js
var theCircle = <Circle bgColor="#F9C240"/>;

ReactDOM.render(
  <div>
    {theCircle}
  </div>,
  destination
);
```

For example, you can go further and create a function that returns a Circle component:

```js
function showCircle() {
  var colors = ["#393E41", "#E94F37", "#1C89BF", "#A1D363"];
  var ran = Math.floor(Math.random() * colors.length);

  // return a Circle with a randomly chosen color
  return <Circle bgColor={colors[ran]}/>;
};
```

To have our example use the showCircle function, all you have to do is evaluate it inside ReactDOM.render:

```js
ReactDOM.render(
    <div>
      {showCircle()}
    </div>,
    destination
);
```

## DEALING WITH ARRAYS IN THE CONTEXT OF JSX
When you are displaying multiple components, you won’t always be able to manually specify them:

```js
ReactDOM.render(
  <div>
    {showCircle()}
    {showCircle()}
    {showCircle()}
  </div>,
  destination
);
```

To display all of these components, React makes it very simple:

```js
var colors = ["#393E41", "#E94F37", "#1C89BF", "#A1D363",
              "#85FFC7", "#297373", "#FF8552", "#A40E4C"];
var renderData = [];

for (var i = 0; i < colors.length; i++) {
  renderData.push(<Circle bgColor={colors[i]}/>);
}

ReactDOM.render(
  <div>
    {renderData}
  </div>,
  destination
);
```

![9-2](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/09fig02.jpg)

Figure 9-2 What you should see in your browser.

# Working with Events
## LISTENING AND REACTING TO EVENTS
Initially, our example will look like Figure 10-1.

![10-1](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/10fig01.jpg)

Figure 10-1 Our example.

After clicking the plus button a bunch of times, it will look sorta like Figure 10-2.

![10-2](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/10fig02.jpg)

Figure 10-2 After clicking the plus button a bunch of times (23?).

### Starting Point
```js
<!DOCTYPE html>
<html>
<head>
  <title>React! React! React!</title>
  <script src="https://unpkg.com/react@15.3.2/dist/react.js"></script>
  <script src="https://unpkg.com/react-dom@15.3.2/dist/react-dom.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>
  <style>
    #container {
      padding: 50px;
      background-color: #FFF;
    }
  </style>
</head>
<body>
  <div id="container"></div>
  <script type="text/babel">
  </script>
</body>
</html>
```

Inside our script tag below the container div, add the following:

```js
var destination = document.querySelector("#container");
var Counter = React.createClass({
  render: function() {
      var textStyle = {
        fontSize: 72,
        fontFamily: "sans-serif",
        color: "#333",
        fontWeight: "bold"
      };

      return (
        <div style={textStyle}>
          {this.props.display}
        </div>
      );
    }
});

var CounterParent = React.createClass({
  getInitialState: function() {
    return {
      count: 0
    };
  },
  render: function() {
      var backgroundStyle = {
        padding: 50,
        backgroundColor: "#FFC53A",
        width: 250,
        height: 100,
        borderRadius: 10,
        textAlign: "center"
      };

      var buttonStyle = {
        fontSize: "1em",
        width: 30,
        height: 30,
        fontFamily: "sans-serif",
        color: "#333",
        fontWeight: "bold",
        lineHeight: "3px"
      };

      return (
        <div style={backgroundStyle}>
          <Counter display={this.state.count}/>
          <button style={buttonStyle}>+</button>
        </div>
      );
    }
});

ReactDOM.render(
  <div>
    <CounterParent/>
  </div>,
  destination
);
```

### Making the Button Click Do Something
What we need to do is going to look roughly like this:

1. Listen for the click event on the button and specify an event handler.
2. Implement the event handler where we increase the value of our this.state.count property that our counter relies on.

```js
return (
  <div style={backgroundStyle}>
    <Counter display={this.state.count}/>
    <button onClick={this.increase} style={buttonStyle}>+</button>
  </div>
);
```

Inside our CounterParent component, add the following highlighted lines:

```js
var CounterParent = React.createClass({
  getInitialState: function() {
    return {
      count: 0
    };
  },

  increase: function(e) {
    this.setState({
      count: this.state.count + 1
    });
  },

  render: function() {
      var backgroundStyle = {
        padding: 50,
        backgroundColor: "#FFC53A",
        width: 250,
        height: 100,
        borderRadius: 10,
        textAlign: "center"
      };

      var buttonStyle = {
        fontSize: "1em",
        width: 30,
        height: 30,
        fontFamily: "sans-serif",
        color: "#333",
        fontWeight: "bold",
        lineHeight: "3px"
      };

      return (
        <div style={backgroundStyle}>
          <Counter display={this.state.count}/>
          <button onClick={this.increase} style={buttonStyle}>+</button>
        </div>
      );
    }
});
```

### Meet Synthetic Events
In React, when you specify an event in JSX like we did with onClick, you are not directly dealing with regular DOM events. Instead, you are dealing with a React-specific event type known as a `SyntheticEvent`. Your event handlers don’t get native event arguments of type MouseEvent, KeyboardEvent, etc. They always get event arguments of type SyntheticEvent that wrap your browser’s native event instead.

Each SyntheticEvent contains the following properties:

![1](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/113tab01.jpg)

**Don’t refer to traditional DOM event documentation when using Synthetic events and their properties.** Because the SyntheticEvent wraps your native DOM event, events and their properties may not map one-to-one. Some DOM events don’t even exist in React. To avoid running into any issues, if you want to know the name of a SyntheticEvent or any of its properties, refer to the React Event System document(https://facebook.github.io/react/docs/events.html) instead.

To increment our counter by 10 when the Shift key is pressed, go back to our increase function and make the following highlighted changes:

```js
increase: function(e) {
  var currentCount = this.state.count;
  if (e.shiftKey) {
    currentCount += 10;
  } else {
    currentCount += 1;
  }

  this.setState({
    count: currentCount
  });
},
```

### You Can’t Directly Listen to Events on Components
```js
var CounterParent = React.createClass({
  getInitialState: function() {
    return {
      count: 0
    };
  },

  increase: function() {
    this.setState({
      count: this.state.count + 1
    });
  },

  render: function() {
    return (
      <div>
        <Counter display={this.state.count}/>
        <PlusButton onClick={this.increase}/>
      </div>
    );
  }
});
```

When somebody clicks on our PlusButton component, the increase function will get called. In case you are curious, this is what our PlusButton component looks like:

```js
var PlusButton = React.createClass({
  render: function() {
      return (
        <button>
          +
        </button>
      );
    }
});
```

No matter how you slice and dice this, none of this matters. It doesn’t matter how simple or obvious the HTML we are returning via a component looks like. **You simply can’t listen for events on them directly.** The reason is because components are wrappers for DOM elements.

Inside the component, we can then assign the event to a DOM element and set the event handler to the the value of the prop we just passed in.Take a look at the following highlighted line:

```js
var CounterParent = React.createClass({
    .
    .
    .

  render: function() {
    return (
      <div>
        <Counter display={this.state.count}/>
        <PlusButton clickHandler={this.increase}/>
      </div>
    );
  }
});
```

In this example, we create a property called clickHandler whose value is the increase event handler. Inside our PlusButton component, we can then do something like this:

```js
var PlusButton = React.createClass({
  render: function() {
      return (
        <button onClick={this.props.clickHandler}>
          +
        </button>
      );
    }
});
```

### Listening to Regular DOM Events
```js
var Something = React.createClass({
  handleMyEvent: function(e) {
    // do something
  },

  componentDidMount: function() {
    window.addEventListener("someEvent", this.handleMyEvent);
  },

  componentWillUnmount: function() {
    window.removeEventListener("someEvent", this.handleMyEvent);
  },

  render: function() {
      return (
        <div>Hello!</div>
      );
    }
});
```

We have our Something component that listens for an event called someEvent. We start listening for this event under the componentDidMount method which is automatically called when our component gets rendered.

### The Meaning of this Inside the Event Handler
When dealing with events in React, the value of this inside your event handler is different from what you would normally see in the non-React DOM world. In the non-React world, the value of this inside an event handler refers to the element that your event is listening on:

```js
function doSomething(e) {
  console.log(this); //button element
}

var foo = document.querySelector("button");
foo.addEventListener("click", doSomething, false);
```

In the React world (when your components are created using React.createClass), the value of this inside your event handler always refers to the **component the event handler lives in**:

```js
var CounterParent = React.createClass({
  getInitialState: function() {
    return {
      count: 0
    };
  },

  increase: function(e) {
    console.log(this); // CounterParent component
    this.setState({
      count: this.state.count + 1
    });
  },

  render: function() {
      return (
        <div>
          <Counter display={this.state.count}/>
          <button onClick={this.increase}>+</button>
        </div>
      );
    }
});
```

In this example, the value of this inside the increase event handler refers to the CounterParent component. It doesn’t refer to the element that triggered the event. You get this behavior because React automatically binds all methods inside a component to this. This autobinding behavior only applies when your component is created using React.createClass. If you are using ES6 classes to define your components, the value of this inside your event handler is going to be undefined unless you explicitly bind it yourself:

```js
<button onClick={this.increase.bind(this)}>+</button>
```

# The Component Lifecycle
## MEET THE LIFECYCLE METHODS
Before we go further, it is time for you to quickly meet our lifecycle methods. They are:

- componentWillMount
- componentDidMount
- componentWillUnmount
- componentWillUpdate
- componentDidUpdate
- shouldComponentUpdate
- componentWillReceiveProps

There are three more methods that we are going to throw into the mix even though they aren’t strictly lifecycle methods, and they are:
- getInitialState
- getDefaultProps
- render

### See the Lifecycle Methods in Action
![11-1](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/11fig01.jpg)

Figure 11-1 A variation on the counter example.

Now, bring up your browser’s developer tools and take a look at the Console tab. In Chrome, you’ll see something that looks like Figure 11-2.

![11-2](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/11fig02.jpg)

Figure 11-2 The Console view in Chrome.

If you click on the plus button once, notice that your Console will show more lifecycle methods getting called (see Figure 11-3).

![11-3](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/11fig03.jpg)

Figure 11-3 More lifecycle methods getting called.

Now that you’ve seen the example, let’s take a quick look at the component that is responsible for all of this:

```js
var CounterParent = React.createClass({
  getDefaultProps: function(){
    console.log("getDefaultProps: Default prop time!");
    return {};
  },

  getInitialState: function() {
    console.log("getInitialState: Default state time!");
    return {
      count: 0
    };
  },

  increase: function() {
    this.setState({
      count: this.state.count + 1
    });
  },

  componentWillUpdate: function(newProps, newState) {
      console.log("componentWillUpdate: Component is about to update!");
  },

  componentDidUpdate: function(currentProps, currentState) {
      console.log("componentDidUpdate: Component just updated!");
  },

  componentWillMount: function() {
      console.log("componentWillMount: Component is about to mount!");
  },

  componentDidMount: function() {
      console.log("componentDidMount: Component just mounted!");
  },

  componentWillUnmount: function() {
      console.log("componentWillUnmount: Component is about to be removed from the DOM!");
  },

  shouldComponentUpdate: function(newProps, newState) {
    console.log("shouldComponentUpdate: Should component update?");
    if (newState.count < 5) {
      console.log("shouldComponentUpdate: Component should update!");
      return true;
    } else {
      ReactDOM.unmountComponentAtNode(destination);
      console.log("shouldComponentUpdate: Component should not update!");
      return false;
    }
  },

  componentWillReceiveProps: function(newProps){
    console.log("componentWillReceiveProps: Component will get new props!");
  },

  render: function() {
      var backgroundStyle = {
        padding: 50,
        border: "#333 2px dotted",
        width: 250,
        height: 100,
        borderRadius: 10,
        textAlign: "center"
      };

      return (
        <div style={backgroundStyle}>
          <Counter display={this.state.count}/>
          <button onClick={this.increase}>
            +
          </button>
        </div>
      );
    }
});
```

### The Initial Rendering Phase
When your component is about to start its life and make its way to the DOM, the following lifecycle methods get called (see Figure 11-4).

![11-4](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/11fig04.jpg)

Figure 11-4 The lifecycle methods called initially.

### The Updating Phase
#### Dealing with State Changes
When a state change happens, all the lifecycle methods in Figure 11-5 get called.

![11-5](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/11fig05.jpg)

Figure 11-5 Lifecycle methods called when a state change happens.

#### Dealing with Prop Changes
The other time your component updates is when its prop value changes after it has been rendered into the DOM. In this scenario, the lifecycle methods in Figure 11-6 get called.

![11-6](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/11fig06.jpg)

Figure 11-6 Lifecycle methods when the component’s prop value changes.

#### The Unmounting Phase
The last phase we are going to look at is when your component is about to be destroyed and removed from the DOM (see Figure 11-7).

![11-7](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/11fig07.jpg)

Figure 11-7 Only one lifecycle method is active when your component is about to be destroyed and removed from the DOM.

# Accessing DOM Elements
To highlight one such situation, take a look at the Colorizer example in Figure 12-1.

![12-1](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/12fig01.jpg)

Figure 12-1 Colorizer example.

Once you have provided a color and submitted it, the white square will turn whatever color value you provided (see Figure 12-2).

![12-2](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/12fig02.jpg)

Figure 12-2 The white square turns yellow.

![12-3](https://www.safaribooksonline.com/library/view/learning-react/9780134546513/graphics/12fig03.jpg)

Figure 12-3 We get purple and the text field is ready for the next color.

In this tutorial, we saw how “easy” it is to access a DOM element directly. React used to provide a much easier way of referencing elements. You could set the `refs` attribute on an element and initialize it to a string value:

```js
<button refs="myButton">Click me!</button>
```

You could then access this element after the component was mounted by doing something like `this.refs.myButton`.

Let’s look at the full Colorizer component with all of the ref-related shenanigans highlighted:

```js
var Colorizer = React.createClass({
    getInitialState: function() {
      return {
          color: ’’,
          bgColor: ’’
      }
    },

    colorValue: function(e) {
      this.setState({color: e.target.value});
    },

    setNewColor: function(e){
      this.setState({bgColor: this.state.color});
      this._input.value = "";
      this._input.focus();
      e.preventDefault();
    },

    render: function() {
      var squareStyle = {
        backgroundColor: this.state.bgColor
      };

      var self = this;

      return (
        <div className="colorArea">
          <div style={squareStyle} className="colorSquare"></div>
          <form onSubmit={this.setNewColor}>
            <input
                ref={
                      function(el) {
                        self._input = el;
                      }
                    }
                onChange={this.colorValue}
                placeholder="Enter a color value">
            </input>
            <button type="submit">go</button>
          </form>
        </div>
      );
    }
});
```

### Simplifying Further with ES6 Arrow Functions
```js
<input
    ref={
          function(el) {
            self._input = el;
          }
        }
    onChange={this.colorValue}
    placeholder="Enter a color value">
</input>
```

Using arrow functions, we can simplify all of this down to just the following:

```js
<input
    ref={
          (el) => this._input = el
        }
    onChange={this.colorValue}
    placeholder="Enter a color value">
</input>
```
