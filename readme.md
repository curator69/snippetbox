# Snippetbox

Snippetbox is a web application built in Go that allows users to paste, share, and view text snippets — similar to services like Pastebin or GitHub Gists. It is designed with simplicity, security, and scalability in mind, leveraging Go's performance and MySQL for data storage.

## Features

- **User Authentication**: Only registered users can create snippets.
- **Session Management**: Secure cookie-based session management.
- **Snippet Management**: Create, read, and manage snippets with customizable expiration dates (1 day, 1 week, or 1 year).
- **MySQL Integration**: All snippets and user data are stored in a MySQL database.
- **Secure by Design**: The application is HTTPS-ready with TLS support and follows best security practices.
- **Dynamic HTML Templating**: HTML templates with Go's html/template package for safe rendering of dynamic content.
- **Middleware for Logging and Recovery**: Includes middleware for structured logging and panic recovery to handle errors gracefully.

## Demo

You can check out a live demo of Snippetbox hosted on an AWS EC2 instance: [Live Demo](http://13.233.101.20:4000)

## Project Setup

### Prerequisites

- Go 1.11+ (with module support)
- MySQL database
- Git

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/curator69/snippetbox.git
   ```
2. Navigate to the project directory:

   ```bash
   cd snippetbox
   ```
3. Install Go modules:

   ```bash
   go mod tidy
   ```
4. Set up MySQL and create a database for Snippetbox:

   ```bash
   CREATE DATABASE snippetbox;
   ```
5. Create a .env file in the root directory with the following content:

   ```env
   DB_DSN="username:password@/snippetbox"
   ```

   Replace username and password with your MySQL credentials.
6. Start the application:

   ```bash
   go run cmd/web/*
   ```
7. Access the application by visiting http://localhost:4000 in your browser.

### File Structure

```
/cmd/web    # Contains the main entry point and handlers
/pkg        # Application-specific packages (models, database interaction)
/ui         # User interface assets (HTML templates, CSS, JS)
  /ui/html  # HTML templates for various pages
  /ui/static # Static assets like CSS, JS, images
```

### Key Components

- **Handlers**: Found under /cmd/web/handlers.go, they control the flow of requests and responses.
- **Templates**: Located in /ui/html/, the Go templates are responsible for rendering dynamic HTML pages.
- **Database Models**: Defined in /pkg/models, these handle the interaction with the MySQL database.
- **Sessions**: Managed using the SCS package to provide secure session management.

## Deployment

Snippetbox is currently deployed on an AWS EC2 instance and can be accessed here: [http://13.233.101.20:4000](http://13.233.101.20:4000)

### How to Deploy

1. Set up an AWS EC2 instance with Ubuntu or Amazon Linux.
2. Install Go and MySQL on the server.
3. Clone the repository and set up environment variables with your MySQL DSN.
4. Use a process manager like pm2 or systemd to run the Go application as a service.
5. Use NGINX or Apache to reverse proxy and serve the application over HTTPS.

## Contributing

Contributions are welcome! Feel free to submit pull requests or open issues for bug fixes, new features, or enhancements.

## License

This project is open-source and available under the MIT License. See the LICENSE file for more details.

## Acknowledgments

- **[Alex Edwards](https://www.alexedwards.net/)** for the [Let&#39;s Go book](https://lets-go.alexedwards.net/), which inspired the structure of this project.
