# API Endpoints

## GET /<collection-user>/<article-id>

- Contains all of the data about the article
  - Stored in the `GLOBALS` JS variable
    - Has data about the current user (useful for the auth-scheme)
    - Contains a variable called "embed" which has the article itself
      - `creator` -> The person who wrote the article and various bio information.  Looks very similar (probably the same) to the `current_user` variable (documented above.)
      - Meta about the article
        - The title, the time it was created/updated
        - The ID of the collection that it is in
      - The `content` of the article contains all of the actual content from that article (shocker)
        - `paragraphs` is an array of JSON object blobs that contain the text of the paragraph, the type of data, and the markups (if any) which are all explained below

#### The user

A user actually contains a **lot** of data, so documented below are the most useful ones:

  - `userId` - the UUID (referenceable across Medium's API) of the user that you're looking at
  - `username` - the Twitter username of the user
    - `twitterScreenName` - the actual screenname on Twitter of the user (seems to be the same between the `username` and this field
  - `name` - the fullname of the user
  - `bio` - the sentence bio of the user, contains @ references
  - `twitterAvatar` - a link to the profile image of the user
  - `createdAt` and `updatedAt` the Unix timestamp of the time the account was created and updated at

Then there is a bunch of data about how many posts you've read, upvoted, unvoted, etc.

#### The paragraph
  - `type` - The type of content that it is
    - 1: text
    - 4: image
  - `text` - Exactly what it sounds like.  Contains the text of that paragraph (more of a grouping, really) without any markup whatsoever - totally plaintext.
  - `markups` - Contains the styling that is applied to certain parts of the text (since none is provided above) and described below

#### The markup object
  - `type` - The kind of markup that it is
    - 2: italics
    - 3: a link to something
  - `start` and `end` are the zero-indexed character count of the markup start and endpoints
  - `href` if `:type => 3`, the link that that anchor should contain
  - `title` and `ref` - (see above)

## GET `/me/activity`
- HEADERS
    - Accept: application/json

- Returns the activity feed on the main page

