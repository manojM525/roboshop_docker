# ---------- Stage 1: Build ----------
FROM golang:1.22-alpine AS builder

# Install build dependencies
RUN apk add --no-cache git

# Set working directory
WORKDIR /build

# Copy go module files first (for caching dependencies)
COPY go.mod go.sum ./

# Download dependencies
RUN go mod download

# Copy the rest of the application source
COPY . .

# Build the binary
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 \
    go build -ldflags="-s -w" -o app .

# ---------- Stage 2: Runtime ----------
FROM gcr.io/distroless/base-debian12

WORKDIR /app

# Copy compiled binary from builder stage
COPY --from=builder /build/app .

# Expose application port
EXPOSE 8080

# Run as non-root user
USER roboshop:roboshop

# Start the service
ENTRYPOINT ["./app"]