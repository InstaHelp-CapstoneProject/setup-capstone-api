# Dockerfile for Python Application

This Dockerfile defines the steps to build a Docker image for a Python-based application running on Python 3.12 with Alpine Linux. It includes necessary dependencies and sets up the application to run with Gunicorn.

## Steps:

1. **Base Image**
    - The image starts with the `python:3.12-alpine` base image, which is a minimal image for Python 3.12 on Alpine Linux.

2. **Install System Dependencies**
    - Installs essential system dependencies, including:
        - `gcc`, `musl-dev`, `linux-headers`, `postgresql-dev`, `libffi-dev`, `openssl-dev`, `mysql-dev`, `build-base`, and `file-dev` (which includes `libmagic`).

3. **Set Working Directory**
    - The working directory inside the container is set to `/app`.

4. **Copy Requirements File**
    - Copies the `requirements.txt` file into the container.

5. **Install Python Dependencies**
    - Installs Python dependencies listed in `requirements.txt` using `pip` with `--no-cache-dir` to prevent caching.

6. **Copy Application Files**
    - Copies the rest of the application files into the container.

7. **Expose Port**
    - Exposes port `8080` for the application to be accessible externally.

8. **Start the Application**
    - The application is started using `gunicorn` with 4 worker processes, binding it to `0.0.0.0:8080` and specifying the entry point as `app:app`.

```Dockerfile
# Base image
FROM python:3.12-alpine

# Install system dependencies including libmagic
RUN apk add --no-cache \
    gcc \
    musl-dev \
    linux-headers \
    postgresql-dev \
    libffi-dev \
    openssl-dev \
    mysql-dev \
    build-base \
    file-dev  # Install file package that includes libmagic

# Set working directory
WORKDIR /app

# Copy requirements first
COPY requirements.txt . 

# Install Python dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy application files
COPY . .

# Expose the required port
EXPOSE 8080

# Start the application with gunicorn
CMD ["gunicorn", "-w", "4", "-b", "0.0.0.0:8080", "app:app"]
