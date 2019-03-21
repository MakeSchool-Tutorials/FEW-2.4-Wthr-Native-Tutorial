---
title: "React and React Native Basic concepts "
slug: react-and-react-native-basic-concepts
---

Let's go over some building blocks of React and React Native that we will use to create our Wthr app.

# Components
React projects are written in JavaScript. The basic building block in React is the Component. **Components** are usually things you can see on the screen and may also have some business logic code that manages their behavior.

Components can be written as a function or as a class that extends `React.Component`.

Look at `App.js` in your project. This file in the entry point. It's also the top level component. Think of components like a tree: one component can branches/child components and these can have their own children. `App.js` is like the root of the tree.

> [action]
>
> Review `App.js` below and make sure you understand what's going on:
>
```JavaScript
// This imports React from the 'react' package
import React from 'react';
// This imports two native Components: `Text`, and `View` from the 'react-native' package.
// `StyleSheet` is a helper Object for creating styles sheets in React Native.  
import { StyleSheet, Text, View } from 'react-native';
>
// The next block of code is the definition of a component. This component is named App, and it extends `React.Component`.
// Components that extend `React.Component` must implement a render function. The `render()` method must return JSX.
export default class App extends React.Component {
  render() {
    // JSX is an extension of the JavaScript language. It allows you to write code that looks like HTML/XML within your JavaScript.
    return (
      // This is a View component with a child Text component. These are displayed on the screen in the default app. Remember these were imported above.
      <View style={styles.container}>
        <Text>Open up App.js to start working on your app!</Text>
      </View>
    );
  }
}
>
// This defines an object that will be used to style the components here in the app component.
const styles = StyleSheet.create({
  // These properties of `container` are standard CSS properties, and the values are the same values you would have used in CSS.
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

# Native Components

React Native uses native components. So far we've seen the `View` and `Text` Components, let's cover those in a bit more detail:

## Text

Makes text

`<Text>Some text that is displayed...</Text>`

## View

A view is a rectangular area on the screen that can display child elements.

```
<View>
  ...Child Components...
</View>
```

## Styling Components

React native supports a subset of CSS style properties and units.

Typically you'll set all styles "inline" on each element and define them as a JS Object.

`<View style={{backgroundColor:'#f00'}}></View>`

# Define Your Own Component

Let's define a component that displays the Weather Data:

> [action]
>
> Create a new file named `DisplayWeather.js`. Make a folder in your project named: `Components` save this file there.
>
> Add the following to `DisplayWeather.js`:
>
```JS
import React from 'react'
import { Text, View, StyleSheet } from 'react-native'
>
const DisplayWeather = (props) => {
  return (
      <View>
        <Text>72˚</Text>
      </View>
  )
}
>
export default DisplayWeather
```

This defines a simple component. _This component is defined as a function._ Component function based component must return JSX and should take a single parameter named props. The View component will act as a container for the Text, and the Text will display the temperature.

For now, we will assume the temperature is 72˚. In the future, you will get the weather data from an online service and display the actual temperature here.

Lastly, let's add a style sheet. Do this by defining a variable named `styles` and assigning it an Object with CSS properties that can be applied to Components.

> [action]
>
> Add a StyleSheet to `/Components/DisplayWeather.js`:
>
```JS
import React from 'react'
import { Text, View, StyleSheet } from 'react-native'
>
const DisplayWeather = (props) => {
  return (
    <View style={styles.container}>
      <Text style={styles.temp}>72˚</Text>
    </View>
  )
}
>
export default DisplayWeather
>
// These objects are assigned to the `style` prop on each of the two components.
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

# Test your Component

Now that we have a component, let's import and display it in the app:

> [action]
>
> Add the following at the top of `App.js`.
>
```js
import DisplayWeather from './Components/DisplayWeather'
```

Notice, when importing your own files you'll need to include a path. Since the file is in the same folder the path begins: './'

> [action]
>
> Replce the current component in the `render()` method of `App.js` with your component:
>
```JS
<View style={styles.container}>
  <DisplayWeather />
</View>
```

Notice that you don't need to use a closing tag for `DisplayWeather` since it doesn't have any children. You do need to use /> to 'self-close' this tag.

Try loading the app on your phone, you should see it say 72˚ in the center of the screen.

# Now Commit

>[action]
>
```bash
$ git add .
$ git commit -m 'added displayweather component'
$ git push
```


# Stretch Challenge:

> [challenge]
>
> Add another Text component to display a description of the weather. Edit the Display Weather component. Add another Text component below the Temp. Use some text that describes the weather, something like:
>
> Partly Cloudy
>
> Save and test your work. Your app should refresh its view in Expo.
