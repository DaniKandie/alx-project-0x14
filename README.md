# CineSeek Movie Discovery App
This project connects to the MoviesDatabase API to display popular and trending movies. Users can search movies by year, genre, or keywords. The app is built using Next.js, TypeScript, and Tailwind CSS.

## API Overview
The MoviesDatabase API provides movie-related information such as titles, genres, release years, and more. It supports search filters like year and genre, and returns detailed results including poster, plot, and ratings. It's ideal for building modern movie discovery apps. It includes youtube trailer url, awards, full biography, and many other usefull informations. 

## API Version
Version: v2.62

## Available Endpoints

- `/titles`: Get movie titles and details. Can filter by genre, year, and more.
- `/titles/search/title`: Search for movies by name/title.
- `/titles/x/titles-by-ids`: Get multiple movies using their unique IDs, from seasons, episodes. upcoming etc
- `/genres`: Get a list of all movie genres.
- `/countries`: Get a list of available countries of origin.
- `/languages`: List of spoken languages in the movies.

## Request and Response Format
### Sample Request (GET `/titles`)
```http
GET https://moviesdatabase.p.rapidapi.com/titles
Headers:
  X-RapidAPI-Key: your_api_key
  X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
Query params:
year=2023
genre=comedy
page=1


**Response (sample JSON):**
```json
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

## Authentication
You must supply your RapidAPI credentials in the HTTP request headers:

X-RapidAPI-Key: your_api_key
X-RapidAPI-Host: moviesdatabase.p.rapidapi.com
These headers authenticate and identify your client to access the endpoints. 

## Error Handling

### Common API errors and their meaning:
- 401 Unauthorized: API key is invalid or missing
- 429 Too Many Requests: Rate limit exceeded
- 5xx responses: Server-side error
- Use try/catch blocks in your code to catch errors. Check HTTP status codes and display user-friendly messages or retry logic if rate-limited.

## Usage Limits and Best Practices
- The API is rate‑limited based on your RapidAPI plan—free tier limits may be low (e.g. hundreds of calls/day).
- Always use pagination to limit response size and reduce load.
- Cache frequent data (e.g. genres list) to reduce calls.
- Never expose your API key on the client side—instead use Next.js server/UI routes or API routes to keep keys hidden.
- Handle loading states so the user sees feedback while data fetches happen