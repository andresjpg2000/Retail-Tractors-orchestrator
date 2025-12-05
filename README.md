# Retail Tractors – Orchestrator Repository

This repository acts as the central entry point for the entire Retail Tractors microservices platform.

It does not contain the actual code for the microservices.
Instead, it contains:

Git submodules pointing to each microservice

The API Gateway configuration (Nginx)

Docker Swarm / Docker Compose orchestration files

Shared environment variables

Project-wide documentation

By cloning this single repository, you automatically pull all microservice repositories.

# Purpose of the Orchestrator Repo

This repository exists to:

✔ Centralize the whole microservices system

All services are tracked here through Git submodules.

✔ Provide one-command setup for the entire platform

Developers can clone everything with a single command.

✔ Hold the API Gateway configuration

Nginx routes all external API requests to the correct microservice.

✔ Serve as the deployment entry point

The repo includes shared Docker Compose or Docker Swarm files used to run the full system.

✔ Keep architecture consistent

Global network config, gateway routing, environment variables, logging setup, etc. live here.

# Repository Structure
/
├── services/
│   ├── users-service/          # Git submodule
│   ├── bookings-service/       # Git submodule
│   ├── payments-service/       # Git submodule
│   ├── inventory-service/      # Git submodule
│   └── notifications-service/  # Git submodule
│
├── gateway/
│   └── nginx.conf              # Nginx reverse-proxy (API Gateway)
│
├── docker-compose.yml          # Local development orchestration - not yet implemented
├── stack.yml                   # Docker Swarm deployment - not yet implemented
│
└── README.md              

# How to Clone the Entire Project (Including Submodules)

Because this repository uses Git submodules, you must clone it with the --recurse-submodules flag:

Recommended
git clone --recurse-submodules <orchestrator-repository-url>
cd orchestrator

If you already cloned it normally:
git submodule init
git submodule update

Updating submodules to the latest commit from each service
git submodule update --remote --merge

# How to Run the Full System - not yet implemented
Using Docker Compose (local development)
docker compose up --build

Using Docker Swarm (production-like)
docker swarm init  # only once
docker stack deploy -c stack.yml retail-tractors

# API Gateway (Nginx)

This repository includes an Nginx configuration that acts as a lightweight API Gateway.

It handles:

Path-based routing

Forwarding to the correct microservice

Acting as the single public entry point

Security, authentication, and business logic remain inside the microservices.