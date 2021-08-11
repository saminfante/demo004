# FpURL

A Python URL Shortener demo app built with Flask.

### Task

- Design a URL shortener (like bit.ly) where a user can enter a 'full URL' and get a generated 'short URL'

### Scope

- No user accounts
- No ability to edit URLs
- Tracks link visits (analytics)
- No true authentication but shortlinks should not be easy to "guess"
- Has a frontend and an API
- Has Stats link with analytics for each URL

### Assumptions

- Would likely get heavy traffic in a prod environment
- Must be able to store millions of URLs
- Traffic would not be evenly distributed across URLs
- Some short URLs would be accessed far more than others

### Components

- TODO: create a diagram of the major components

### Key Challenges/Issues

- How should we store the documents?
    - options:
        - Used a database for this version (SQLite) for both stats and the document store.
        - Storing docs on a file would be ideal since docs can be large, and we won't likely need a search feature.

### More info

    - For this version we used a db (SQLite)
    - Cache invalidation not a priority since short URLs cannot be edited
    - Several other issues/system design challenges to be discussed in code review.
    - This impl. is far from ideal but a much better iteration may be ready before the code review.

### Future improvements (scalability/performance)

    - Skip the "full" docs db and just let a hash of the URL indicate which server contains the document.
    - (e.g. use a file store, possibly with a minimal DB only for the statistics.
    - Create a more optimal way to generate URLs and avoid/resolve any collisions
    - Preferably store all raw data from each visit (flexibility for future analytics)
    - Use datastore for analytics and create a table with columns: shorturl, datetime, visits.
