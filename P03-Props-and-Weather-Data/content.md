---
title: "Props and Weather Data"
slug: props-and-weather-data
---

Before our app will actually display the weather data, we need to pass the weather data from App to DisplayWeather. Components all have a special property named **props** that are used for passing information from a parent component to a child component.

# Passing Props

> [action]
>
> Use props to pass the weather data from App to DisplayWeather in `App.js`:
>
```JavaScript
render() {
  return (
    <View style={styles.container}>
[bold]      <DisplayWeather data={this.state.weather} />[/bold]
    </View>
  );
}
```

# Using Props

Props are used to passed data from a parent to a child component. Children get values from **keys** on the props object.

We want the `DisplayWeather` component to display a message when the weather data is loading. It also needs to display an error message if there was a problem, and otherwise display the weather data.

In the App component you set your data on the **data prop**. In `DisplayWeather` you get this as `props.data`, which we'll use to help us check the above conditions.

> [action]
>
> Add these two if statements above `return` in `/Components/DisplayWeather.js`:
>
```JavaScript
const DisplayWeather = (props) => {
  // No data yet, so it must still be loading
  if (props.data === null) {
    return <Text>Loading...</Text>
  }
>
  // Cod is where codes go, so if an error occurred, the value would not be 200 (could be 400, 404, etc.)
  if (props.data.cod !== 200) {
    return <Text>An Error has occurred</Text>
  }
>
  // If no error and not loading, load/display weather data, grabbing the appropriate data from props
  const { temp } = props.data.main
  const { description } = props.data.weather[0]
 >
  return (
    <View style={styles.container}>
      <Text style={styles.temp}>{temp}˚</Text>
      <Text>{description}</Text>
    </View>
  )
}
```

# Looking at the OpenWeatherMap Data

The weather data from OpenWeatherMap is a JSON object. It has a structure. To get information like the temperature and description you'll need to navigate the structure:

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

In the `render()` method in `DisplayWeather`, we used:

```JavaScript
const { temp } = props.data.main
const { description } = props.data.weather[0]
```

> [action]
>
> Find `main.temp` in the JSON snippet above

This gives us 54.36 which is the temperature in F.

> [action]
>
> Next find `weather[0].description` in the JSON snippet above.

Weather is an array which is why we need to get the first element with `[0]`.

Great work on **using Props and State to configure and manage components in this chapter!**

# Product So Far

Save and reload the app, you should now be getting the temperature of where you're at with a short description of the weather.

**Congrats on building your first native react app!**

> [action]
>
> As you go through FEW 2.4, reflect back to this tutorial and check that the material you're learning is builds upon what you learned here.

# Feedback and Review - 2 minutes

**We promise this won't take longer than 2 minutes!**

Please take a moment to rate your understanding of learning outcomes from this tutorial, and how we can improve it via our [tutorial feedback form](LINK_TO_YOUR_FORM)

This allows us to get feedback on how well the students are grasping the learning outcomes, and tells us where we can improve the tutorial experience.

# Stretch Challenges

> [challenge]
>
> Display some more of the weather info in the DisplayWeather component. Try these:
>
> - humidity
> - pressure
> - name
>
> To do this you will need to get the value by navigating the Weather JSON. Then you'll need to add a  `<text>` component to display the value.
>
> Last you'll want to style the new elements. Add a new property to the `styles` object for the element that will use the style. Think of this like a class name you might assign to an HTML element.
>
> Next, assign an object with style properties under this property. Here are some properties you can use:
>
> - `fontSize`
> - `fontWeight`
> - `color`
>
> Assign these properties values that work with React Native. React Native does not use the full selection of CSS values and generally doesn't use units.
>
> For example `fontSize` can be set to `24` and that's the equivalent of `font-size: 24px` in CSS terms.
>
> Some properties take keyword values these are always a string and React Native usually implements a subset of values supported by CSS. For example `fontWeight: 'bold'` is the same as `font-weight: bold` in CSS.
>
> Check the style properties by looking at the component reference. This will list all of the CSS properties supported by that component. Here is a link to the [Text Component](https://facebook.github.io/react-native/docs/text).
