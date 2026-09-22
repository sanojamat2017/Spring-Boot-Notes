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


src
 └── main
      ├── java
      │    └── com.example.demo
      │           ├── controller
      │           │      └── HomeController.java
      │           └── DemoApplication.java
      │
      └── resources
            ├── templates
            │      ├── login.html
            │      └── home.html
            │
            └── application.properties


import jakarta.servlet.http.HttpSession;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.*;

@Controller
public class HomeController {

    // Login Page
    @GetMapping("/")
    public String loginPage() {
        return "login";
    }

    // Login Process
    @PostMapping("/login")
    public String login(
            @RequestParam String username,
            @RequestParam String password,
            HttpSession session,
            Model model) {

        // Dummy validation
        if(username.equals("admin") && password.equals("1234")) {

            // Store data in session
            session.setAttribute("username", username);

            return "redirect:/home";
        }

        model.addAttribute("error", "Invalid Username or Password");

        return "login";
    }

    // Home Page
    @GetMapping("/home")
    public String home(HttpSession session,
                       Model model) {

        String username =
                (String) session.getAttribute("username");

        // If session not available
        if(username == null) {
            return "redirect:/";
        }

        model.addAttribute("username", username);

        return "home";
    }

    // Logout
    @GetMapping("/logout")
    public String logout(HttpSession session) {

        // Destroy session
        session.invalidate();

        return "redirect:/";
    }
}

# login.html

<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">

<head>
    <title>Login</title>
</head>

<body>

<h2>Login Page</h2>

<form action="/login" method="post">

    Username:
    <input type="text"
           name="username">

    <br><br>

    Password:
    <input type="password"
           name="password">

    <br><br>

    <button type="submit">
        Login
    </button>

</form>

<p style="color:red"
   th:text="${error}"></p>

</body>
</html>


# home.html

<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">

<head>
    <title>Home</title>
</head>

<body>

<h2>Welcome</h2>

<h3 th:text="${username}"></h3>

<a href="/logout">
    Logout
</a>

</body>
</html>

Important Session Methods

| Method            | Purpose          |
| ----------------- | ---------------- |
| setAttribute()    | Store data       |
| getAttribute()    | Read data        |
| removeAttribute() | Remove one value |
| invalidate()      | Destroy session  |

# application.properties

server.servlet.session.timeout=30m

# Advantages of Session

 Easy login management
 Secure user tracking
 Stores user-specific data
 Simple implementation in Spring Boot

# Disadvantages of Session

 Uses server memory
 Large applications need distributed sessions
 Session timeout handling required

# Why Session Needed?

Because HTTP is stateless.
