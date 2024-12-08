# Use the official Python image from the Docker Hub
FROM python:3.9-slim

# Set the working directory
WORKDIR /workspace

# Install system dependencies
RUN apt-get update && apt-get install -y \
    build-essential \
    libpq-dev \
    git \
    && rm -rf /var/lib/apt/lists/*

# Create a non-root user and set permissions
RUN useradd -ms /bin/bash vscode \
    && mkdir -p /home/vscode/.local/bin \
    && chown -R vscode:vscode /home/vscode \
    && chown -R vscode:vscode /workspace

# Switch to the non-root user
USER vscode

# Copy requirements.txt and install Python dependencies
COPY requirements.txt /workspace/
RUN pip install --no-cache-dir -r requirements.txt