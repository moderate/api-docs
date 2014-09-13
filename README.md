# API Endpoints

## GET `/matter/<article-id>`

- Contains meta information about the content requested
  - Contains the cover image
  - Includes information about the author and their profile
- Contains the article content itself
  - Broken down into sections which have mysterious numerical-codes
  - These probably go with the type of content they are, i.e., quote, paragraph, etc.

## GET `/me/activity`
- HEADERS
    - Accept: application/json

- Returns the activity feed on the main page

