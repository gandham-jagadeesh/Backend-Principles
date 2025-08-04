## What is a Backend?

A backend, in its traditional definition, is a computer that listens for HTTP, WebSocket, gRPC, or other kinds of requests through an open port, such as 80 or 443, which is accessible over the Internet, allowing clients or other frontends to connect to it, send data to it, or receive data depending on the kind of request.

The backend is referred to as a server because it provides or serves some kind of content, including static files like images, JavaScript files, or HTML files, as well as JSON, and it also accepts data sent by clients.

To understand the backend, it is essential to have a holistic view of its components and how they work behind the scenes, which involves going through the entire flow of how the backend operates and interacts with clients.

## How Backends Work?

The backend is served by a server deployed in AWS, and when a request is made from a browser, it reaches the server and receives a response, with the entire flow involving several steps, including DNS lookup and firewall configuration.

The request starts from the browser and reaches the server through the domain name, which is routed by the DNS server to the IP address of an EC2 instance in AWS, where the backend demo is deployed.

The DNS server has different types of records, including A records that point to a particular IP address and CNAME records that point to a domain name or subdomain, with the A record for the backend demo pointing to the IP address of the EC2 instance.

The request reaches the EC2 instance through the IP address and passes through a firewall, which is the AWS native firewall, before reaching the server, with the security group assigned to the instance specifying the ports that are allowed to be accessible over the internet.

The request is then managed by a reverse proxy server, which is NGINX, that sits in front of other servers and manages different types of redirects and configurations from a centralized space, with the config listening for port 80 and redirecting the request to port 443 for HTTPS.

The NGINX config is set up to redirect requests to the localhost port where the node server is running, with the final hop being the node server running on localhost, and the request is routed to the server using the domain name and port number.

The node server is managed by PM2, which is used to manage processes, and the request finally reaches the server, which is running on localhost, with the response being sent back to the browser through the same route.

The entire flow of the request involves several hops, including the browser, DNS server, AWS server, firewall, NGINX, and node server, before finally reaching the server and receiving a response.

## Why Do We Need Backends?

When a user interacts with an application, such as liking a post on Instagram, a series of actions occur between the user's device and the server, including sending a request to the server, processing the request, and sending a notification to the relevant user, all of which require a backend.

The backend server plays a crucial role in managing and storing data, such as user information and actions, and it must be centralized to handle all kinds of information and state for various users.

The primary responsibility of a backend can be condensed to a single word: data, which involves fetching, receiving, and persisting data, as well as performing actions that deal with data.

While it may seem possible to perform all backend functions on the frontend, such as connecting to a database and performing actions, this is not feasible due to the way frontends work behind the scenes, which will be explored further.

The concept of backend is essential for managing and storing data, and for performing actions that involve data, and it is necessary to have a centralized server that can handle all kinds of information and state for various users.

## How Frontends Work?

When the browser refreshes, it fetches the primary HTML file and other resources such as JavaScript, images, fonts, and CSS files in different requests after obtaining the HTML file.

The browser looks at the domain name, and the response is an HTML file, which is fetched along with other resources, and the record shows an entry for the subdomain "front end demo" that points to a particular IP address.

The IP address is traced to an EC2 instance, where ports 443 and 80 are allowed for HTTPS and HTTP traffic, and the request lands on the EC2 instance with the same public IP address.

The engine config shows that the server is listening for the "front end demo" domain and redirects traffic to localhost 3000, instead of 3001, and the request reaches the frontend Next.js server, which serves files such as JS, CSS, and HTML files.

The browser receives the main HTML file, goes through the resources, fetches them one by one, and paints the window with the fetched CSS, adding styles such as background, fonts, and button styles.

Once the browser fetches all the JavaScript files, it hydrates all the event listeners for buttons and interactions on the page, allowing buttons to work and redirect to other pages when clicked.

The process of fetching resources, painting the window, and hydrating event listeners enables the browser to render the page and make it interactive, allowing users to interact with the page.

## Why Can't We Write Backend Logic in Frontends?

Frontend logic is fetched by the browser from a server and executed by the browser in the client's machine, whereas backend logic is executed on the server, highlighting a key difference between the two, with the browser acting as the runtime for frontend code.

Browser runtimes are often sandbox environments, isolated from the operating system, processes, and file system, which restricts the code's access to resources, such as the DOM, browser APIs, local storage, and cookies, and only allows access to external APIs with the required headers.

The security policies of browsers, including CORS policy, restrict JavaScript code from calling external APIs that are not in the same domain, and while there are ways to get around this, it is a significant restriction for backend logic.

Writing backend logic in the frontend is not feasible due to security reasons, as browsers' security policies are restrictive, and backends often need to access the underlying file system, which browsers do not allow.

Another reason is that frontend code cannot call external APIs whenever needed, unless the API has the appropriate CORS headers, which is a significant limitation for backend servers that need to connect to other servers and fetch data from multiple places.

Databases are also a limitation, as server runtimes have access to native database drivers, which allow for efficient communication with databases, whereas browsers are not designed to maintain persistent connections to databases, and even if they were, each user would need to open their own connection, overwhelming the database server.

Computing power is also a limitation, as frontend applications can run on a wide range of devices with varying computing power, and heavy business logic can cause performance issues, whereas a centralized backend server can be easily scaled up to handle the load.

Overall, keeping backend logic in the frontend is not a good idea, and it is better to have a centralized backend server that can handle the load, access databases, and connect to external APIs, making it a more scalable and secure solution.
