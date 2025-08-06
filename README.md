# CineSeek Movie Discovery App

This project connects to the MoviesDatabase API to display popular and trending movies. Users can search for movies by year, genre, or keywords. The app is built using Next.js, TypeScript, and Tailwind CSS.

---

## API Overview

The MoviesDatabase API provides movie-related information such as titles, genres, release years, and more. It supports search filters like year and genre and returns detailed results including posters, plot summaries, and ratings. It also includes YouTube trailer URLs, awards, full biographies, and many other useful details. This makes it ideal for building modern movie discovery apps.

---

## API Version

**Current Version:** v2.62

---

## Available Endpoints

- `/titles`: Get movie titles and details. Supports filtering by genre, year, and more.
- `/titles/search/title`: Search for movies by name/title.
- `/titles/x/titles-by-ids`: Get multiple movies using their unique IDs, including seasons, episodes, upcoming titles, etc.
- `/genres`: Get a list of all movie genres.
- `/countries`: Get a list of available countries of origin.
- `/languages`: List of spoken languages in the movies.

---

## Request and Response Format

{
  "page": 1,
  "results": [
    {
      "id": "tt1234567",
      "titleText": { "text": "Example Movie" },
      "releaseYear": { "year": 2023 },
      "primaryImage": { "url": "https://example.com/poster.jpg" },
      "genres": [ { "text": "Comedy" } ],
      "plot": { "text": "A fun story..." },
      "awards": { "wins": 2, "nominations": 5 },
      "trailer": { "url": "https://youtube.com/..." }
    }
  ],
  "totalPages": 100,
  "totalResults": 1000
}


### Sample Request (GET `/titles`)

```http
GET https://moviesdatabase.p.rapidapi.com/titles
Headers:
  X-RapidAPI-Key: your_api_key
  X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
Query Params:
  year=2023
  genre=comedy
  page=1```

---

### Authentication

You must supply your RapidAPI credentials in the HTTP request headers:
- X-RapidAPI-Key: your_api_key
- X-RapidAPI-Host: moviesdatabase.p.rapidapi.com

### Error Handling

Common API Errors and Their Meaning:

- **401 Unauthorized**: API key is invalid or missing.
- **429 Too Many Requests**: You have exceeded your rate limit.
- **5xx Server Errors**: Something went wrong on the API server.

### How to Handle These Errors:

- Use `try/catch` blocks in your code to manage exceptions.
- Always check the response status codes.
- Display friendly error messages to users.
- Implement retry logic where appropriate, or ask users to try again later.

---

### Usage Limits and Best Practices

- The API enforces rate limits based on your RapidAPI subscription plan (e.g., **500 requests/day** for the free tier).
- Always use **pagination** when fetching large datasets to improve performance and reduce server load.
- **Cache frequently-used data** (such as genres) locally or in memory to avoid redundant requests.
- **Never expose your API key** on the frontend. Use server-side API routes (e.g., in Next.js) to keep it secure.
- Always handle loading and error states in your UI to provide a smooth and responsive user experience.
