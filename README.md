# Jenkins CI/CD Pipeline with Docker Agent on AWS EC2

# Project Overview

This project demonstrates the implementation of a CI/CD pipeline using Jenkins, Docker, AWS EC2, and GitHub.

Jenkins is hosted on an AWS EC2 instance and integrated with a GitHub repository. Docker is configured as a Jenkins build agent, allowing pipeline jobs to execute inside isolated Docker containers instead of installing all build dependencies directly on the Jenkins server.

The main goal of this project is to create an automated, efficient, and reusable CI/CD workflow while improving resource utilization and maintaining a clean Jenkins environment.

# Architecture

                    ┌─────────────────┐
                    │     Developer   │
                    │  Push / Commit  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │     GitHub      │
                    │   Repository    │
                    └────────┬────────┘
                             │
                             │ Webhook / Polling
                             ▼
              ┌─────────────────────────────┐
              │        AWS EC2 Instance     │
              │                             │
              │          Jenkins            │
              │             │               │
              │             ▼               │
              │     Docker Jenkins Agent    │
              │             │               │
              │             ▼               │
              │       Build / Test         │
              │                             │
              └─────────────────────────────┘

# Technologies Used

AWS EC2 – Jenkins server

Jenkins – CI/CD automation server

Docker – Containerization and Jenkins build agent

GitHub – Source code management

Jenkins Docker Plugin – Docker-based agent integration

Jenkins Pipeline – Pipeline automation

Git / GitHub Integration – Source code management

# CI/CD Workflow

The pipeline follows this workflow:

-Developer pushes code to the GitHub repository.

-Jenkins detects the repository change.

-Jenkins starts the required Docker-based agent.

-The source code is pulled from GitHub.

-Dependencies are installed inside the Docker environment.

-Application build steps are executed.

-Automated tests can be executed.

-If all stages are successful, the pipeline completes successfully.

-Docker agent/container can then be removed, keeping the Jenkins environment clean.

# Why Docker as a Jenkins Agent?

Instead of installing every required build tool directly on the Jenkins EC2 server, Docker is used to provide an isolated build environment.
Benefits
-Clean and isolated build environment
-Consistent build dependencies
-Easy environment setup
-Reduced configuration on the Jenkins server
-Better resource utilization
-Agents can be created when required
-Easy to reproduce builds
-Helps avoid dependency conflicts

This approach also supports cost optimization because the same EC2 infrastructure can run different workloads using temporary containerized build environments instead of requiring separate servers for different build requirements.

# Jenkins Plugins
The project uses Jenkins plugins required for GitHub and Docker integration.
Important components include: 
Git plugin
GitHub integration
Pipeline plugin
Docker-related Jenkins plugin
Docker Pipeline functionality
