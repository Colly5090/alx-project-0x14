# API Explorer: Mastering RESTful Connections

CineSeek is a modern movie discovery application built with Next.js, TypeScript, and Tailwind CSS. The application allows users to browse movies from the MoviesDatabase API, view movie details, and search for films by year or genre. The project focuses on creating a responsive, well-structured web application with proper API integration and TypeScript typing.

## API Overview

This api provides complete and updated data for over 9 million movies, series and episodes titles and 11 million actors / crew and cast members. It involves the collection of information for movies, tv-shows, actors. Including youtube trailer url, awards, full biography, and many other usefull informations

## API Version

v1 (current)

## Available Endpoints

- Titles: This endpoint is used to get the title of series, movies, episodes and ratings.
- Search: This let you get a movie by searching by imdb id, alias, title and a keyword.
- Actors: This let you get available actors
- Utils: This helps in searching by genres, list and titleTypes of utils
- Obsolete: This allows crew and main actors to be searched

## Request and Response Format

### Request

This request uses GET method and includes the necessary headers for authentication and host information.

| Field    | Value                           | Description                       |
| -------- | ------------------------------- | --------------------------------- |
| Method   | `GET`                           | Retrieves data                    |
| Hostname | `moviesdatabase.p.rapidapi.com` | Base API hostname                 |
| Headers  | `x-rapidapi-key`                | Your API Key for authentication   |
|          | `x-rapidapi-host`               | Hostname for routing via RapidAPI |

### Response

A successful response will return a JSON object containing metadata and a list of movie titles.

{
"page": 1,
"next": "/titles?page=2",
"entries": 50,
"results": [
{
"id": "tt0000001",
"titleText": {
"text": "Carmencita"
},
"titleType": {
"text": "short"
},
"releaseYear": {
"year": 1894
}
},
{
"id": "tt0000002",
"titleText": {
"text": "Le clown et ses chiens"
},
"titleType": {
"text": "short"
},
"releaseYear": {
"year": 1892
}
}
]
}

## Authentication

In the GET request header the API key can be provided as a value to the 'x-rapidapi-key' key

## Error Handling

The Movies Database API may return error responses in cases of invalid requests, authentication issues, or exceeded rate limits. Below are common HTTP error statuses and how to handle them.

| HTTP Status | Description           | Cause                                       |
| ----------- | --------------------- | ------------------------------------------- |
| 401         | Unauthorized          | Missing or invalid `x-rapidapi-key`         |
| 403         | Forbidden             | Key does not have access or is rate-limited |
| 404         | Not Found             | Invalid endpoint or resource                |
| 429         | Too Many Requests     | Exceeded usage quota or rate limit          |
| 500         | Internal Server Error | Problem on the server side                  |

**Error Handling in Code Snippet**
if (res.statusCode >= 200 && res.statusCode < 300) {
console.log("Success:", JSON.parse(body));
} else {
console.error(`Error ${res.statusCode}:`, body);
}

## Usage Limits and Best Practices

As part of RapidAPI’s platform, this API enforces usage limits based on our free tier subscription plan for this project.

**Best Practices**

- **Use Pagination:** When retrieving large datasets, use pagination to avoid overloading the server and staying within rate limits.

- **Cache Responses:** Cache static data (like movie details) on your end to reduce repeated API calls.
- **Monitor Usage:** Periodically check usage stats on RapidAPI to avoid unexpected cutoffs.
