# Use the official Go image as the base
FROM golang:1.22

# Set the working directory inside the container
WORKDIR /app

# Copy the local code to the container
COPY . .

# Build the Go application
RUN go build -o main main.go

# Expose port 8001
EXPOSE 8001

# Run the binary
CMD ["./main"]