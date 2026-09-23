# Spring-Boot-Session Module

# What is Session ?
1. A Session is a way to store user-specific data on the server for a particular user while they are using an application.
2. It helps the server remember the user between multiple requests.
3. HTTP is a stateless protocol, meaning:
    Request 1 → server responds
    Request 2 → server does not remember Request 1
So session is used to maintain user information across requests.

# Real-Time Example
    1. Gmail
    2. Facebook
# After login:

1. You open multiple pages
2. Refresh browser
3. Navigate to profile/dashboard

# Still the application remembers:

1. Your username
2. Login status
3. Cart data
4. Preferences

This is done using Session Management.

# Why Do We Need Session?

# Without session:

1. User must login again for every request
2. Cart data will be lost
3. User information cannot be maintained

# Session helps to:

1. Keep user logged in
2. Store temporary user data
3. Track user activity
4. Maintain shopping cart
5. Secure authenticated users

# When Do We Use Session?

We use sessions when application needs to remember users.

| # | Application / System | Session Usage                                            |
| - | -------------------- | -------------------------------------------------------- |
| 1 | Application          | Maintain user login/session information                  |
| 2 | Banking App          | Track the logged-in user during banking activities       |
| 3 | E-commerce           | Maintain shopping cart and user session                  |
| 4 | Student Portal       | Maintain student login and session information           |
| 5 | Admin Dashboard      | Maintain admin authentication and access                 |
| 6 | Online Exam          | Track the logged-in candidate during the exam            |
| 7 | Social Media         | Maintain user login and session while using the platform |



# What is Session Management?

# Session management means:

Creating, maintaining, validating, and destroying user sessions.

# It includes:

1. Creating session after login
2. Storing user data in session
3. Using session across requests
4. Invalidating session during logout

# Step-by-Step Flow

1. User logs in
2. Server creates session
3. Session ID generated
4. Session ID stored in browser cookie
5. Browser sends Session ID in every request
6. Server identifies user using Session ID

| **Session**                                                        | **Cookie**                                                     |
| ------------------------------------------------------------------ | -------------------------------------------------------------- |
| Stored on the **server**                                           | Stored in the **browser/client**                               |
| Generally **more secure** because data is maintained on the server | Generally **less secure** because data is stored on the client |
| Can store **objects and complex data**                             | Mainly stores **small text/string values**                     |
| Usually **temporary** and ends after timeout or logout             | Can **persist longer**, depending on its expiration time       |
| Suitable for **login/authentication information**                  | Suitable for **preferences and small client-side data**        |
| Consumes **server memory/resources**                               | Does not consume server memory for storing the cookie data     |
| Session ID is commonly sent to the browser                         | Cookie itself is sent between browser and server               |
| Example: `HttpSession` in Java                                     | Example: `Cookie` in Java                                      |


# Dependencies

Add:

1. Spring Web
2. Thymeleaf

# 1. What is a Cookie?

A cookie is a small piece of data stored in the user's web browser by the server.

For example, when a user submits:

Name     : Sanoj\
Email    : sanoj@gmail.com\
City     : Mumbai\

Spring Boot can ask the browser to store:

username = Sanoj\
email = sanoj@gmail.com\
city = Mumbai\

The browser stores this information and automatically sends the cookie back to the server with later requests to the same site.

2. Why Do We Need Cookies?

Cookies are useful when the browser needs to remember something between requests.

| Cookie               | Session                                                 | Database                        |
| -------------------- | ------------------------------------------------------- | ------------------------------- |
| Stored in browser    | Stored on server                                        | Stored in database              |
| Small data           | Can hold server-side state                              | Large persistent data           |
| Sent with requests   | Identified using session ID                             | Accessed using queries          |
| User can inspect it  | User normally can't see session data directly           | User doesn't directly access DB |
| Can have expiration  | Usually temporary/persistent depending on configuration | Persistent                      |
| Good for preferences | Good for login/session state                            | Good for permanent records      |


4. Types of Cookies

There are several important cookie concepts.

1. Session Cookie

Cookie exists until the browser session ends.

Browser opens
     ↓
Cookie created
     ↓
Browser closed
     ↓
Cookie normally removed
2. Persistent Cookie

Has an expiration time.

Example:

username=Sanoj
Max-Age=3600

It can remain after the browser is closed until it expires.

3. Secure Cookie

Sent only over HTTPS.

Secure
4. HttpOnly Cookie

JavaScript cannot normally access it.

HttpOnly

Useful for security-sensitive cookies such as authentication tokens.

5. SameSite Cookie

Controls cross-site sending behavior.

Common values:

Strict
Lax
None

5. Create Spring Boot Project

Create a project with:

Spring Web
Thymeleaf
Spring Boot DevTools

We don't need MySQL for this particular cookie example because the purpose is to learn browser-side cookie storage.
