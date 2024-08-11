# Weather App 🌤️

A dynamic web application that fetches weather data from a weather API based on the user's location or a user-inputted location. It displays current weather conditions, temperature, and other relevant information, along with hourly and weekly forecasts.

## Features

- **Real-time Weather Updates:** Automatically fetches weather data based on the user's public IP address or a user-inputted location.
- **Temperature Units:** Allows users to toggle between Celsius and Fahrenheit.
- **Detailed Weather Information:** Displays current temperature, weather conditions, UV index, wind speed, humidity, visibility, air quality, and more.
- **Forecast:** Provides both hourly and weekly forecasts.
- **Dynamic Backgrounds and Icons:** Changes background images and icons based on the current weather conditions.

## Technologies Used

- **Frontend:** HTML, CSS, JavaScript
- **API:** [Visual Crossing Weather API](https://www.visualcrossing.com/)

## Usage

- Upon opening the app, it will automatically detect your location and display the current weather information.
- Use the search bar to input a location and get weather details for that area.
- Toggle between Celsius and Fahrenheit using the buttons provided.
- Switch between hourly and weekly forecasts using the respective buttons.

## Code Overview

### HTML

The HTML structure consists of a sidebar for the search input and weather details, and a main section for forecast information.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Weather App</title>
    <script src="https://kit.fontawesome.com/64d58efce2.js" crossorigin="anonymous"></script>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <!-- partial:index.partial.html -->
    <div class="wrapper">
        <div class="sidebar">
            <!-- Sidebar content -->
        </div>
        <div class="main">
            <!-- Main content -->
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

### CSS

The CSS file (`style.css`) handles the styling for the app, including layout, colors, fonts, and responsive design.

### JavaScript

The JavaScript file (`script.js`) contains functions to:

- Fetch the user's public IP address to determine their location.
- Fetch weather data from the Visual Crossing Weather API.
- Update the UI with current weather conditions and forecasts.
- Handle user interactions, such as location search and unit toggling.

```javascript
const temp = document.getElementById("temp"),
    date = document.getElementById("date-time"),
    // other DOM elements...

let currentCity = "";
let currentUnit = "c";
let hourlyorWeek = "week";

// Function to get date and time
function getDateTime() {
    // implementation...
}

// Fetch public IP and weather data
function getPublicIp() {
    fetch("https://geolocation-db.com/json/", { method: "GET", headers: {} })
        .then((response) => response.json())
        .then((data) => {
            currentCity = data.city;
            getWeatherData(data.city, currentUnit, hourlyorWeek);
        })
        .catch((err) => console.error(err));
}

getPublicIp();

// Fetch weather data
function getWeatherData(city, unit, hourlyorWeek) {
    // implementation...
}

// Update UI with weather data
function updateForecast(data, unit, type) {
    // implementation...
}

// Event listeners for user interactions
searchForm.addEventListener("submit", (e) => {
    e.preventDefault();
    let location = search.value;
    if (location) {
        currentCity = location;
        getWeatherData(location, currentUnit, hourlyorWeek);
    }
});

// Other utility functions...

```
