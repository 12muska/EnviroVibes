# EnviroVibes
Project Details:
1. HTML (index.html):
The HTML file contains the basic structure of the webpage.
It includes a title, a container for the main content, an input field for the city, a button to fetch weather data, and a div to display the weather information.
2. CSS (styles/style.css):
The CSS file provides basic styling for the webpage.
It sets the background color and allows for customization.
3. JavaScript (scripts/script.js):
The JavaScript file contains the logic for fetching weather data from the OpenWeatherMap API and updating the UI.
Code Explanation:
index.html:
html
Copy code
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <link rel="stylesheet" href="styles/style.css">
    <title>Weather App</title>
</head>
<body>

    <!-- Main Content -->
    <div class="container text-center mt-5">
        <h1>Weather App</h1>
        <input type="text" id="cityInput" placeholder="Enter city">
        <button class="btn btn-primary" onclick="getWeather()">Get Weather</button>

        <div id="weatherInfo" class="mt-4"></div>
    </div>

    <!-- Scripts -->
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
    <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.0.9/dist/umd/popper.min.js"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
    <script src="scripts/script.js"></script>
</body>
</html>
The HTML file includes Bootstrap for styling and responsiveness.
It has a title, a container with a heading, an input field for the city, a button to trigger weather data fetch, and a div to display the weather information.
The Bootstrap classes are used for styling.
style.css:
css
Copy code
body {
    background-color: #f8f9fa;
}

/* Add your custom styles here */
The CSS file sets the background color of the body to a light gray.
script.js:
javascript
Copy code
function getWeather() {
    const cityInput = document.getElementById('cityInput');
    const weatherInfo = document.getElementById('weatherInfo');

    // You can replace this with your preferred weather API
    const apiKey = 'YOUR_API_KEY';
    const apiUrl = `https://api.openweathermap.org/data/2.5/weather?q=${cityInput.value}&appid=${apiKey}&units=metric`;

    // Fetch weather data
    fetch(apiUrl)
        .then(response => response.json())
        .then(data => {
            const temperature = data.main.temp;
            const description = data.weather[0].description;

            weatherInfo.innerHTML = `
                <p>Temperature: ${temperature} &#8451;</p>
                <p>Description: ${description}</p>
            `;
        })
        .catch(error => {
            console.error('Error fetching weather data:', error);
            weatherInfo.innerHTML = 'Error fetching weather data. Please try again.';
        });
}
The JavaScript file defines a function getWeather that is called when the "Get Weather" button is clicked.
It retrieves the city input and constructs the API URL with the OpenWeatherMap API key.
The fetch function is used to get weather data in JSON format.
The data is then used to update the HTML content with temperature and weather description.
In case of an error, an error message is displayed.
