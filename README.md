# Webserv

**Webserv** is a lightweight, event-driven web server written in C++ that supports HTTP/1.1 methods (GET, POST, DELETE) along with CGI integration for dynamic content. 
It uses non-blocking I/O via the `poll` mechanism and includes a configuration parser to allow flexible server and location settings. 
Additionally, the project includes example Python CGI scripts for handling dynamic requests and file uploads.

## Features

- **HTTP/1.1 Support:**  
  Handles basic HTTP methods including GET, POST, and DELETE.

- **CGI Integration:**  
  Executes CGI scripts (e.g., Python scripts) to generate dynamic responses.

- **Event-Driven I/O:**  
  Uses `poll` to efficiently manage multiple client connections and I/O events.

- **Custom Configuration:**  
  Parses configuration files (e.g., `configs/default.conf`) to set up multiple servers, locations, error pages, redirects, and more.

- **Autoindex and File Uploads:**  
  Supports directory listings (autoindex) when enabled and provides file upload functionality via multipart/form-data.

- **Error Handling and Redirects:**  
  Configurable error pages and support for HTTP redirects.           

## Installation

### Prerequisites

- **Compiler:** A modern C++ compiler (e.g., `g++` supporting C++11 or later).
- **Build Tools:** Make using a Makefile.
- **Python 3:** Required to run the CGI scripts.
- **POSIX Environment:** The project uses UNIX-specific system calls (e.g., `fork`, `poll`).

### Building the Server

1. **Clone the repository:**

   ```bash
   git clone https://github.com/DjoykeAbyah/42_WEBSERV.git
   cd 42_WEBSERV
   ```

2. **Compile the project:**
  A Makefile is provided, so simply run:

  ```bash
  make
  ```

### Running the Server

To run the server, execute the compiled binary. You can optionally pass a configuration file as a command-line argument. 
If none is provided, the server defaults to `configs/default.conf`.

```bash
./localhost:8080
```

# Configuration

The server reads its settings from a configuration file (e.g., `default.conf`). The configuration allows you to specify:

### Server Settings:
- Port  
- Server name  
- Root directory  
- Index file  
- Error pages  
- Autoindex options  

### Location Blocks:
- Specific directives for certain URL paths (e.g., CGI settings, allowed methods, upload paths).

Make sure the configuration file is not empty and follows the expected format.

# Usage

### Accessing the Homepage

Open `www/index.html` in your browser (or visit `http://localhost:8080/index.html`) to see the homepage. The page includes links for:

- **Greeting via a CGI GET request:** Handled by `cgi-bin/hello.py`.
- **Uploading reviews or files:** Handled by `cgi-bin/post.py`.
- **Viewing saved reviews/messages:** Handled by `cgi-bin/get.py`.

### CGI Scripts

The CGI scripts in the `cgi-bin` directory demonstrate dynamic content handling:

- **hello.py:** Greets the user using data from GET parameters.
- **post.py:** Accepts POST requests to save review messages (and file uploads) to disk.
- **get.py:** Reads and displays the saved messages.


