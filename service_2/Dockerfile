# Use an official Python runtime as the base image
FROM python:3.13

# Set the working directory inside the container
WORKDIR /app

# Install uv
RUN pip install uv

# Copy the local code to the container
COPY . .

# Create and activate a virtual environment, then sync dependencies
RUN uv venv
RUN uv sync

# Expose port 8002
EXPOSE 8002

# Run the app
CMD ["uv", "run", "app.py"]