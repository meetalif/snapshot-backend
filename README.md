# Picshar
Backend for Snapshot.

## Endpoints

- [x] Login endpoint with username and password
   - Must generate a session JWT
   - Method: POST
   - Path: '/users/login'
   - Body: { username, password }
   - Response: { token }
- [x] Login endpoint with JWT token
   - Method: POST
   - Path: '/users/login'
   - Body: { token }
   - Response: {}
- [x] User Registration Endpoint
   - Must generate a session JWT
   - Method: POST
   - Path: '/users/'
   - Body: { username, password, email, birthdate, bio }
   - Response: { token }


- [x] User information endpoint
   - Should not have private user information (password, birthday)
   - Must include the number of posts that the user has liked, calculated on-demand
   - Must include the number of publications that the user has uploaded, calculated on-demand
   - Must include the number of followers of the user, calculated on-demand
   - Must include the number of followers of the user, calculated on-demand
   - Method: GET
   - Path: '/users/'
   - Query: { user_id }
   - Response: { username, email, bio, liked_count, posts_count, followers_count, followed_count }
- [x] Endpoint of posts that a user has uploaded
   - It is only allowed if the user is following the user, unless it is the user themselves
   - Method: GET
   - Path: '/posts/'
   - Query: { author }
   - Response: { posts }
- [x] Endpoint of posts that a user has "liked"
   - It is only allowed if the user allows their likes to be seen, unless it is the user themselves
   - Method: GET
   - Path: '/posts/liked-by'
   - Query: { user_id }
   - Response: { posts }
- [x] Endpoint of posts that a user has saved
   - It is only allowed for the user himself
   - Method: GET
   - Path: '/posts/saved-by'
   - Query: { user_id }
   - Response: { posts }
- [x] Endpoint of users followed by a user
   - It is only allowed if the user is following the user, unless it is the user themselves
   - Method: GET
   - Path: '/follows/following'
   - Query: { user_id }
   - Response: { users }
- [x] Endpoint of a user's followers
   - It is only allowed if the user is following the user, unless it is the user themselves
   - Method: GET
   - Path: '/follows/followers'
   - Query: { user_id }
   - Response: { users }

- [x] Endpoint of requesting to follow a user
   - Only allowed if the user is no longer following the user
   - Method: POST
   - Path: '/follows/request'
   - Body: { user_id }
   - Response: {}
- [x] Endpoint accept or reject follow request
   - Only allowed if the user is the one receiving the request
   - Method: POST
   - Path: '/follows/response'
   - Body: { request_id, action }
   - Response: {}
   - The 'action' field corresponds to the string 'accept' or 'reject'.


- [x] Get timeline of a user
   - Must be paginated
   - Method: GET
   - Path: '/posts/timeline'
   - Body: { user_id }
   - Response: { posts }


- [x] Create/upload publication endpoint
   - Method: POST
   - Path: '/posts/'
   - Body: { img_url, bio, author }
   - Response: { }
- [x] Publication information endpoint
   - Must include the number of likes of the publication, calculated on-demand
   - Must include the comments of the publication, calculated on-demand
   - Method: GET
   - Path: '/posts/'
   - Body: { post_id }
   - Response: { img_url, bio, author, likes, comments }


- [x] Endpoint of liking a post
   - Method: POST
   - Path: '/posts/like'
   - Body: { post_id }
   - Response: { }
- [x] Endpoint of saving a post
   - Method: POST
   - Path: '/posts/save'
   - Body: { post_id }
   - Response: { }
- [x] Endpoint of commenting on a post
   - Method: POST
   - Path: '/posts/'
   - Body: { post_id, comment }
   - Response: { }


## Unit Tests (Jest)

- [x] Login
   - [x] Valid information
   - [x] Invalid information (user does not exist)
   - [x] Invalid information (wrong password)
- [x] Registration
   - [x] Complete information
   - [x] Incomplete information


- [x] User Information
   - [x] Password and birthday not included in the response
   - [x] Number of user posts reflects the correct number
   - [x] Number of posts that the user likes reflects the correct number
   - [x] Number of followers reflects the correct number
   - [x] Number of followed reflects the correct number


- [x] List of followers of a user
- [x] List of a user's followers
- [x] Request to follow
- [x] Accept request
   - [x] Accept previously accepted or rejected request
- [x] Reject request
   - [x] Reject previously accepted or rejected request


- [x] Like the post
- [x] Posts "liked" by a user
- [x] Save post
- [x] Posts saved by a user
- [x] Comment post
- [x] Comments on a publication