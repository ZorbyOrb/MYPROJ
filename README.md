# Project Setup Instructions

## Prerequisites
Ensure you have the following installed on your system:
- Windows Subsystem for Linux (WSL)
- Ubuntu (WSL)
- Visual Studio Code (VS Code)
- Podman

## Setup Steps

1. **Restart your system** and open a terminal.
    ```bash
    wsl -l -v
    ```

2. **Launch Ubuntu**.
    ```bash
    # Open VS Code within Ubuntu WSL
    code
    ```

3. **Create a project directory** in the VS Code terminal.
    ```bash
    mkdir <your-repo-name>
    cd <your-repo-name>
    ```

4. **Initialize Git in the project directory**.
    ```bash
    git init
    git config --global user.name "iitm-rollno"
    git config --global user.email "iitm-email"
    git remote add origin <your-repo-link.git>
    git pull origin main
    ```

5. **Authenticate with VS Code** to enable repository access.

6. **Locate your repository in VS Code** by using the "Open Folder" option in the Explorer panel.

7. **Open an Ubuntu terminal (not the VS Code terminal)**.
    ```bash
    cd <your-repo-name>
    ls  # Verify the repository files
    ```

8. **Make your first commit** by creating a new file `app.py` in VS Code.

## Building and Running the Docker Container
Ensure Podman is installed before proceeding.

### Build the Docker Image
```bash
podman build -t user-name/repo-name .
```

### Run the Docker Container
```bash
podman run -e AIPROXY_TOKEN=$env:AIPROXY_TOKEN -p 8000:8000 user-name/repo-name
```

## Accessing the API
The API is available at [http://localhost:8000/](http://localhost:8000/). Below are the available endpoints:

- **Home Endpoint**: `GET /`
  - Returns a message to verify the server is running.

- **Run Task Endpoint**: `POST /run?task=<task_description>`
  - Executes a task based on the provided description.

- **Read File Endpoint**: `GET /read?path=<file_path>`
  - Reads the contents of a specified file.

### Example API Requests

- Run a specific task:
    ```bash
    curl -X POST "http://localhost:8000/run?task=Format+/data/format.md+using+prettier"
    ```

- Read a file:
    ```bash
    curl "http://localhost:8000/read?path=/data/format.md"
    ```

## Contribution Guidelines
1. Fork the repository.
2. Create a new branch for your feature or bug fix.
3. Make your changes and commit them.
4. Push your changes to your forked repository.
5. Open a pull request to the main repository.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

