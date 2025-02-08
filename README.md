Description
This is a simple digital clock implementation in JavaScript that displays the current time in a 12-hour format (with AM/PM) on a webpage. The time updates every second.

The clock will:

Display the time in the format HH:MM:SS AM/PM.
Convert the time to a 12-hour format (e.g., 12:30:45 PM instead of 12:30:45).
Automatically update the time every second.
Features:
12-hour format: Converts the time from 24-hour format to 12-hour format (e.g., 13:00:00 becomes 01:00:00 PM).
AM/PM display: Adds the AM/PM indicator based on the time of day.
Live updates: The time updates every second (1-second interval).
Proper formatting: Ensures that hours, minutes, and seconds always appear as two digits (e.g., 05:03:09 PM).
Files
index.html: The HTML file contains the structure for displaying the clock.
style.css: The CSS file contains styling for the clock display.
script.js: The JavaScript file that controls the clock's functionality.
How it Works
JavaScript (script.js):
The updateClock function is responsible for fetching the current time using JavaScript's Date object.
It converts the 24-hour format to 12-hour format.
The AM/PM status is determined based on the time, and the clock is updated every second using setInterval.
The time is displayed in the HTML element with the ID clock.
CSS (style.css):
The CSS centers the clock on the webpage, sets up a background, and applies other styles to make the clock look clean and modern.
How to Use
Download or copy the following files:

index.html
style.css
script.js
Open the index.html file in a browser, and the digital clock will be displayed.

The clock will update every second, showing the current time in a 12-hour format with AM/PM.

Code Breakdown
JavaScript (script.js)
javascript
Copy
Edit
function updateClock() {
    const now = new Date();  // Get the current time
    let hours = now.getHours();  // Get hours (24-hour format)

    // Determine AM or PM
    const meridian = hours >= 12 ? "PM" : "AM";

    // Convert to 12-hour format
    hours = hours % 12 || 12;  // If 0 (midnight), set to 12
    hours = hours.toString().padStart(2, '0');  // Pad hours to 2 digits (e.g., 09)

    const minutes = now.getMinutes().toString().padStart(2, '0');  // Pad minutes
    const seconds = now.getSeconds().toString().padStart(2, '0');  // Pad seconds

    // Create the time string
    const timeString = `${hours}:${minutes}:${seconds} ${meridian}`;

    // Display the time in the HTML element with ID 'clock'
    document.getElementById("clock").textContent = timeString;
}

// Initialize the clock
updateClock();

// Update the clock every second
setInterval(updateClock, 1000);
Explanation:
updateClock: Fetches the current time and formats it into a 12-hour format with AM/PM.
setInterval: Calls updateClock every 1000 milliseconds (or 1 second) to update the time on the page.
CSS (style.css)
css
Copy
Edit
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Arial', sans-serif;
  background-color: #333;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.clock-container {
  background-color: #222;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 0 0 15px rgba(255, 255, 255, 0.3);
}

.clock {
  font-size: 5rem;
  color: #fff;
  font-weight: bold;
}
Explanation:
* { margin: 0; padding: 0; box-sizing: border-box; }: Resets margin and padding for all elements to ensure consistent styling.
body: Centers the clock vertically and horizontally.
.clock-container: Applies styling to the clock container, adding a background color, padding, rounded corners, and a shadow effect.
.clock: Styles the clock text, making it large, bold, and white.
License
This project is open source and can be freely used and modified.
