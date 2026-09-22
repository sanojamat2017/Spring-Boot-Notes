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

# This is done using Session Management.

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

# Common 			                Use Cases
1. Application		                Session Usage
2. Banking App		                Logged-in user
3. E-commerce		                Shopping cart
4. Student Portal		            Student login
5. Admin Dashboard		            Admin authentication
6. Online Exam		                Candidate tracking
7. Social Media		                User session

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

# Session			                      Cookie
Stored on server	                  Stored in browser
More secure		                      Less secure
Can store objects	                  Stores text only
Temporary		                        Can persist longer

