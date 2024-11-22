# DevTinder Project -Authentication, JWT & Cookies

## Code Demonstration Link

* [DevTinder Backend Repository](https://github.com/akshadjaiswal/devTinder-backend)

# DevTinder Project - API Development and Express Router

## Overview
Today's learning focused on finalizing the DevTinder API endpoints and structuring the application using Express Router for better modularity and maintainability. The APIs were categorized into different routers based on their functionality.

---

## 1. DevTinder API Endpoints

### Auth Router
Handles user authentication, including signup, login, and logout.
- **POST `/signup`**: Register a new user.
- **POST `/login`**: Authenticate a user and issue a token.
- **POST `/logout`**: Revoke the user's session.

---

### Profile Router
Manages user profile-related operations.
- **GET `/profile/view`**: Retrieve the profile information of the logged-in user.
- **PATCH `/profile/edit`**: Update user profile details.
- **PATCH `/profile/password`**: Change the user's password.

---

### Connection Request Router
Handles connection requests between users with various statuses:
- **Status Options**: `ignore`, `interested`, `accepted`, `rejected`.
- **Endpoints**:
  - **POST `/request/send/intrested/:userId`**: Send a connection request to another user.
  - **POST `/request/ignored/:userId`**: Mark a request as ignored.
  - **POST `/request/review/accepted/:requestId`**: Accept a connection request.
  - **POST `/request/review/rejected/:requestId`**: Reject a connection request.

---

### User Router
Handles operations related to connections, requests, and the user feed.
- **GET `/user/connections`**: Get a list of connections for the logged-in user.
- **GET `/user/requests/received`**: Retrieve a list of received connection requests.
- **GET `/user/feed`**: Get a list of suggested users to connect with.

---

## 2. Structuring with Express Router

### Key Concepts:
1. **Creating a Routes Folder**:
   - Organize the API endpoints into separate route files for each functionality (e.g., `authRoutes.js`, `profileRoutes.js`).

2. **Using Express Router**:
   - Leverage the `express.Router()` to define routes in a modular way.
   - Each route file exports its router, which is then mounted to a specific path in the main application file.

```javascript
    const express = require("express");
    const profileRouter = express.Router();
    const { userAuth } = require("../Middlewares/auth");


    //profile API to get the profile details
    profileRouter.get("/profile", userAuth, async (req, res) => {
        const user = req.user;
        res.send(user);
    });

    module.exports = profileRouter;
```

### Benefits of Using Express Router:
- **Modularity**: Separate files for each router improve code organization and readability.
- **Scalability**: Easier to maintain and expand as the application grows.
- **Reusability**: Common middleware and logic can be reused across routes.

---

## Conclusion
This structured approach to API development ensures that the DevTinder backend is organized, maintainable, and scalable. Using Express Router and clearly defined endpoints simplifies future feature additions and debugging.
