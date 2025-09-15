# CodeRefine-SystemDesign-IEEEMDB

### Description
IEEEMDB is a system that helps people discover movies, track what they've watched, and share their thoughts with friends. Think of it as a personal movie diary and social network all in one.

### Functional Requirements:
1. Admins should be able to add movies
2. Users should be able to review movies
3. Users should be able to view suggested movies
4. Users should be able to search movies

--- out of scope ---
- Users should be able to create and share their own movie lists
- Users should be able to follow other users
- Users should be able to specify whether he watched a specific movie or not 
- Users should be able to get notified when new movie of their likings come out
  
### Non Functional Requirements:
- low latency search
- High scalability especially in storage
- Highly available

--- out of scope ---
- GDPR user privacy
- handling system failures
- monitoring, logging
- CI/CD pipeline
---
### Data Models
```
Movie {
    id,
    title,
    description,
    trailers,
    photos,
    actors,
    Rate,
    genres
    ...metadata
}
```
```
genre {
    id,
    name
}
```
```
Actor {
    id,
    name,
    ...metadata
}
```
```
Review {
    id,
    description,
    reviewerId
    rate,
    ...metadata
}
```
```
User {
    id,
    name,
    roles,
    ...metadata
}
```
```
role {
    id,
    name
}
```
```
Notification {
    id,
    movieSummery,
    description
    ...metadata
}
```
```
MovieSummery {
    movieId,
    movieName
}
```
---
### APIs
```
POST /user -> user | null
{
    name,
    ...metadata
}
```
```
POST /movie -> movie | null
{
    title,
    description,
    trailers,
    photos,
    actors,
    Rate
    ...metadata
}
```
```
POST /review -> review | null
{
    description,
    reviewerId (won't exist in body but will be  extracted from auth token),
    rate,
    ...metadata    
}
```
```
GET /search -> list<movies>
{
    title,
    actor,
    genre,
    ...parameters
}
```
```
WSS /notification
{
    movieSummery,
    description
    ...metadata
}
```
### System Design
[System Design file](https://github.com/OmarNaru1110/CodeRefine-SystemDesign/blob/e0d9ddf2552666e927cf92e1253db334ea67107a/system%20design.excalidraw)

---
### Deep Dive
[Deep Dive file](https://github.com/OmarNaru1110/CodeRefine-SystemDesign/blob/e0d9ddf2552666e927cf92e1253db334ea67107a/deep%20dive)
