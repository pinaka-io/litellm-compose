# LiteLLM Docker Compose

A Docker Compose setup for running [LiteLLM](https://github.com/BerriAI/litellm) proxy server with PostgreSQL and Prometheus monitoring.

## Services

- **LiteLLM Proxy**: AI gateway/proxy server running on port 4000
- **PostgreSQL**: Database for storing models and configurations on port 5432
- **Prometheus**: Metrics collection and monitoring on port 9090

## Prerequisites

- Docker and Docker Compose installed
- [Task](https://taskfile.dev/) (optional, for using Taskfile commands)
- `.env` file with your configuration (see `.env.example`)

## Quick Start

### Using Task (recommended)

```bash
# Copy the example env file and configure it
cp .env.example .env

# Edit .env with your API keys and settings
nano .env

# Start services
task up

# Stop services
task down

# Stop services and remove volumes
task down-volumes
```

### Using Docker Compose directly

```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# Stop services and remove volumes
docker-compose down -v
```

## Configuration

### Environment Variables

Copy `.env.example` to `.env` and configure your settings:

```bash
cp .env.example .env
```

Required variables are documented in `.env.example`.

### LiteLLM Config (Optional)

To use a custom LiteLLM configuration file:

1. Create a `config.yaml` file (see `config.yaml` example)
2. Uncomment the volumes and command sections in `docker-compose.yml`
3. Restart the services

## Accessing Services

- **LiteLLM API**: http://localhost:4000
- **LiteLLM UI**: http://localhost:4000/ui
- **Prometheus**: http://localhost:9090
- **PostgreSQL**: localhost:5432

## Health Checks

The services include health checks to ensure they're running properly:

- LiteLLM: checks `/health/liveliness` endpoint
- PostgreSQL: checks database connectivity

## Data Persistence

- PostgreSQL data is persisted in the `litellm_postgres_data` volume
- Prometheus data is persisted in the `prometheus_data` volume

## Task Commands

- `task up` - Start all services in detached mode
- `task down` - Stop all services
- `task down-volumes` - Stop services and remove all volumes (clean slate)

## Documentation

- [LiteLLM Documentation](https://docs.litellm.ai/)
- [LiteLLM GitHub](https://github.com/BerriAI/litellm)

## License

This configuration is provided as-is for use with LiteLLM.
