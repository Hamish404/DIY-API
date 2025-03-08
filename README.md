# Joke API

This is a simple REST API built with Express.js that provides access to a collection of jokes. It allows you to retrieve random jokes, specific jokes, filter jokes by type, and perform CRUD operations (Create, Read, Update, Delete) on the joke data.

**Note:** This is a learning exercise. Storing the `MASTER_KEY` directly in the code is a security risk and should not be done in production environments.

## Features

* **Get a random joke:** Retrieves a random joke from the collection.
* **Get a specific joke:** Retrieves a joke by its ID.
* **Filter jokes by type:** Retrieves jokes based on their joke type (e.g., Puns, Science).
* **Create a new joke:** Adds a new joke to the collection.
* **Update a joke:** Updates an existing joke.
* **Patch a joke:** Partially updates an existing joke.
* **Delete all jokes (Admin only):** Deletes all jokes in the collection. Requires admin authentication.
* **Delete a specific joke:** Deletes a joke by its ID.
* **Basic Admin Authentication:** Uses a header key to authenticate admin requests.

## Getting Started

### Prerequisites

* Node.js and npm installed.

### Installation

1.  Clone the repository:

    ```bash
    git clone https://github.com/Hamish404/DIY-API
    cd DIY-API
    ```

2.  Install dependencies:

    ```bash
    npm install
    ```

3.  Start the server:

    ```bash
    npm start
    ```

    The server will start on port 3000.

## API Endpoints

### 1. Get a Random Joke

* **Endpoint:** `/random`
* **Method:** `GET`
* **Response:** JSON object containing a random joke.

    ```json
    {
      "id": 1,
      "jokeText": "Why don't scientists trust atoms? Because they make up everything.",
      "jokeType": "Science"
    }
    ```

### 2. Get a Specific Joke

* **Endpoint:** `/jokes/:jokeId`
* **Method:** `GET`
* **Parameters:**
    * `jokeId`: The ID of the joke.
* **Response:** JSON object containing the specified joke.

    ```json
    {
      "id": 1,
      "jokeText": "Why don't scientists trust atoms? Because they make up everything.",
      "jokeType": "Science"
    }
    ```

### 3. Filter Jokes by Type

* **Endpoint:** `/filter?type=[jokeType]`
* **Method:** `GET`
* **Query Parameters:**
    * `type`: The type of joke to filter (e.g., Puns, Science, Wordplay, Math, Sports, Movies, Food).
* **Response:** JSON array containing jokes of the specified type.

    ```json
    [
      {
        "id": 1,
        "jokeText": "Why don't scientists trust atoms? Because they make up everything.",
        "jokeType": "Science"
      },
      {
        "id": 6,
        "jokeText": "How do you organize a space party? You planet!",
        "jokeType": "Science"
      }
    ]
    ```

### 4. Create a New Joke

* **Endpoint:** `/jokes`
* **Method:** `POST`
* **Body (JSON):**

    ```json
    {
      "text": "New joke text",
      "type": "Joke Type"
    }
    ```

* **Response:** JSON object of the newly created joke.

### 5. Update a Joke

* **Endpoint:** `/jokes/:jokeId`
* **Method:** `PUT`
* **Parameters:**
    * `jokeId`: The ID of the joke to update.
* **Body (JSON):**

    ```json
    {
      "text": "Updated joke text",
      "type": "Updated Joke Type"
    }
    ```

* **Response:** JSON object of the updated joke.

### 6. Patch a Joke

* **Endpoint:** `/jokes/:id`
* **Method:** `PATCH`
* **Parameters:**
    * `id`: The ID of the joke to patch.
* **Body (JSON):**

    ```json
    {
      "text": "Partially updated joke text",
      "type": "Partially Updated Joke Type"
    }
    ```

* **Response:** JSON object of the patched joke.

### 7. Delete All Jokes (Admin Only)

* **Endpoint:** `/jokes/all`
* **Method:** `DELETE`
* **Headers:**
    * `x-admin-key`: Your master key.
* **Response:** `All jokes deleted`

### 8. Delete a Specific Joke

* **Endpoint:** `/jokes/:id`
* **Method:** `DELETE`
* **Parameters:**
    * `id`: The ID of the joke to delete.
* **Response:** `Joke deleted` or `Joke not found`.

## Authentication

* Admin routes require an `x-admin-key` header with the correct master key.

## Data

* The jokes are stored in an in-memory array. This will be lost when the server restarts.
