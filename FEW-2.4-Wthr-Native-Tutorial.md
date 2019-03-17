# FEW 2.4 Tutorial - Wthr-Native

What's Wthr? It's a new native app that shows the current weather info on your phone. 

What does it mean to be a native app? As a native app, it runs truly native code on your device. 

Does it work on iOS or Android? It runs on both! This project is built with React Native. React Native can build for Android and iOS both from the same code base. 

By completing this tutorial you will have created a native app, suitable for publishing to the App store! 

What do I need to know to complete this tutorial? There is little in the way of prerequisites. You need to know the basics of JavaScript. If you have experience with React that will help but is not required. 

You do need a computer with a text editor and mobile phone, iOS or Android for testing your project. 

You can also test from the desktop using the iOS or Android simulator. This is more work than testing on a real phone. The tutorial here will test from a real device. 

## What is React Native? 

React Native is based on React which is a JavaScript library for creating user interfaces. React Native is written with JavaScript using the syntax and patterns used with React but compiles into native iOS or Android code. 

Read more about it [here](https://facebook.github.io/react-native/).

## Getting started 

### Node.JS

To work with React Native you'll need to install Node.js. 

... installing node...

### Installing Xcode or Android Studio

If you're building apps for iOS you'll want to install Xcode. This only runs on a Mac. If you want to build apps for Android you'll want to install Android Studio. This runs on either Mac or Windows. 

... install Xcode 

... Install Android Studio 

Install the command line tools. You'll use these to create your base projects. 

Open the terminal and use the command below replacing `<NameOfProject>` with the name of the project you are creating. 

`expo init <NameOfProject>`

The command will prompt you for the type of starter project you want to create. Choose 'Blank template'

Next, the command prompts you for an app name. This can be different from the project name. 

Wait for the process to finish installing all of the dependent files. 

You'll need the Expo App to view your 

Next, navigate to the new project folder in the terminal. 

`cd <NameOfProject>`

Before running the App on your phone you'll need to install Expo. Expo runs in your phone and is used to preview your App while you work. 

iOS: https://itunes.apple.com/app/apple-store/id982107779

Android: https://play.google.com/store/apps/details?id=host.exp.exponent&referrer=www

From here you run the project by typing:

`npm start` or `yarn start`

This should open a browser window which looks something like: 

![ScreenShot-1.png](ScreenShot-1.png)

Scan the QR code in the lower left with your phone. On the iPhone you can open the camera and scan the image, you don't need to take a picture. The phone should open a notification asking if you want to open Expo. 

If you don't have Expo you'll need to install it on your phone 

## React and React Native Basic concepts 

React projects are written in JavaScript. The basic building block in React is the Component. Components are usually things you can see on the screen and may also have some business logic code that manages their behavior. 

Components can be written as a function or as a class that extends `React.Component`. 

Look at App.js. This file in the entry point. It's also the top level component. Think of components like a tree. One component can branches/child components and these can have their own children. App.js is like the root of the tree. 

```JavaScript 
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';

export default class App extends React.Component {
  render() {
    return (
      <View style={styles.container}>
        <Text>Open up App.js to start working on your app!</Text>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

The first two lines import React from the 'react' package. The second line imports two native Components: `Text`, and `View` from the 'react-native' package. `StyleSheet` is a helper Object for creating styles sheets in React Native.  

```JavaScript 
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';

...
```

The next block of code is the definition of a component. This component is named App, and it extends `React.Component`. 

```JavaScript 
...
export default class App extends React.Component {
  render() {
    return (
      <View style={styles.container}>
        <Text>Open up App.js to start working on your app!</Text>
      </View>
    );
  }
}
...
```

Components that extend `React.Component` must implement a render function. The `render()` method must return JSX. 

JSX is an extension of the JavaScript language. It allows you to write code that looks like HTML/XML within your JavaScript. 

Here you can see the render method returns. 

```JSX
<View style={styles.container}>
  <Text>Open up App.js to start working on your app!</Text>
</View>
```

This is a View component with a child Text component. These are displayed on the screen in the default app. Remember these were imported above. 

The last snippet of the code defines an object that will be used to style the components here in the app component. 

```JavaScript 
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

Notice the property `container` has four properties with values. These properties: flex, backgroundColor, alignItems, and `justifyContent` are standard CSS properties and the value are the same values you would have used in CSS. 

Summary

React native build truly native apps from JavaScript and React. 

React apps are built from components. 

Components can be written as a function (I'll show this later) or as a class that extends `React.Component`. 

Components are styled with JavaScript using standard CSS properties. 

### Native Components 

React Native uses native components. You must use Native components to build apps with React Native. So far we've seen the `View` and `Text` Components.

#### Text 

Makes text 

`<Text>Some text that is displayed...</Text>`

#### View 

A view is a rectangular area on the screen that can display child elements. 

```
<View>
  ...Child Components...
</View>
```

### Styling Components 

React native supports a subset of CSS style properties and units. 

Typically you'll set all styles "inline" on each element and define them as a JS Object. 

`<View style={{backgroundColor:'#f00'}}></View>`

### Activity 

Define a component that displays the Weather Data. Create a new file name it 'DisplayWeather.js'. make a folder in your project named: 'Components' save this file there. 

Add the following to DisplayWeather.js. 

```JSX
import React from 'react'
import { Text, View, StyleSheet } from 'react-native'

const DisplayWeather = (props) => {
  return (
    
  )
}

export default DisplayWeather
```

This defines a simple component. This component is defined as a function. Component function based component must return JSX and should take a single parameter named props. 

```JSX
import React from 'react'
import { Text, View, StyleSheet } from 'react-native'

const DisplayWeather = (props) => {
  return (
    <View>
      <Text>72˚</Text>
    </View>
  )
}
```

Add a View and Text Component. The View will act as a container for the Text and the Text will display the temperature. For now, we will assume the temperature is 72˚. In the future, you will get the weather data from an online service and display the actual temperature here. 

```JSX
import React from 'react'
import { Text, View, StyleSheet } from 'react-native'

const DisplayWeather = (props) => {
  return (
    <View style={styles.container}>
      <Text style={styles.temp}>72˚</Text>
    </View>
  )
}

export default DisplayWeather

const styles = StyleSheet.create({
  container: {
    flex: 1, 
    justifyContent: 'center'
  }, 
  temp: {
    fontSize: 40,
    fontWeight: 'bold'
  }
})
```

Lastly, add a style sheet. Do this by defining a variable named `styles` and assigning it an Object with CSS properties that can be applied to Components. 

Look at the code above notice the styles object defines keys, `container` and `temp`, that each holds an object. These objects are assigned to the `style` prop on each of the two components. 

## Test your Component 

Import and display this component in App. Add the following at the top of App.js. 

`import DisplayWeather from './DisplayWeather'`

Notice, when importing your own files you'll need to include a path. Since the file is in the same folder the path begins: './'

Use your component in the `render()` method in the App Component. 

```JSX
<View style={styles.container}>
  <DisplayWeather />
</View>
```

Notice that you don't need to use a closing tag for `DisplayWeather` since it doesn't have any children. You do need to use /> to 'self-close' this tag. 

Challenge: 

Add another Text component to display a description of the weather. Edit the Display Weather component. Add another Text component below the Temp. Use some text that describes the weather, something like: 

> Partly Cloudy

Save and test your work. Your app should refresh its view in Expo. 

## Get the geolocation

To get the weather data you need to know the location of the phone. We can get this: 

`navigator.geolocation.getCurrentPosition(success, error, options)`

The component needs to know if the location data is available or not. Getting location data is an asynchronous operation. You'll need to make a request and wait for a response. 

## Component Lifecycle methods 

Components have a lifecycle that can be used to track when they are created and when they are removed. You would like the App Component to get the geolocation when the component is created. To do this add this method to the App Class. 

```JavaScript 
...
componentDidMount() {
  navigator.geolocation.getCurrentPosition((location) => {
    console.log(location)
  }, (err) => {
    console.log(err.message)
  })
}
...
```

The `componentDidMount()` method is called when the component is created and added to a view. The code in this method will run at that time. The code here requests the current position. If the request is successful it prints the data to the console if not it prints an error. 

```JavaScript 
export default class App extends React.Component {

  componentDidMount() {
    navigator.geolocation.getCurrentPosition((location) => {
      console.log(location)
    }, (err) => {
      console.log(err.message)
    })
  }

  render() {
    return (
      <View style={styles.container}>
        <DisplayWeather />
      </View>
    );
  }
}
```
Running the code now will cause Expo to refresh your and the phone will ask you for permission to use your location. Tapping Allow will show the following in the console a moment later:

```JSON
Object {
  "coords": Object {
    "accuracy": 65,
    "altitude": 34.92243192580078,
    "altitudeAccuracy": 10,
    "heading": -1,
    "latitude": 37.75495136832096,
    "longitude": -122.49818570206919,
    "speed": -1,
  },
  "timestamp": 1552707836378.427,
}
```

The object returned has two properties: `coords` and `timestamp`. In `coords` is `latitude` and `longitude`. 

## State 

Your component needs to know when it has geolocation and when it doesn't. It won't have the data when loads, and it may never get the data if it isn't allowed access to the phone's location or if the data isn't available for some other reason. 

You can use `state` to keep track of this. State is a feature of Class-based components. State is special, setting state will cause a component to render. This means that changing state will allow your component to redraw itself. 

Define some state in the constructor. Add the following to the App Class. 

```JavaScript 
...
constructor(props) {
  super(props)

  this.state = {
    location: null, 
    weather: null
  }
}
...
```

Here the state is `location`, and the value is `null`, `weather` will hold the weather data when it is loaded its default value is `null`, no weather data.  

Set the value of the location state in your componentDidMount. 

```JavaScript 
componentDidMount() {
  navigator.geolocation.getCurrentPosition((location) => {
    this.setState({ location })
  }, (err) => {
    console.log(err.message)
  })
}
```

In components state is special. You'll always set it by calling `this.setState()`. 

## Loading the Weather data 

You will get the weather data from openweathermap.org. Go there now and make a user account. 

Go to your profile and get your developer API key. 

Add a new method to the App Class. 

```JavaScript
loadWeather() {
  const apikey = 'your_api_key'
  const { latitude, longitude } = this.state.location.coords
  const units = 'Imperial'
  const url = `https://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&appid=${apikey}&units=${units}`
  fetch(url)
  .then(res => res.json())
  .then(json => this.setState({ weather: json }))
  .catch(err => console.log(err.message))
}
```

Replace 'your_api_key' with your API Key from OpenWeatherMap. 

Call this method when you resolve the location in componentDidMount. 

```JavaScript 
componentDidMount() {
  navigator.geolocation.getCurrentPosition((location) => {
    this.setState({ location })
    this.loadWeather()
  }, (err) => {
    console.log(err.message)
  })
}
```

React Native uses native systems to get geolocation and to make network requests. These have all been mapped to JavaScript API that works just like it does in the browser. 

Notice here that fetch() is used to load data. After a connection is made the data is streamed as JSON. When that resolves we use this.setState() to assign the weather data to state which will also re-render the component. 

`.then(json => this.setState({ weather: json }))`

## Passing props

You'll want to pass the weather data from App to DisplayWeather. Components all have a special property named props that are used for passing information from a parent component to a child component. 

use props to pass the weather data from App to DisplayWeather. 

```JavaScript
render() {
  return (
    <View style={styles.container}>
      <DisplayWeather data={this.state.weather} />
    </View>
  );
}
```

## Using Props

Props are used to passed data from a parent to a child component. Children get values from keys on the props object. 

In DisplayWeather make a few changes. You'll want this component to display a message when the weather data is loading. Then display an error message if there was a problem, and otherwise display the weather data. 

Add these two if statements above return in the DisplayWeather Component. 

```JavaScript
const DisplayWeather = (props) => {
  if (props.data === null) {
    return <Text>Loading...</Text>
  }

  if (props.data.cod !== 200) {
    return <Text>An Error has occurred</Text>
  }

  const { temp } = props.data.main
  const { description } = props.data.weather[0]
 
  return (
    <View style={styles.container}>
      <Text style={styles.temp}>{temp}˚</Text>
      <Text>{description}</Text>
    </View>
  )
}
```

In the App component you set your data on the data prop. In DisplayWeather you get this as props.data. 

The first if statement returns a Text component if `props.data` is null. This shows the text "loading...". 

The second if statement looks at the cod property on data. If an error occurred the value here will not be 200. In this case, return a Text component with an error message. 

If these two if statements are bypassed then display the weather data. First, collect the temp and description to be displayed in the JSX block that is returned. 

## Looking at the OpenWeatherMap Data

The weather data from OpenWeatherMap is a JSON object. It has a structure. To get information like the temperature and description you'll need to navigate the structure. 

```JSON
Object {
  "base": "stations",
  "clouds": Object {
    "all": 1,
  },
  "cod": 200,
  "coord": Object {
    "lat": 37.75,
    "lon": -122.5,
  },
  "dt": 1552710644,
  "id": 5391997,
  "main": Object {
    "humidity": 50,
    "pressure": 1021,
    "temp": 54.36,
    "temp_max": 59,
    "temp_min": 50,
  },
  "name": "San Francisco County",
  "sys": Object {
    "country": "US",
    "id": 4322,
    "message": 0.0097,
    "sunrise": 1552745967,
    "sunset": 1552789093,
    "type": 1,
  },
  "visibility": 16093,
  "weather": Array [
    Object {
      "description": "clear sky",
      "icon": "01n",
      "id": 800,
      "main": "Clear",
    },
  ],
  "wind": Object {
    "deg": 360,
    "speed": 5.82,
  },
}
```

In the render() method you used: 

```JavaScript
const { temp } = props.data.main
const { description } = props.data.weather[0]
```

Find main.temp, this gives us 54.36 which is the temperature in F. 

Next find `weather[0].description`. Weather is an array which is why we need to get the first element with `[0]`. 

## Challenges

Challenge: Display some more of the weather info in the DisplayWeather component. Try these: 

- humidity
- pressure
- name

To do this you will need to get the value by navigating the Weather JSON. Then you'll need to add a  `<text>` component to display the value. 

Last you'll want to style the new elements. Add a new property to the `styles` object for the element that will use the style. Think of this like a class name you might assign to an HTML element. 

Next, assign an object with style properties under this property. Here are some properties you can use: 

- `fontSize`
- `fontWeight`
- `color`

Assign these properties values that work with React Native. React Native does not use the full selection of CSS values and generally doesn't use units. 

For example `fontSize` can be set to `24` and that's the equivalent of `font-size: 24px` in CSS terms. 

Some properties take keyword values these are always a string and React Native usually implements a subset of values supported by CSS. For example `fontWeight: 'bold'` is the same as `font-weight: bold` in CSS. 

Check the style properties by looking at the component reference. This will list all of the CSS properties supported by that component. Here is a link to the [Text Component](https://facebook.github.io/react-native/docs/text). 







