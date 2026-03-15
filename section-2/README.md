# Section 2 – Troubleshooting – 502 Bad Gateway

## Problem

The system contains two services:

- Nginx reverse proxy
- Node.js web application

The Node.js application runs on port 3000, but the Nginx configuration forwards traffic to port 8080.

Example configuration:

proxy_pass http://web:8080;

However, the Node.js application is listening on port:

const PORT = 3000;

Because of this mismatch, Nginx cannot connect to the backend service.

## Root Cause

The root cause of the 502 Bad Gateway error is a port mismatch between the reverse proxy and the backend service.

Nginx attempts to forward requests to port 8080, while the Node.js application is running on port 3000.

Since no service is listening on port 8080, Nginx cannot reach the backend and returns a 502 Bad Gateway response.

## Fix

The fix is to update the Nginx configuration so that it forwards requests to the correct port.

Correct configuration:

proxy_pass http://web:3000;

After updating the configuration, Nginx sends requests to the correct backend port where the Node.js application is running.

## Why This Works

After correcting the proxy target, Nginx can successfully communicate with the Node.js backend service.

Requests flow as follows:

Client → Nginx → Node.js application

## Preventing This in Production

Several best practices can prevent similar issues in production environments.

Use environment variables for configuration:

const PORT = process.env.PORT || 3000;

Avoid hardcoding ports in multiple configuration files.

Implement health checks to detect backend failures early.

Monitor logs and HTTP status codes to identify repeated 502 errors.

Use centralized configuration management for infrastructure and services.

## Conclusion

The issue was caused by incorrect port configuration between Nginx and the backend application.

Updating the proxy_pass directive to the correct port resolves the 502 Bad Gateway error and restores communication between the reverse proxy and the application.