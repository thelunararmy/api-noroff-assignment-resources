# Shelf Help (Books) API

## Open Endpoints

Open endpoints do not require authentication.

### Books `GET /Books`

#### Sample Response

```json
[
  {
    "id": 1,
    "isbn": "1982137274",
    "title": "The 7 Habits of Highly Effective People",
    "author": "Stephen R Covey",
    "coverImg": "assets/images/1.jpg",
    "rating": 0,
    "blurb": "The 7 Habits have become famous and are integrated into everyday thinking by millions and millions of people. Why? Because they work! With Sean Covey’s added takeaways on how the habits can be used in our modern age, the wisdom of the 7 Habits will be refreshed for a new generation of leaders. This beloved classic presents a principle-centered approach for solving both personal and professional problems. With penetrating insights and practical anecdotes, Stephen R. Covey reveals a step-by-step pathway for living with fairness, integrity, honesty, and human dignity—principles that give us the security to adapt to change and the wisdom and power to take advantage of the opportunities that change creates."
  }
]
```

## Protected Endpoints

Protected endpoints require the X-API-Key header with the API key as value.

### 🔒 Book `POST /books`

Use the `POST` method to create a new Book in the API database.

#### Sample Code

```javascript
const apiURL = "your-api-url-goes-here";
const apiKey = "your-public-api-key-goes-here";

fetch(`${apiURL}/trainers`, {
  method: "POST",
  headers: {
    "X-API-Key": apiKey,
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    id: 6,
    isbn: "1982137274",
    title: "Some Title",
    author: "Some author",
    coverImg: "assets/images/1.jpg",
    rating: 0,
    blurb: "Some blurb",
  }),
})
  .then((response) => {
    if (!response.ok) {
      throw new Error("Could not create new Book");
    }
    return response.json();
  })
  .then((newBook) => {
    // newBook is the new book with an id
  })
  .catch((error) => {});
```

#### Sample response

```json
{
  "id": 6,
  "isbn": "1982137274",
  "title": "Some Title",
  "author": "Some author",
  "coverImg": "assets/images/1.jpg",
  "rating": 0,
  "blurb": "Some blurb"
}
```

### 🔒 Book `PATCH /books`

The `PATCH` method is used to update a single record

#### Sample Code

```javascript
const apiURL = "your-api-url-goes-here";
const apiKey = "your-public-api-key-goes-here";
const bookId = 1; // Update book with id 1

fetch(`${apiURL}/trainers/${userId}`, {
  method: "PATCH", // NB: Set method to PATCH
  headers: {
    "X-API-Key": apiKey,
    "Content-Type": "application/json",
  },
  body: JSON.stringify({
    // Provide new Pokémon to add trainer with id 1
    rate:4
  }),
})
  .then((response) => {
    if (!response.ok) {
      throw new Error("Could not update book");
    }
    return response.json();
  })
  .then((updatedBook) => {
    // updatedBook is the book with the Patched data
  })
  .catch((error) => {});
```
