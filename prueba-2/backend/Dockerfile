# Use Python 3.9 slim as base image 
FROM python:3.9-slim

# Set working directory for the application
WORKDIR /app

# Set environment variables 
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Upgrade pip to the latest version
RUN pip install --upgrade pip

# Copy requirements file and install Python dependencies
COPY requirements.txt .

# Install PostgreSQL client 
RUN apt-get update && apt-get install -y postgresql-client

# Install temporary build dependencies (gcc) for psycopg2, install Python packages, then clean up to reduce image size
RUN apt-get install -y --no-install-recommends gcc && \
    pip install -r requirements.txt && \
    apt-get purge -y --auto-remove gcc

# Copy the entire project to the container
COPY . .

# Command to run the Django development server, exposing it on all interfaces for Docker
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]