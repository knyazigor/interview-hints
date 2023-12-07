## Basic usage of XHR (XMLHttpRequest):

To make a simple request using XHR, you can follow these steps:

1. Create a new instance of the `XMLHttpRequest` object:
   ```javascript
   var xhr = new XMLHttpRequest();
   ```

2. Open a connection by specifying the HTTP method (e.g., GET, POST) and the URL of the server endpoint:
   ```javascript
   xhr.open('GET', 'https://api.example.com/data', true);
   ```

3. Set any request headers if needed:
   ```javascript
   xhr.setRequestHeader('Content-Type', 'application/json');
   ```

4. Define a callback function to handle the response:
   ```javascript
   xhr.onload = function() {
     if (xhr.status === 200) {
       // Successful response
       var response = JSON.parse(xhr.responseText);
       // Handle the response data here
     } else {
       // Error handling
       console.log('Request failed. Status:', xhr.status);
     }
   };

5. Send the request:
   ```javascript
   xhr.send();
   ```

This is a basic example of making a GET request using XHR. You can modify the code according to your specific requirements.

## Basic usage of fetch():

The `fetch()` function is a modern alternative to XHR for making HTTP requests in JavaScript. Here's a basic example of how to use `fetch()` to make a simple request and handle the response:

```javascript
fetch('https://api.example.com/data')
  .then(function(response) {
    if (response.ok) {
      // Successful response
      return response.json();
    } else {
      // Error handling
      throw new Error('Request failed. Status:', response.status);
    }
  })
  .then(function(data) {
    // Handle the response data here
    console.log(data);
  })
  .catch(function(error) {
    // Error handling
    console.log(error);
  });
```

In this example, `fetch()` returns a Promise that resolves to the response object. We can use the `ok` property of the response object to check if the request was successful. If it was, we can parse the response using `.json()` method. If there was an error, we can throw an error and handle it in the `catch` block.

Note that `fetch()` also supports additional options for customizing the request, such as setting headers, specifying the request method, and sending data.

```javascript
async function postData(url = "", data = {}) {
  // Default options are marked with *
  const response = await fetch(url, {
    method: "POST", // *GET, POST, PUT, DELETE, etc.
    mode: "cors", // no-cors, *cors, same-origin
    cache: "no-cache", // *default, no-cache, reload, force-cache, only-if-cached
    credentials: "same-origin", // include, *same-origin, omit
    headers: {
      "Content-Type": "application/json",
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
    redirect: "follow", // manual, *follow, error
    referrerPolicy: "no-referrer", // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
    body: JSON.stringify(data), // body data type must match "Content-Type" header
  });
  return response.json(); // parses JSON response into native JavaScript objects
}

postData("https://example.com/answer", { answer: 42 }).then((data) => {
  console.log(data); // JSON data parsed by `data.json()` call
});
```