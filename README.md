# DevOps Academy Assignment

This repository contains solutions for the DevOps Academy assignment.

Repository:  
https://github.com/SamuelM162/DevOpsAcademy1

---

## Sections

### Section 1 – Implementation

Task B – Dockerize a Python Web App

The Flask application was containerized using Docker and Docker Compose.

Application runs inside the container on port 3000 and is exposed to the host machine on port 3001.

Access:

http://localhost:3001

Details:
section-1/README.md

---

### Section 2 – Troubleshooting

Task A – 502 Bad Gateway (Nginx + Node.js)

The issue was caused by a port mismatch between Nginx and the Node.js application.

Nginx forwarded requests to port 8080 while the application was running on port 3000.

Fix: update proxy_pass to use the correct port.

Details:
section-2/README.md

---

### Section 3 – Thought Process

Task A – Production went down

This section explains a structured approach to debugging production incidents.

Steps include:
- confirming the incident
- checking recent deployments
- inspecting infrastructure
- reviewing logs
- applying rollback if necessary
- fixing the root cause

Details:
section-3/README.md

---

## Technologies Used

Docker  
Docker Compose  
Python  
Flask  
Nginx  
Node.js