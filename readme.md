# Chuck Norris Jokes

This project is a simple web application that fetches and displays random Chuck Norris jokes using the [Chuck Norris API](https://api.chucknorris.io/). The application updates the joke displayed on the webpage each time a button is clicked.

## Features

- Fetches a random Chuck Norris joke from the API.
- Displays the joke on the webpage.
- Updates the joke when the "Get Another Joke" button is clicked.
- Automatically displays a joke when the page is loaded.

## How It Works

The application uses an XMLHttpRequest to fetch jokes from the Chuck Norris API. When the user clicks the button, a new joke is fetched and displayed. If the API request fails, an error message is shown instead.

## Code Overview

Here is a brief overview of the key parts of the code:

### HTML Elements

- `jokeEl`: The DOM element where the joke is displayed.
- `jokeBtn`: The button that triggers the fetching of a new joke.

### JavaScript Functions

- `generateJoke`: This function handles the API request to fetch a new joke. It uses an XMLHttpRequest to make a `GET` request to the Chuck Norris API. When the request is successful, it updates `jokeEl` with the new joke. If the request fails, it displays an error message.

### Event Listeners

- `jokeBtn.addEventListener('click', generateJoke)`: This sets up an event listener on the button, so that a new joke is fetched each time the button is clicked.
- `document.addEventListener('DOMContentLoaded', generateJoke)`: This ensures a joke is fetched and displayed as soon as the page is loaded.

## Usage

To use this project, follow these steps:

1. Clone the repository to your local machine.
2. Open the `index.html` file in your browser.

You should see a Chuck Norris joke displayed on the page, and you can click the "Get Another Joke" button to fetch and display a new joke.

## Example

Here is an example of how the application looks and works:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Chuck Norris Jokes</title>
  </head>
  <body>
    <h1>Chuck Norris Jokes</h1>
    <p id="joke">Loading...</p>
    <button id="joke-btn">Get Another Joke</button>

    <script>
      const jokeEl = document.getElementById("joke");
      const jokeBtn = document.getElementById("joke-btn");

      const generateJoke = () => {
        const xhr = new XMLHttpRequest();

        xhr.open("GET", "https://api.chucknorris.io/jokes/random");

        xhr.onreadystatechange = function () {
          if (this.readyState === 4) {
            if (this.status === 200) {
              jokeEl.innerHTML = JSON.parse(this.responseText).value;
            } else {
              jokeEl.innerHTML = "Something Went Wrong (Not Funny)";
            }
          }
        };

        xhr.send();
      };

      jokeBtn.addEventListener("click", generateJoke);
      document.addEventListener("DOMContentLoaded", generateJoke);
    </script>
  </body>
</html>
```
