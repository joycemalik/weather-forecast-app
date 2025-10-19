# Minimalist Pincode Weather Forecast App

A simple, single-file web application that fetches and displays the current weather and a 5-day forecast for a given US pincode, featuring a clean user interface and subtle visual feedback.

## How to Use

To get this application up and running:

1.  **Obtain an OpenWeatherMap API Key:**
    *   Go to [OpenWeatherMap](https://openweathermap.org/api).
    *   Sign up for a free account.
    *   Navigate to your API keys section and copy your personal API key.

2.  **Open `index.html`:**
    *   Save the provided `index.html` content as `index.html` on your local machine.
    *   Open this file in any modern web browser (e.g., Chrome, Firefox, Edge, Safari).

3.  **Configure API Key:**
    *   Edit the `index.html` file.
    *   Locate the JavaScript section (`<script>...</script>`).
    *   Find the line `const API_KEY = 'YOUR_OPENWEATHERMAP_API_KEY';`
    *   Replace `'YOUR_OPENWEATHERMAP_API_KEY'` with the actual API key you obtained from OpenWeatherMap.

4.  **Enter Pincode and Get Weather:**
    *   In the web page, enter a US pincode (e.g., `90210`, `10001`, `60601`) into the input field.
    *   Click the "Get Weather" button or press `Enter`.
    *   The application will display the current weather and a 5-day forecast for that location.

## Code Explanation

This project is a self-contained web application within a single `index.html` file, leveraging pure HTML, CSS, and vanilla JavaScript.

### HTML Structure

The HTML provides a straightforward layout:
*   A main container (`.container`) wraps all elements.
*   An input field and a button (`.input-section`) for user interaction.
*   Placeholder paragraphs for loading messages (`#loadingMessage`) and error alerts (`#errorMessage`).
*   A hidden `div` (`#weatherDisplay`) that becomes visible to show the weather data, containing:
    *   A section for current weather (`.current-weather`), displaying city, temperature, description, icon, and detailed stats (min/max temp, humidity, wind).
    *   A section for the 5-day forecast (`.forecast-section`), which includes a grid (`#forecastGrid`) where individual forecast cards are dynamically injected.

### CSS Styling

All CSS is embedded within a `<style>` tag in the HTML `<head>`.
*   It uses CSS variables (`:root`) for easy theme customization (background colors, text colors, etc.).
*   Flexbox and CSS Grid are utilized for responsive layout, ensuring a pleasant experience across different screen sizes.
*   Styling is applied to create distinct cards for current weather and forecast items, with subtle hover effects (`transform`, `box-shadow`) for an interactive feel.
*   A simple `keyframes` animation (`@keyframes pulse`) is applied to the current temperature to give a gentle visual "pulse", contributing to the "amazing animations" aspect in a minimalist way.
*   Basic media queries are included for responsiveness on smaller devices.

### JavaScript Logic

The JavaScript code is embedded within a `<script>` tag at the end of the `<body>` for optimal loading performance.
*   **API Integration:** It interacts with the OpenWeatherMap API:
    *   `api.openweathermap.org/geo/1.0/zip`: To convert a given pincode (assuming US) into geographical coordinates (latitude and longitude) and retrieve the city name.
    *   `api.openweathermap.org/data/2.5/weather`: To fetch current weather conditions using the obtained coordinates.
    *   `api.openweathermap.org/data/2.5/forecast`: To retrieve a 5-day/3-hour forecast for the location.
*   **DOM Manipulation:** It dynamically updates the HTML elements based on the fetched data.
*   **Error Handling & Loading States:**
    *   Includes checks for empty pincode input and an unconfigured API key.
    *   Displays loading messages (`#loadingMessage`) during API calls and appropriate error messages (`#errorMessage`) if data fetching fails.
*   **Weather Icons:** The `getWeatherIcon` function maps OpenWeatherMap's standard icon codes to visually intuitive Unicode emoji characters (e.g., `☀️`, `☁️`, `🌧️`), maintaining a minimalist approach without requiring external image assets.
*   **Forecast Processing:** The `renderForecast` function processes the 3-hour interval forecast data to select a single, representative entry (e.g., closest to noon) for each of the next five days, providing a cleaner daily forecast view.
*   **Event Listeners:** An event listener is attached to the "Get Weather" button for clicks and to the pincode input field for the `Enter` keypress, triggering the `fetchWeather` function.

## License

This project is licensed under the MIT License. You are free to use, modify, and distribute this code for personal or commercial purposes, provided the original license notice is included.