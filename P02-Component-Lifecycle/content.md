---
title: "Component Lifecycle"
slug: component-lifecycle
---

Components have a lifecycle that can be used to track when they are created and when they are removed. We would like the App Component to get the geolocation when the component is created.

To get the weather data, we need to know the location of the phone. We can get this:

`navigator.geolocation.getCurrentPosition(success, error, options)`

The component needs to know if the location data is available or not. Getting location data is an asynchronous operation. You'll need to make a request and wait for a response.

# Component Lifecycle methods

The `componentDidMount()` method is called when the component is created and added to a view. The code in this method will run at that time. The code here requests the current position. If the request is successful it prints the data to the console if not it prints an error.

> [action]
>
> To get geolocation, add the `componentDidMount()` method to `App.js`:
>
```JavaScript
export default class App extends React.Component {
>
  componentDidMount() {
    navigator.geolocation.getCurrentPosition((location) => {
      console.log(location)
    }, (err) => {
      console.log(err.message)
    })
  }
>
  render() {
    return (
      <View style={styles.container}>
        <DisplayWeather />
      </View>
    );
  }
}
>
...
```

Running the code now will cause Expo to refresh your and the phone will ask you for permission to use your location. Tapping Allow will show the following in the console where you ran `npm start` a moment later:

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

**NOTE:** You may need to restart the expo app and re-scan the QR code to see the above output.

# State

Your component needs to know when it has geolocation and when it doesn't. It won't have the data when loads, and it may never get the data if it isn't allowed access to the phone's location or if the data isn't available for some other reason.

You can use `state` to keep track of this. `state` is a feature of Class-based components, and setting `state` will cause a component to render. This means that changing `state` will allow your component to redraw itself!

> [action]
>
> Define some state by adding a constructor to `App.js` within the class definition:
>
```JavaScript
export default class App extends React.Component {
>
...
>
constructor(props) {
  super(props)
>
  // These will hold the user's location and the weather data when it is loaded
  this.state = {
    location: null,
    weather: null
  }
}
>
...
>
}
```

Next, we need to set the value of the location state in `componentDidMount`:

> [action]
>
> Update `componentDidMount` in `App.js` to the following:
>
```JavaScript
componentDidMount() {
  navigator.geolocation.getCurrentPosition((location) => {
    // Now we're setting the state instead of just logging to console
    // You'll always set state by calling `this.setState()`.
    this.setState({ location })
  }, (err) => {
    console.log(err.message)
  })
}
```

# Loading the Weather data

Let's get some weather data to load. We'll get ours from [openweathermap.org](openweathermap.org).

> [action]
>
> Go to [openweathermap.org](openweathermap.org) now and make a user account.
>
> Once you've signed in, select **API Keys** from the nav bar, and **copy your developer API key.**


React Native uses native systems to get geolocation and to make network requests. These have all been mapped to a JavaScript API that works just like it does in the browser. With that in mind, let's add a new method to the App Class that will load in our weather data:

> [action]
>
> Create the `loadWeather` method in the App Class of `App.js`, replacing `your_api_key` with your actual API key:
>
```JavaScript
loadWeather() {
  const apikey = 'your_api_key'
  const { latitude, longitude } = this.state.location.coords
  const units = 'Imperial'
  const url = `https://api.openweathermap.org/data/2.5/weather?lat=${latitude}&lon=${longitude}&appid=${apikey}&units=${units}`
  // `fetch()` is used to load data
  fetch(url)
  // After a connection is made the data is streamed as JSON
  .then(res => res.json())
  // When that resolves we use `this.setState()` to assign the weather data to state which will also re-render the component.
  .then(json => this.setState({ weather: json }))
  .catch(err => console.log(err.message))
}
```

Call this method when you resolve the location in `componentDidMount`.

> [action]
>
> Update `componentDidMount` to call `loadWeather`:
>
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

We shouldn't see anything change in the app quite yet. We still have some work to do in terms of passing the data from `App` to `DisplayWeather`, which we'll get to in the next chapter.

# Now Commit

>[action]
>
```bash
$ git add .
$ git commit -m 'implemented state and component lifecycle'
$ git push
```
