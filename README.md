\# Dockerfile Deep Dive — DevOps Winter Arc



\## Project Overview

A Node.js HTTP API packaged using Docker to demonstrate Dockerfile instructions, runtime configuration, layer caching, and container security.



\## Technologies

\- Node.js

\- Docker Desktop

\- Alpine Linux

\- Git and GitHub



\## Build and Run

```bash

docker build --progress=plain -t demo-api:v1 .

docker run -d --name api -p 3000:3000 demo-api:v1

```



\## API Endpoints

\- `GET /` — Returns a greeting and the application environment.

\- `GET /health` — Returns `ok`.



\## Runtime Configuration

Environment variables `GREETING` and `APP\_ENV` can change the application's response without rebuilding the image.



\## Docker Layer Caching

Dependency manifests are copied before application source code. When only `server.js` changes, Docker can reuse the dependency installation layer if its inputs remain unchanged.



\## CMD vs ENTRYPOINT

The `Dockerfile.greeter` experiment uses `ENTRYPOINT \["echo", "Hello"]` and `CMD \["World"]`. The default output is `Hello World`; passing `DevOps` produces `Hello DevOps`.



\## Security and Optimization

The `.dockerignore` file excludes unnecessary files and `.env`. The container runs as the non-root `node` user. Secrets should not be stored in Docker build arguments or image environment variables.



\## Conclusion

This project demonstrates Docker image building, runtime configuration, caching, image inspection, and basic container security practices.

