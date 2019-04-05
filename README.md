# <img src="https://avatars2.githubusercontent.com/u/42252722?s=100&u=82447676189516e243e244d3f949169c0e91583b&v=4" /> The FRN Stack

|Created By | Role | Last Update | Email |
|:---------:|:----:|:-----------:|:-----:|
| Daniel Scott | SEI Lead Local Instructor Dallas | 04/03/2019 | daniel.scott@generalassemb.ly |

![react meets firebase](repo_imgs/react_meets_firebase_wht.png)
For this lesson, we'll look at a secretly popular tech stack known at the FRN stack (Firebase, ReactJS, and NodeJS). 

Here are the high level points we'll cover in this lesson:

- Pre-requisites and requirements
- What is Google Firebase?
- Set up Google Firebase
- Light overview of React/Setup for lesson
- Build a Todos App
- Conclusion


Here are the learning objectives:

_By the end of this lesson, students should be able to:_

- Setup a Google Firebase Project
- Use the Google Firebase Real Time Database (RTDB) and Authentication
- Reference Google Firebase documentation
- Demonstrate preliminary understanding of Google Firebase and how to use it with React

<hr>

## Pre-requisites and Requirements

![tools](repo_imgs/tools.png)

_To have success in this lesson, students should have:_

- Familiarity with ReactJS Fundamentals..i.e. `components`, `props`, `component state`, `stateless functional components vs class based components`, and `component lifecycle methods`.
- latest version `nodejs` installed
- `create-react-app` build tool installed
- `VS Code`as their text editor!
- A Chrome Browser

_Please see below for links to the resources referenced above_

<hr>

## What is Google Firebase?

_Founded by James Tamplin and Andrew Lee as “Firebase” in 2011, then acquired by Google in 2014._

_“Firebase frees developers, so they can focus on creating phenomenal user experiences. You don’t need to manage servers, write an API, or configure a datastore.”_

_“Firebase is your server, your API and your datastore."_

### Who Uses Google Firebase?

![who uses google firebase?](repo_imgs/who_uses_firebase.png)

Ever since Google acquired Firebase in 2014, it's rise in popularity has skyrocked to where it is today. 

Since the Google acquisition, Firebase exploaded with robust features for both web and mobile applications.

Many companies and their developers have found tremendous value in this technology, which is why you probably recognize most of these brands!

### Not Just A Database

When people hear "Google Firebase" for the first time, they often get confused thinking it's just a Database. Although the Real Time Database is a core feature, it's just one of several services you can use from Google Firebase:

![firebase services](repo_imgs/firebase_services.png)

**The Best Definition of Google Firebase is that it's a "BAAS" (Backend As A Service)**

![google firebase](repo_imgs/google_firebase.png)

### The Google Firebase Real Time Database (RTDB)
- The Core Service That Put the Spotlight on Firebase
- A Single JSON Object that allows up to 32 levels of Depth 
  
  (We don't recommend nesting your data that deep though)

<hr>

## Setup Google Firebase

It's the moment we've all been waiting for! 

It's time to set up Google Firebase!

**The First Step to Get Started is to "Signup For Google Firebase" and "signin"**

Go to: [https://firebase.google.com/](https://firebase.google.com/)


#### Step 1 - Click "Get Started":
![fig 1](repo_imgs/fig_1.png)

#### Step 2 - Click "Add Project":
![fig 2](repo_imgs/fig_2.png)

#### Step 3 - Complete Project Details and Name Your Project: React-Fire-Todos" Then Click "Create Project":
![fig 3](repo_imgs/fig_3.png)

#### Click Continue
![fig 3.2](repo_imgs/fig_3_1.png)

#### Step 4 - Click "Database"
![fig 4](repo_imgs/fig_4.png)

#### Step 5 - Scoll Down Until You See "Choose Realtime Database" Click "Create Database"
![fig 5](repo_imgs/fig_5.png)

#### Step 6 - Select "Start in Test Mode" and Then Click "Enable"
![fig 6](repo_imgs/fig_6.png)


<hr>

## Setup Our React Frontend
![react logo](repo_imgs/react_logo.png)

It's time to make sparks fly! 

Assuming you have the `create-react-app` build tool installed. 

Navigate to a place on your machine where you can work and then run `create-react-app react-fire-todos` to build a react application and install base dependencies.

Once the build finishes, we'll clean it up and add directories/files as we prepare for Firebase integration.

<hr>

### Step 1 - Remove `logo.svg` and JSX from `App.js`

- Remove `logo.svg` inside of `./src/`
- Remove unnecessary JSX code from `App.js`
  
Your `App.js` should look like this once you're done:

```js
// Inside of App.js

import React, { Component } from 'react'
import 'App.css'

class App extends Component {
    render(){
        return(
            <div className="App">
            
            </div>
        )
    }
}

export default App
```
**NOTE: We've left the root div/JSX element in place**

<hr>

### Step 2 - Create config directory/file for Google Firebase

- Create a directory inside of `./src/` named `firebaseConfig`
- Create a file named `index.js` inside of `./src/firebaseConfig/`

You're directory/file structure should look like this once you're done:

![directory structure](repo_imgs/directory_structure.png)

<hr>

### Step 3 - Enter Google Firebase

Now we're ready to install Google Firebase! 

From the root of your project, go ahead and run the command `npm i firebase`.

Then, while that's installing, go back to the Google Firebase console for our config code:

#### Step 1 - From the RTDB Dashboard, Click the Gear Widget Then "Project Settings"
![fig 7](repo_imgs/fig_7.png)

#### Step 2 - Scroll to the Bottom and Click the `</>` Icon
![fig 8](repo_imgs/fig_8.png)

#### Step 3 - Now We Have Access to Our Config Code 

![fig 9](repo_imgs/fig_9.png)

Copy the `config` object from the console to add to `./src/firebaseConfig/index.js` as shown below:

```js
import firebase from 'firebase/app'
import 'firebase/database'
import 'firebase/auth'


const config = {
    apiKey: YOUR_API_KEY,
    authDomain: YOUR_AUTH_DOMAIN,
    databaseURL: YOUR_DATABASE_URL,
    projectId: YOUR_PROJECT_ID,
    storageBucket: YOUR_STORAGE_BUCKET,
    messagingSenderId: YOUR_MESSAGE_SENDER_ID
};

firebase.initializeApp(config)

export default firebase
```
**Please NOTE:** For the simplicity of this lesson, we'll write our actual keys/credentials in this file, however...

:warning: **DO NOT PUSH TO GITHUB** :warning:


:warning: **DO NOT PUSH TO GITHUB!** :warning:


:warning: **DO NOT PUSH TO GITHUB!** :warning:


:warning: **DO NOT PUSH TO GITHUB!** :warning:


:warning: **DO NOT PUSH TO GITHUB!** :warning:


:warning: **DO NOT PUSH TO GITHUB!** :warning:

Some of you will probably do this anyways ... but you've been warned
... because doing so will run the risk of your credentials being stolen by bad actors.


<img src="https://media.giphy.com/media/xcnMwNunTCn9m/giphy.gif" />


<hr>

### Step 4 - Create your components files

Now it's time to begin creating components for our project!

The architecture of this project is fairly straightforward. 
We'll have one parent "smart component", this component is charged with passing certain members down to our stateless functional components as props ... i.e. component state and methods.

Create a directory named `components` inside of `./src`. 

Inside of `./src/components/` create two files:
- `Dashboard.js`
- `Login.js`

Once you're done, your directory/file structure should look like this:

![component files](repo_imgs/directory_structure2.png)

<hr>

### Step 5 - Add boilerplate code to component files

For your `Dashboard.js` file, we'll write a stateless functional component. 

Go ahead and add this code:

```js
// Inside of Dashboard.js

import React from 'react'

const Dashboard = props => (
    <div>
        <h5>Here are your Todos</h5>
        <div>
            {
                /* We'll print our todos here */
            }
            <form>
                <input name="text"/>
                <button>Add Todo</button>
            </form>
        </div>
    </div>
)

export default Dashboard
```

For the `Login.js` file, we'll write a stateless functional component in it as well. 

Go ahead and add the following code to that file:

```js
// Inside of Login.js

import React from 'react'

const Login = props => (
    <button>Login with Google</button>
)

export default Login
```

Next, for our parent component, `App.js`, we'll add the following code:

```js
// Inside of App.js

import React, { Component } from 'react'
import Dashboard from './components/Dashboard'
import 'App.css'


class App extends Component {
    render(){
        return(
            <div className="App">
                <h1>Welcome to React Fire Todos</h1>
                <Dashboard />
            </div>
        )
    }
}

export default App
```

:tada: Awesome! Now we're ready to begin working with Firebase!

<hr>

## Firebase 101

For this part, we'll spend a few minutes getting familiar with the basic CRUD (**CREATE READ UPDATE DELETE**) operations of the Google Firebase RTDB (Real Time Database).

<hr>

### Setup Parent Component

1. Import `firebase` inside of `App.js`
2. Setup the `componentDidMount()` lifecycle method
3. `console.log(firebase.database())` from inside of the `componentDidMount()` lifecycle method

Once you're done, your code inside of `App.js` should look like this:

```js

// Inside of App.js

import React, { Component } from 'react'
import Dashboard from './components/Dashboard'
import firebase from './firebaseConfig'
import 'App.css'


class App extends Component {
    
    componentDidMount(){
        console.log(firebase.database())
    }

    render(){
        return(
            <div className="App">
                <h1>Welcome to React Fire Todos</h1>
                <Dashboard />
            </div>
        )
    }
}

export default App
```

If we haven't done so already, it would be a good idea to run our react front-end using it's included dev server. We can do that with the following command from the root directory of our project:

`npm start`

Now, once our component mounts, we should see our Database object logged to the console:

![console log](repo_imgs/console_log.png)


<hr>

### Create Data

Let's see how creating data with the Firebase RTDB works.


#### Let's create a single document.

Here's the code:

```js
// First let's save a piece of data to a variable we can reference later
const todo = { text: "Clean my room" }

firebase.database().ref('todos')
.set(todo)
.then(() => console.log("Todo Written Successfully"))
.catch(error => {
    console.log("Something Went Wrong: ", error.message)
})

```
This is what's happening:

1. First we expose our database object by calling [`.database()`](https://firebase.google.com/docs/reference/js/firebase.database) on `firebase`
2. Then we have access to a method called [`.ref()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference#ref), which allows us to reference a "collection" location inside our RTDB; it will be created if it doesn't exist 
3. Now that we've referenced the location where our data belongs, we can pass our data to a method called [`.set()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference?authuser=0#set), this method writes data to the the referenced database location, and will also overwrite any data at this location and all child locations
4. According to the [firebase documentation](https://firebase.google.com/docs/reference/js/firebase.database.Reference?authuser=0#set), [`.set()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference?authuser=0#set) returns a promise, so we can handle either case of it's outcome with [JavaScript's `.then()` or `.catch()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
5. In this case we can `console.log()` a message


#### What if we needed to create multiple "documents" in a collection?

_The Firebase RTDB has a special way of doing that_

Here's the code:

```js
    
const todoText = "Clean my room"

firebase.database().ref('todos')
.push({text: todoText})
.then(() => console.log("Todo Written Successfully"))
.catch(error => {
    console.log("Something went wrong: ", error.messge)
})

```

This is what's happening:

1. Now that we've referenced the location where our data belongs with `.ref('todos')`, we can pass our data to a method called [`.push()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference#push), this allows us to add a child key to our `todos` collection with a unique identifier as it's name and our data as it's value
   - Subsequent calls to `.push()` with data passed in will continue to add child keys to our `todos` key
2. According to the [firebase documentation](https://firebase.google.com/docs/reference/js/firebase.database.Reference#push), [`.push()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference#push) returns a promise, so we can handle either case of it's outcome with [JavaScript's `.then()` or `.catch()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
3. In this case we can `console.log()` a message

<hr>

### Read Data 

Let's see how reading data with the Firebase RTDB works.

Here's the code:

#### We can read a single piece of data by it's unique key once

```js
firebase.database().ref('todos/-Lb0H9NA_e32dvLg86OC')
.once('value')
.then(snapshot => console.log(snapshot.val()))
.catch(error => {
    console.log('Something Went Wrong', error.message)
})
```
This is what's happening:

1. First we reference the data by it's unique key using a string path: `todos/-Lb0H9NA_e32dvLg86OC`
2. Then we call firebase's [`.once()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference?authuser=0#once) method, which listens for the specified event type we pass in once; in this case we specify `value`
   - You can check out more event types [here](https://firebase.google.com/docs/reference/js/firebase.database?authuser=0#eventtype) 
3. `.once()` returns a `Promise`, which we can handle with JavaScript's `.then()` or `.catch()`
4. Upon a success, the callback we pass as an argument to `.then()` get's passed a current snapshot of our data, which by convention, Google Firebase calls [`dataSnapshot`](https://firebase.google.com/docs/reference/js/firebase.database.DataSnapshot?authuser=0) or `snapshot`
5. We can then access the unique key or properties of that `snapshot`, with `.key` or by calling `.val()` respectively
6. Upon a failure, the callback we pass as an argument to `.catch()` get's passed an error object with a message property we can access to gather information regarding the failure


#### We can create an array containing multiple pieces of data 

**NOTE:** _This is the primary way to read data from the RTDB._

```js
firebase.database().ref('todos')
.on('value')
.then(snapshot => {
    const dataArray = []
    snapshot.forEach(childSnapshot => {
        dataArray.push({
            id: childSnapshot.key,
            ...childSnapshot.val()
        })
    })
    console.log(dataArray)
    // We could also set our state array here 
})
.catch(error => {
    console.log('Something Went Wrong', error.message)
})

```

This is what's happening:

1. First we reference our todos collection using Firebase's [`.ref()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference?authuser=0#ref)
2. Then we call Firebase's [`.on()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference?authuser=0#on) listener method that will listen for a particular event type at our reference; in this case, we listen for a [`value`](https://firebase.google.com/docs/reference/js/firebase.database?authuser=0#eventtype) type
   - Unlike the `.once()` method, `.on()` initializes an ongoing subscription to Firebase that always listens for the event type we specify; *"we call it and forget it"*
3. Just like `once()`, `.on()` returns a `Promise` we can handle with JavaScript's `.then()` or `.catch()` for success and failure repectively
4. For the `value` event type, we'll get the initial [`snapShot`](https://firebase.google.com/docs/reference/js/firebase.database.DataSnapshot?authuser=0) stored at whatever we pass to `.ref()`, and then trigger again each time the data changes. That `snapshot` gets passed to the annonymous callback function we pass into `.then()`
5. We then use Firebase's [`.forEach()`](https://firebase.google.com/docs/reference/js/firebase.database.DataSnapshot?authuser=0#foreach), to enumerate the `top-level` children from our `snapshot` thus providing access to each `childSnapshot`
6. `.forEach()` takes a callback as an argument so we can perform an action on each `childSnapshot`; in this case, we're creating a new object literal for each `childSnapshot` and pushing it into an array
7. With all of this in place, we can update state with a new array each time a change pertaining to the event we specify is detected. (i.e. ... `"value"`, `"child_added"`, `"child_changed"` ...etc)

<hr>

### Update Data

Let's see how updating data with the Firebase RTDB works.

Here's the code:

```js
// Here's the todo text we'd like to update an existing todo to
const updatedTodoText = "Clean the living room"

firebase.database().ref('todos/-Lb0H9NA_e32dvLg86OC')
.update({ text: updatedTodoText })
.then(() => console.log("Todo Updated Successfully"))
.catch(error => {
    console.log("Something went wrong: ", error.message)
})

```

This is what's happening:

1. First we reference a single piece of data we'd like to remove using `.ref()`, passing in a string path to our referenced data
2. Then we call Firebase's [`.update()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference?authuser=0#update) passing in the key along with it's updated value; Firebase handles the rest! :sunglasses:
3. `.update()` is an extremely powerful Firebase method, so it's recommended to [check out the documentation](https://firebase.google.com/docs/reference/js/firebase.database.Reference?authuser=0#update) to fully grasp it's capabilities
4. Just like many of the **CRUD** operations methods for the Firebase RTDB, `.update()` returns a promise we can pass to either `.then()` or `.catch()` depending on success or failure

<hr>

### Delete Data

Let's see how deleting data with the Firebase RTDB works.

Here's the code:

```js
firebase.database().ref('todos/-Lb0H9NA_e32dvLg86OC')
.remove()
.then(() => console.log('Todo Removed Successfully'))
.catch(error => {
    console.log('Something Went Wrong: ', error.message)
})
```

Here's what's happening:

1. First we reference a single piece of data we'd like to remove using `.ref()`, passing in a string path to our referenced data
2. Then we call Firebase's [`.remove()`](https://firebase.google.com/docs/reference/js/firebase.database.Reference#remove) method, which will "remove" the data at the referenced RTDB location
3. Then we can handle the `Promise` that gets returned from calling `remove()` just as before using JavaScript's `.then()` and `.catch()`

<hr>

## Let's Build an App!

One of the best ways to learn a new skill/technology is by incorporating them into a project!

That said, let's build a simple todo app using React and Firebase!

We'll keep it simple, no additional styling, no React Router, just pure React and Firebase.

"Todo" this, we'll work in steps, let's get started:

<hr>

### Step 1 - Setup Parent Component State:

For simplicity, we'll use `App.js` as our parent component.

Here's the code:

```js

// Inside of App.js

class App extends Component {
    
    state = {
        text: "",
        todos: [],
        user: null,
        isAuthenticated: false
    }
    
    render(){
        ...
 
```
1. We'll use property initializer syntax for cleanliness
2. We need a `text` state property to store input data from our form
3. We'll store a collection of todo objects inside a `todos` array property
4. Later on we'll explore how firebase handles authentication, so we'll setup properties to store data based on authentication state.

<hr>

### Step 2 - Create a Method to Update Component State

To handle form data from our `<Dashboard />` component, we’ll create a `handleChange()` method inside of `App.js` to update it’s state `text` property based on user input.

For more context on how React handles forms, you can check out [this section from the documentation](https://reactjs.org/docs/forms.html)

Here's the code:

```js
// Inside of App.js
    
class App extends Component {
    
    state = {
        text: "",
        todos: [],
        user: null,
        isAuthenticated: false
    }

    handleChange = e => {
        this.setState({ [e.target.name]: e.target.value })
    }
    
    render(){
        ...
 
```

<hr>

### Step 3 - Pass Methods and State as Props

To use our `handleChange()` method and `text` state property, we’ll pass them as props to our `<Dashboard />` component.

Here's the code:

```js
// Inside of App.js

render() {
  return (
    <div className="App">
      <h1>Welcome to React Fire Todos</h1>
          <Dashboard
            text={this.state.text}
            handleChange={this.handleChange} 
          />
    </div>
  );
}
```

<hr>

### Step 4 - Wire Up Input Element in `<Dashboard />` Component

From inside our `<Dashboard />` component, we'll reference our `text` and `handleChange` members from `props` using `value` and `onChange`.

Here's the code:

```js
// Inside of Dashboard.js

import React from 'react'

const Dashboard = props => (
    <div>
        <h5>Here are your todos</h5>
        <div>
            {
                /* We'll Print Our Todos here*/
            }
        </div>
        <form>
            <input
            name="text" 
            value={props.text} 
            onChange={props.handleChange}
            />
            <button>Add Todo</button>
        </form>
    </div>
)

export default Dashboard
```

<hr>

### Step 5 - Create a Submit Handler Method for `<App />` component

let’s create a submit handler method for our form element.

Here's the code:

```js
// Inside of App.js

handleSubmit = e => {
  e.preventDefault()
  firebase.database().ref('todos')
  .push({ text: this.state.text })
  .then(() => {
    this.setState({ text: "" })
    console.log("Data Created Successfully")
  })
  .catch(error => {
      console.log("Something Went Wrong: ", error)
   })
}
```

<hr>

### Step 6 - Pass Submit Handler as Prop to `<Dashboard />` Component

In our `<App />` component, we’ll pass our submit handler as a prop to our `<Dashboard />` component.

Here's the code:

```js
// Inside of App.js

render() {
  return (
    <div className="App">
      <h1>Welcome to React Fire Todos</h1>
          <Dashboard
            text={this.state.text}
            handleChange={this.handleChange}
            handleSubmit={this.handleSubmit} 
          />
    </div>
  );
}
```

<hr>

### Step 7 - Final Setup of Form Element

Let's reference the `handleSubmit` event handler from props in our form using `onSubmit`

Here's the code:

```js
// Inside of Dashboard.js

import React from 'react'

const Dashboard = props => (
    <div>
        <h5>Here are your todos</h5>
        <div>
            {
                /* We'll Print Our Todos here*/
            }
        </div>
        <form onSubmit={props.handleSubmit}>
            <input
            name="text" 
            value={props.text} 
            onChange={props.handleChange}
            />
            <button>Add Todo</button>
        </form>
    </div>
)

export default Dashboard
```

<hr>

### Step 8 - Setup of Data Fetch Subscription using React Lifecycle Method

Inside our `<App />` component we'll take advantage of the `componentDidMount()` lifecycle method to initialize a subscription once the component mounts. 

As we learned earlier, this subscription will update our state array anytime a change is detected.


Here's the code:

```js
// Inside of App.js

componentDidMount(){
    firebase.database().ref('todos')
    .on('value', snapshot => {
      const newStateArray = []
      snapshot.forEach(childSnapshot => {
        newStateArray.push({
          id: childSnapshot.key,
          ...childSnapshot.val()
        })
      })
      this.setState({ todos: newStateArray })
    })
}

```

<hr>

### Step 9 - Pass State Array to `<Dashboard />` Component as a Prop

We'll use our `<Dashboard />` component to render our list of todos.

let's pass our todos state array to our `<Dashboard />` component as a prop.

Here's the code:

```js
render() {
  return (
    <div className="App">
      <h1>Welcome to React Fire Todos</h1>
          <Dashboard
            text={this.state.text}
            todos={this.state.todos}
            handleChange={this.handleChange}
            handleSubmit={this.handleSubmit} 
          />
    </div>
  );
}
```

<hr>

### Step 10 - Print Data From State Array in `<Dashboard />` Component 

Let's iterate our state array using JavaScript’s `.map()` to transform it’s elements into JSX `<p>` elements. 

**NOTE:** _Don't forget to add your key prop!_ :sunglasses:

Here's the code:

```js
// Inside of Dashboard.js

import React from 'react'

const Dashboard = props => (
    <div>
        <h5>Here are your todos</h5>
        <div>
            {
                props.todos.map(todo => (
                    <p key={todo.id}>{todo.text}</p>
                ))
            }
        </div>
        <form onSubmit={props.handleSubmit}>
            <input
            name="text" 
            value={props.text} 
            onChange={props.handleChange}
            />
            <button>Add Todo</button>
        </form>
    </div>
)

export default Dashboard
```

<hr>

### Step 11 - Create a Method to Remove Todos

Let’s set up a method inside our `<App />` component to remove a todo item based on it’s id. We can create a dynamic path string for `.ref()` using template strings.

In case you're wondering how we'll manage state, don't worry! 

Once an item is removed, our Firebase subscription will automatically update state for us. :smiley:

Here's the code:

```js
// Inside of App.js

handleRemove = todoId => {
  firebase.database().ref(`todos/${todoId}`)
  .remove()
  .then(() => console.log("Data Removed Successfully"))
  .catch(error => { 
      console.log("Something Went Wrong", error)
   })
}
```

<hr>

### Step 12 - Pass `handleRemove` to `<Dashboard />` Component

We need to use our `handleRemove` method in our `<Dashboard />` component, so let's pass it down as a prop.

Here's the code:

```js
// Inside of App.js

render() {
  return (
    <div className="App">
      <h1>Welcome to React Fire Todos</h1>
          <Dashboard
            text={this.state.text}
            todos={this.state.todos}
            handleChange={this.handleChange}
            handleSubmit={this.handleSubmit} 
            handleRemove={this.handleRemove}
          />
    </div>
  );
}
```

<hr>

### Step 13 - Finish Remove Todo Feature in `<Dashboard />` Component

Let's finish up our simple “delete todo” feature inside our `<Dashboard />` component.

For simplicity, we don't need to set up anything fancy, just a simple `<span>` element configured to for `click` events. 

We'll reference our `handleRemove` method passing
in the expected todo id as an argument.

Here's the code:

```js
// Inside of Dashboard.js

import React from 'react'

const Dashboard = props => (
    <div>
        <h5>Here are your todos</h5>
        <div>
            {
                props.todos.map(todo => (
                    <p key={todo.id}>
                        <span onClick={() => props.handleRemove(todo.id)}>
                        X</span>&nbsp;{todo.text}
                    </p>
                ))
            }
        </div>
        <form onSubmit={props.handleSubmit}>
            <input
            name="text" 
            value={props.text} 
            onChange={props.handleChange}
            />
            <button>Add Todo</button>
        </form>
    </div>
)

export default Dashboard
```

<hr>

### Step 14 - Simple Firebase Auth

It's time to make some sparks fly! 

We're going to use the `Firebase SDK` (**Software Development Kit**) for managing authentication state and give our user a simple popup window to "login" using their google account.

Depending on Authentication state, we can change component state, which in turn will allow us to manage what our user sees.

In this lesson, we'll conditionally render components based on authentication state.

First we need to setup our `Firebase` project to allow us to use `Google Login`

#### From the "Project Overview" Screen, Click Authentication

![setup_auth01](repo_imgs/setup_auth01.png)

#### From "Authentication", click "Sign-In method" and then "Google"

![setup_auth02](repo_imgs/setup_auth02.png)

#### Click "Enable", enter your email, then click "Save"

![setup_auth03](repo_imgs/setup_auth03.png)

#### Verify Google Sign-in is "Enabled" in green

![setup_auth04](repo_imgs/auth_setup04.png)

#### Summary - We are fully ready to use Firebase Auth :tada:

<hr>

### Setup Login Method

Let’s set up a feature to allow a user to sign in with Google. 

**NOTE:** This workflow is adapted from the [Firebase SDK workflow documentation](https://firebase.google.com/docs/auth/web/google-signin?authuser=0).

Here's the code:

```js
// Inside of App.js

  handleLogin = () => {
    const provider = new firebase.auth.GoogleAuthProvider();
    firebase.auth().signInWithPopup(provider)
    .then(() => {
      console.log("User Logged In Successfully")
    })
    .catch(error => {
      console.log("Something Went Wrong: ", error.message)
    })
  }

```

Here's what's happening:

1. To Use the Google Sign-In Method, we instantiate a new instance of the `GoogleAuthProvider` from the `firebase.auth` object, and assign what gets returned to a new variable we'll call `provider`
2. Then we call `firebase.auth()`, which exposes methods we can use on Firebase's `auth()` object; in this instance, we'll use `signInWithPopup`
3. `signInWithPopup` expects a provider as it's argument, so we'll pass that in.
4.  A `Promise` gets returned, which we can handle with JavaScript's `.then()` or `.catch()`

<hr>

### Setup Auth State Subscription

Let’s set up an auth state subscription to actively check if a user has been authenticated based on authentication state.


Here's the code:

```js
// Inside of App.js

  componentDidMount(){
    firebase.database().ref('todos')
    .on('value', snapshot => {
      const newStateArray = []
      snapshot.forEach(childSnapshot => {
        newStateArray.push({
          id: childSnapshot.key,
          ...childSnapshot.val()
        })
      })
      this.setState({ todos: newStateArray })
    })

    /* Here's where we setup our Auth State Subscription.
     * We can use an if else statement or a ternary expression
     * to conditionally set component state based on 
     * Authentication state.
     */
    firebase.auth().onAuthStateChanged(firebaseUser => {
      firebaseUser ?
        this.setState({
          user: firebaseUser.displayName,
          isAuthenticated: true
        })
        :
        this.setState({
          user: null,
          isAuthenticated: false
        })
    })
```

This is what's happening:

1. Just like for our `Firebase RTDB` subscription, the `onAuthStateChanged()` method, when called, sets up a subscription.
2. Anytime a change is detected, `onAuthStateChanged()` will return our authenticated user, or `null` depending on auth state respectively.
3. We can then change component state using an if statement or ternary expression like in this example above

<hr>

### Conditionally Render Components 

We’ll keep our user flow simple by conditionally rendering our login button based on component state. 

A ternary expression is an easy way to implement this. 

We’ll also pass our `handleLogin` method to our `<Login />`component as a prop.

Here's the code:

```js
// Inside of App.js

render() {
  return (
    <div className="App">
      <h1>Welcome to React Fire Todos</h1>
      {
          this.state.isAuthenticated ? 
          <Dashboard
            text={this.state.text}
            todos={this.state.todos}
            handleChange={this.handleChange}
            handleSubmit={this.handleSubmit} 
            handleRemove={this.handleRemove}
          /> 
          :
          <Login
            handleLogin={this.handleLogin} 
          />
      }
    </div>
  );
}
```

<hr>

### Finish Login Button 

Let's set up our `<login />` component to call the `handleLogin` method from props.

Here's the code:

```js
import React from 'react'

const Login = props => (
    <button onClick={props.handleLogin}>
        Login With Google
    </button>
)

export default Login
```

<hr>

### Create a Logout Method

Our last job for this app is to create a method to sign a user out. Once this action is resolved, our `onAuthStateChanged` subscription will trigger and change our component state.

Here's the code:

```js
handleLogout = () => {
  firebase.auth().signOut()
  .then(() => {
    console.log("User Logged Out Successfully")
  })
  .catch(error => {
    console.log("Something Went Wrong: ", error.message)
  })
}
```

<hr>

### Pass `handleLogout` As a Prop to `<Dashboard />`

Let’s pass our `handleLogout` method as a prop to our `<Dashboard />` component so we can wire it to a logout button.

Here's the code:

```js
// Inside of App.js

render() {
  return (
    <div className="App">
      <h1>Welcome to React Fire Todos</h1>
      {
          this.state.isAuthenticated ? 
          <Dashboard
            text={this.state.text}
            todos={this.state.todos}
            handleChange={this.handleChange}
            handleSubmit={this.handleSubmit} 
            handleRemove={this.handleRemove}
            handleLogout={this.handleLogout}
          /> 
          :
          <Login
            handleLogin={this.handleLogin} 
          />
      }
    </div>
  );
}
```
<hr>

### Create Logout Button

Now we can create our logout button inside our `<Dashboard />` component and wire it to the handleLogout method we passed as a prop.


Here's the code:

```js
import React from 'react'

const Dashboard = props => (
    <div>
        <h5>Here are your todos</h5>
        <button onClick={props.handleLogout}>Logout</button>
        <div>
....
```


<hr>

### Conclusion - At this point, we've...
1. Setup a Google Firebase Project
2. Use the Google Firebase Real Time Database (RTDB) and Authentication
3. Learn how to reference Google Firebase documentation

...and most importantly, we should now have a preliminary understanding of Google Firebase and how to use it with React.

**PLEASE NOTE:** There are other ways to use Google Firebase with React; this is one way that happens to be a simpler les complex way...

There are several items referenced above, but feel free to check out the higher-level references below:

### References:
- [Google Firebase](https://firebase.google.com/)
- [Google Firebase Auth](https://firebase.google.com/docs/auth/web/google-signin)
- [Google Firebase Database](https://firebase.google.com/docs/reference/js/firebase.database.Reference)
  