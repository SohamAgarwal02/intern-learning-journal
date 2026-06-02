# 1. What is Client–Server Architecture?
Client–Server Architecture is a model where a client requests services or data, and a server provides them. The client can be a web browser, mobile app, or desktop application, while the server stores and processes data. This architecture is widely used in websites, applications, and online services.

# 2. How the Web Works (End-to-End Flow)
When a user enters a website URL, the browser first finds the server's IP address using DNS. It then sends an HTTP/HTTPS request to the server. The server processes the request and sends back a response containing web page data. The browser renders the content and displays it to the user.

# 3. HTTP Basics (Methods & Status Codes)
HTTP (HyperText Transfer Protocol) is used for communication between clients and servers. Common methods include GET (retrieve data), POST (send data), PUT (update data), and DELETE (remove data). Common status codes are 200 (Success), 404 (Not Found), and 500 (Server Error).

# 4. Client vs Server Responsibilities
The client is responsible for sending requests, displaying data, and handling user interactions. The server processes requests, manages databases, performs business logic, and returns responses. Together they enable web applications to function efficiently.

# 5. Stateless Nature of HTTP
HTTP is a stateless protocol, meaning each request is independent and the server does not remember previous requests. To maintain user sessions, technologies such as cookies, session IDs, and tokens are used.

# 6. Introduction to APIs (REST Basics)
An API (Application Programming Interface) allows different software applications to communicate with each other. REST APIs use HTTP methods such as GET, POST, PUT, and DELETE. They usually exchange data in JSON format.
# 7. DNS and IP Address Concept
An IP address uniquely identifies a device on a network. DNS (Domain Name System) converts human-readable domain names like google.com into IP addresses. This makes websites easier for users to access.

# 8. HTTP vs HTTPS
HTTP transfers data in plain text and is less secure. HTTPS uses SSL/TLS encryption to protect data during transmission. HTTPS is recommended for secure communication and online transactions.

# 9. Basic Request–Response Flow (Login Example)
When a user enters login credentials, the browser sends a POST request to the server. The server verifies the username and password. If valid, it creates a session or token and sends a success response. The user is then granted access to the application.
